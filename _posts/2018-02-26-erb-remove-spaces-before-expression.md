---
layout: post
title: ERB remove spaces before expression
date: 2018-02-26 20:54 +0300
tags: [til, ruby]
---

Usually, this ERB template 

```
<% [1,2,3].each do |f| %>
  <%= f %>
<% end %>
```

will produce the following output

```
irb(main):019:0> ERB.new(File.read('f.txt')).result
=> "\n    1\n\n    2\n\n    3\n\n"
```

Sometimes you want to keep your ERB code idented properly, but to skip thise spaces before the actual output.

You can use [ERB trim_mode](http://ruby-doc.org/stdlib-2.5.0/libdoc/erb/rdoc/ERB.html#method-c-new) for that.

According to the [https://www.systutorials.com/docs/linux/man/1-erb/](https://www.systutorials.com/docs/linux/man/1-erb/)
trim mode value `-` will remove all spaces before `<%-`.

**Attention** only before `<%-`! So it will not work for `<%=`.

That's why the only way to achieve this behaviour, is to add some useless `<%- 1 %>` expression before output, that you want to trim.

```
<% [1,2,3].each do |f| %>
    <%- 1 %><%= f %>
<% end %>
```

and try

```
irb(main):018:0> ERB.new(File.read('f.txt'), nil, '-').result
=> "\n1\n\n2\n\n3\n\n"
```

BTW, in rails the default value for ERB `trim_mode` is `-`.



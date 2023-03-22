---
layout: post
title: SMB security program checklist
date: 2023-03-15 00:00 +0300
---

For most of my career, I've been working on public web applications. Even when I switched to the security domain the type of the companies remained the same.
Imagine a SaaS company that develops its custom software, runs it in the cloud, and operates fully remotely. That's where most of my experience is.

Usually, such startups don't care much about security, at least in the early and mid stages. They have little or no dedicated security staff and just rely on developers' experience and common sense. Such an approach can work fine for a while, but eventually, the technical debt has to be paid.
When the company grows, new people join and new teams emerge it becomes hard to rely on common sense. The more codebase and infrastructure changes happen, the harder it is to be aware of the potential risks that they bring.

But security scope is not limited just by application and infrastructure code. A lot of issues reside in the way how companies perform their day-to-day operations. This area of security may sound like a bureaucracy, but it is inevitable evil if you want to protect the business.

So instead of patching random findings here and there, it is much better to have a structured plan. This plan is called a Security Program.

## When security program is important?

- To work with enterprise customers. Such clients usually take security seriously and tend to assess and request certifications from their service providers.
- If the company processes some sensitive medical or financial data.
- In case of any confirmed data breach or other security incidents. The importance of security becomes clear when it is too late.

## Cybersecurity frameworks

To define the structure of the security program there are multiple different cybersecurity frameworks: e.g. NIST, CIS, ISO 27001/27002, SOC2, HIPAA, and others.
They are usually complex, broad in scope, and can take a lot of resources for full adaption. Though they all share the same goal - provide standards, guidelines, and best practices to manage risks in a digital world.

If you plan to pass some security audits and get certification then it is worth getting familiar with the framework of your choice. But if your intention is just to make the first steps in the implementation of a security program, then probably the better idea is to stick to some generic security checklist and avoid spending your limited resources on an overwhelming framework implementation.

## SMB security checklist

For those who are looking for a SaaS company security checklist, here is my choice of action items that you should focus on before diving into any cybersecurity framework. It is not an exhaustive list, some items can be missing, so the post will be continuously updated.

Each of these items deserves a separate blog post, so subscribe to my [LinkedIn](https://www.linkedin.com/in/stanislav-mekhonoshin-b3088953/) or [Twitter](https://twitter.com/stasik_mexx) to get updates ;)

- Services inventory
- Secrets inventory
- Access Matrix
- Offboarding checklist
- WAF for public endpoints
- Network segregation
- VPN solution
- Centralized logging
- SIEM
- SAST toolkit
- Supply chain management
- Vulnerabilities scanning
- Password manager/Disks encryption/Screen locks/AV on workstations
- Security awareness training
- Annual pentest
- Risk assessment
- Quarterly security audit
- Bug bounty program
- Security Champions program

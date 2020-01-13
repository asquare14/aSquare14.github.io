---

title: "CNCF/Fluentd Internship: Week 2/12"
layout: post
date: 2020-01-19 13:30
tag:
- fluentd
- cncf
category: blog
author: atibhi
description: Description of week-2 of fluent-d internship

---

#### Week 2 of the internship

I registered config maps for 3 output plugins and made changes to the 2 PRs opened last week(the [Pull Requests](https://github.com/fluent/fluent-bit/pulls/aSquare14) are under review.) 

The plugins are : 

1) [out_azure](https://docs.fluentbit.io/manual/output/azure) 

2) [out_datadog](https://docs.fluentbit.io/manual/output/datadog)

3) [td](https://docs.fluentbit.io/manual/output/td)

4) [out_tcp](https://docs.fluentbit.io/manual/output/tcp)

5) [nats](https://docs.fluentbit.io/manual/output/nats)

I devised a rough workflow for migrating the plugins :

**Test Plugin&#8594;
Add config map &#8594;Remove/Simplify code in Config File of plugin &#8594;Test Plugin&#8594; Send PR &#8594; Make changes to PR**


I also got my hands dirty with Microsoft Azure and Datadog to test if the plugins are working properly. This was particularly exciting for me because I am getting to learn about DevOps along with Software Engineering.

Moreover, I learnt a lot from my mentors Eduardo and Masoud. They explained in detail what the function of a `config_map` is and why `offsetof` is used in config maps. Writing down the explanation below for future reference.

**Config Map**

The config map has two main jobs:

1) Specify "which" parameters are allowed in any plugin.

2) Optional support to write the recieved parameter to the plugin context 

3) When a config map is specified, if a parameter was not registered it will fail and exit.

**offsetof()**
    
The macro offsetof() returns the offset of the field member from the    start of the structure type. `offsetof()` returns the offset of the given member within the given type, in units of bytes.

#### Plan for the next week

- Add config maps for the rest of the output plugins.
- Make changes requested for the Pull Requests which are under review.

---
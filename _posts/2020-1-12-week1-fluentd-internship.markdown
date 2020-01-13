---

title: "CNCF/Fluentd Internship: Week 1/12"
layout: post
date: 2020-01-12 13:30
tag:
- fluentd
- week1
- cncf
category: blog
author: atibhi
description: Description of week-1 of fluent-d internship

---

#### Introduction

Hi everyone ! I am [Atibhi Agrawal](https://twitter.com/atibhi_a), a pre-final year student of Integrated Masters (Bachelors+Masters) in Electronics and Communication engineering course at International Institute of Information Technology, Bangalore. I will be contributing to fluent-d as a part of the CommunityBridge and Cloud Native Computing Foundation's internship program. I will also be gettings 4 credits for the same as I have taken it as a project elective under [Professor B.Thangaraju](https://www.iiitb.ac.in/faculty/thangaraju-b) who takes the Operating Systems, Software Engineering courses etc. in our college.

#### How I heard of fluent-d 

I was an intern at Hackerrank last summer where one of the tasks involved sending logs to stackdriver using fluent-d. That was the first time I heard of fluent-d. Fluentd is an open source data collector for unified logging layer. In November of 2020 I got the opportunity to go to KubeCon and Cloud Native Con North America as a diversity scholar and I met Eduardo over there at the maintainers meetup. He told me about the internship and I applied. The application process consisted of tasks as well as a video interview with Eduardo and Masoud. I was so happy and grateful when I heard back from them that I was selected.

#### Week 1 of the internship

Last week was my first week of the internship. I had a video call meeting with [Eduardo](https://twitter.com/edsiper) and [Masoud](https://twitter.com/_koleini) at the beginning of the week where we talked about the work that was expected of me as well as explained the general guidelines and code of conduct to be followed for the internship. 

Currently, [Fluent-bit](https://fluentbit.io) exposes an API which is used by the plugins to read configuration values. This works as expected but problems arise when the plugin receives an unknown configuration key. There is also a need to reduce risk in case of bad configuration keys or depreciated property names. My task is to add config maps to plugin so that in the future dynamic reload support can be implemented. Dynamic reload is important so that the core is aware of the expected configuration properties of each plugin and it can perform validations before taking any reload action. You can refer to [this](https://github.com/fluent/fluent-bit/issues/1672) issue for more details.

During the past week, I worked on adding config maps to [nats](https://fluentbit.io/documentation/0.12/output/nats.html) and [out_tcp](https://github.com/fluent/fluent-bit/tree/master/plugins/out_tcp) plugin. My Pull Requests are under review. I also revised up on C basics and went through the codebase to get familiar with the code.

#### Plans for next week

I plan to add config maps for the remaining plugins in the next week. 

I am really excited for my internship and look forward to contributing, learning and growing ! :smile:

---
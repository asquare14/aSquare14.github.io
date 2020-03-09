---

title: "CNCF/Fluentd Internship: Week 8/12"
layout: post
date: 2020-03-9 10:02
tag:
- fluentd
- cncf
category: blog
author: atibhi
description: Description of week-8 of fluent-d internship

---

#### Week 8 of the internship

**Work done**

- This week my first PR got **merged**. The out-forward PR. I had some doubts regarding this plugin which I also got clarified.
- Started working on in_mqtt plugin. Also read up about [MQTT](https://www.youtube.com/watch?v=EIxdz-2rhLs). MQTT stands for **Message Queuing Telemetry Transport**. MQTT is a simple messaging protocol, designed for constrained devices with low-bandwidth. MQTT allows to send commands to control outputs, read and publish data from sensor nodes and much more. Therefore, it makes it really easy to establish a communication between multiple devices.
- I also found a bug in the in_mqtt plugin. It was regarding [munmap_chunk](https://stackoverflow.com/questions/32118545/munmap-chunk-invalid-pointer/32118638). There was an issue on exit.

- Started working on in_syslog plugin. Read up about [syslog](https://en.wikipedia.org/wiki/Syslog). In computing, **syslog is a standard for message logging**. It allows separation of the software that generates messages, the system that stores them, and the software that reports and analyzes them. 


#### Pull Requests Waiting for Review

- out-forward - https://github.com/fluent/fluent-bit/pull/1904 
- out-tcp - https://github.com/fluent/fluent-bit/pull/1971 

- out-retry -https://github.com/fluent/fluent-bit/pull/1911 

- out-td - https://github.com/fluent/fluent-bit/pull/1892  

- out-azure - https://github.com/fluent/fluent-bit/pull/1878/files

- in_mqtt - https://github.com/fluent/fluent-bit/pull/1985


#### Plans for next week

- Migrate in_syslog and finish reviews.

---

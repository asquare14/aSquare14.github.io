---

title: "CNCF/Fluentd Internship: Week 3/12"
layout: post
date: 2020-01-26 12:30
tag:
- fluentd
- cncf
category: blog
author: atibhi
description: Description of week-3 of fluent-d internship

---

#### Week 3 of the internship

This week I worked on the [forward](https://docs.fluentbit.io/manual/output/forward) output plugin. It is the protocol used by fluentd to route messages between peers. It also provides interoperability between
Fluentd and Fluentbit. I faced some issues while setting up Fluentd because the port that was used by Fluentd was also being used by ruby. After, I got the setup, I registered a config map for the forward plugin. However,forward output supports upstream servers and hence I had to read about [Upstream Servers](https://docs.fluentbit.io/manual/configuration/upstream_servers) to test the plugin. While reading about upstream server I also read about [TLS]( https://www.cloudflare.com/learning/ssl/transport-layer-security-tls/) which is a widely adopted security protocol designed to facilitate privacy and data security for communications over the Internet. In fact, HTTPS is an implementation of TLS encryption on top of the HTTP protocol. 

I also worked on the [gelf](https://docs.fluentbit.io/manual/output/gelf) and **retry** output plugins and registered config maps for them. 

I also started working on **splunk** plugin but faced issues while setting up splunk in the cloud and sending logs to it. I shall complete this in the next few days after taking help from my mentors and also work on other output plugins.


#### Plan for the next week

- Add config maps for the rest of the output plugins.
- Make changes requested for the Pull Requests which are under review.

---

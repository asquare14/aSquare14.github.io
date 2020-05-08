---

title: "[Jan 2020 - April 2020]CNCF/Fluentd Internship: Weekly Blogs"
layout: post
date: 2020-01-12 13:30
tag:
- fluentd
- cncf
- internship
category: blog
author: atibhi
description: Weekly Blogs

---



#### Introduction

Hey everyone ! I am [Atibhi Agrawal](https://twitter.com/atibhi_a), a pre-final year student of Integrated Masters (Bachelors+Masters) in Electronics and Communication engineering course at International Institute of Information Technology, Bangalore. I will be contributing to fluent-d as a part of the CommunityBridge and Cloud Native Computing Foundation's internship program. I will also be gettings 4 credits for the same as I have taken it as a project elective under [Professor B.Thangaraju](https://www.iiitb.ac.in/faculty/thangaraju-b) who takes the Operating Systems, Software Engineering courses etc. in our college.

#### How I heard of fluent-d 

I was an intern at Hackerrank last summer where one of the tasks involved sending logs to stackdriver using fluent-d. That was the first time I heard of fluent-d. Fluentd is an open source data collector for unified logging layer. In November of 2020 I got the opportunity to go to KubeCon and Cloud Native Con North America as a diversity scholar. At the conference, I met Eduardo at the maintainers meetup. He told me about the internship and I applied for it. The application process consisted of tasks as well as a video interview with Eduardo and Masoud. I was so happy and grateful when I heard back from them that I was selected.

## Week 1

January 6 to January 12 was the first week of the internship. I had a video call meeting with [Eduardo](https://twitter.com/edsiper) and [Masoud](https://twitter.com/_koleini) at the beginning of the week where we talked about the work that was expected of me. They also explained the general guidelines and code of conduct to be followed for the internship. 

Currently, [Fluent-bit](https://fluentbit.io) exposes an API which is used by the plugins to read configuration values. This works as expected but problems arise when the plugin receives an unknown configuration key. There is also a need to reduce risk in case of bad configuration keys or depreciated property names. My task is to add config maps to plugin so that in the future dynamic reload support can be implemented. Dynamic reload is important so that the core is aware of the expected configuration properties of each plugin and it can perform validations before taking any reload action. You can refer to [this](https://github.com/fluent/fluent-bit/issues/1672) issue for more details.

During the past week, I worked on adding config maps to [nats](https://fluentbit.io/documentation/0.12/output/nats.html) and [out_tcp](https://github.com/fluent/fluent-bit/tree/master/plugins/out_tcp) plugin. My Pull Requests are under review. I also revised up on C basics and went through the codebase to get familiar with the code.

#### Plans for next week

I plan to add config maps for the remaining plugins in the next week. 

I am really excited for my internship and look forward to contributing, learning and growing ! :smile:

---

## Week 2

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

## Week 3

This week I worked on the [forward](https://docs.fluentbit.io/manual/output/forward) output plugin. It is the protocol used by fluentd to route messages between peers. It also provides interoperability between
Fluentd and Fluentbit. I faced some issues while setting up Fluentd because the port that was used by Fluentd was also being used by ruby. After, I got the setup, I registered a config map for the forward plugin. However,forward output supports upstream servers and hence I had to read about [Upstream Servers](https://docs.fluentbit.io/manual/configuration/upstream_servers) to test the plugin. While reading about upstream server I also read about [TLS]( https://www.cloudflare.com/learning/ssl/transport-layer-security-tls/) which is a widely adopted security protocol designed to facilitate privacy and data security for communications over the Internet. In fact, HTTPS is an implementation of TLS encryption on top of the HTTP protocol. 

I also worked on the [gelf](https://docs.fluentbit.io/manual/output/gelf) and **retry** output plugins and registered config maps for them. 

I also started working on **splunk** plugin but faced issues while setting up splunk in the cloud and sending logs to it. I shall complete this in the next few days after taking help from my mentors and also work on other output plugins.


#### Plan for the next week

- Add config maps for the rest of the output plugins.
- Make changes requested for the Pull Requests which are under review.

---

## Week 4

**Work done** - 
- Worked on **forward** plugin and made changes in the PR. Thank you Fujimoto Seiji for reviewing this PR.
- Also explored influxDB and stackdriver services.

**Things learnt** :) -

- Eduardo told me that we should test every single property of the configuration that I am porting to a config map and the test should involve a real data flow test. I was actually testing the plugins but not using every parameter, just using the basic parameters so this advice was very useful. I shall keep this in mind for future !


#### Plans for next week

- Test every plugin for which I have regsitered config maps till now.
- I don't want to work on newer plugins till the old ones are merged, so this week I plan to work on my old PRs and try to get them merged . :)

---

## Week 5

**Work done** - 

This week I worked on the output plugins retry, forward and tcp. I made changes in the PR for these plugins as suggested by Eduardo. 
I learnt a lot about config_maps in general this week. I am going to summarize whatever I learnt :
- A Configmap aims to auto-set the values into the proper plugin context.
- It has the following fields, type, property name, default value, option flags, set context property using offset, member offset and description.
- The set context property is related to member offset. If the set context property is true only then will the plugin property be written to context else it will not.
- Registering config maps can reduce complexity of the code.
- There are two types of configuration keys, public and private. We must not expose the private configuration keys.
- Config maps support different data types.

#### Plans for next week

- Test every plugin for which I have regsitered config maps till now.
- Migrate more plugins.

---

## Week 6

**Work done** - 

- Continued working on out-tcp,gelf, forward and retry plugins. 
- Made changes in Pull Request as requested.
- Went through the flb_config_map.c file to understand the whole flow of config maps.


#### Plans for next week

- Test every plugin for which I have regsitered config maps till now.

---

## Week 7

**Work done**

- Made changes on treasure_data, forward, retry and tcp plugins.

- [out-azure](https://github.com/fluent/fluent-bit/pull/1878/files) Sent Pull Request for this, setup Azure Log Analytics Engine as well.(Waiting for review)

- Made changes in out_forward, out_retry, out_treasure_data and out_tcp. (Waiting for review.)

- out_forward got [merged](https://github.com/fluent/fluent-bit/commit/d6c5dc5086a13b4e49a8a98a74ff255bc9282e77).

- Have started writing [daily blogs](https://docs.google.com/document/d/1xCTCMhxXSfzQaaUMGIlahoGK-jixN51OqBK74FhXDi4/edit).



#### Plans for next week

- Test every plugin for which I have regsitered config maps till now.
- Migrate in_syslog and in_mqtt.

---

## Week 8
**Work done**

- This week my first PR got **merged**. The out-forward PR. I had some doubts regarding this plugin which I also got clarified.
- Started working on in_mqtt plugin. Also read up about [MQTT](https://www.youtube.com/watch?v=EIxdz-2rhLs). MQTT stands for **Message Queuing Telemetry Transport**. MQTT is a simple messaging protocol, designed for constrained devices with low-bandwidth. MQTT allows to send commands to control outputs, read and publish data from sensor nodes and much more. Therefore, it makes it really easy to establish a communication between multiple devices.
- I also found a bug in the in_mqtt plugin. It was regarding [munmap_chunk](https://stackoverflow.com/questions/32118545/munmap-chunk-invalid-pointer/32118638). There was an issue on exit.

- Started working on in_syslog plugin. Read up about [syslog](https://en.wikipedia.org/wiki/Syslog). In computing, **syslog is a standard for message logging**. It allows separation of the software that generates messages, the system that stores them, and the software that reports and analyzes them. 


#### Pull Requests Waiting for Review

- out-tcp - https://github.com/fluent/fluent-bit/pull/1971 

- out-retry -https://github.com/fluent/fluent-bit/pull/1911 

- out-td - https://github.com/fluent/fluent-bit/pull/1892  

- out-azure - https://github.com/fluent/fluent-bit/pull/1878/files

- in_mqtt - https://github.com/fluent/fluent-bit/pull/1985


#### Plans for next week

- Migrate in_syslog. 
- finish reviews.
- finish out_tcp2

---

## Week 9

**Work done**

- This week I had issues with my laptop and I spent 1.5 days to fix it and setup fluent-bit again.
- I worked on out-azure plugin that was reviewed and examined the existing parameter handlings one
by one and tested out each and every line of them.
- Apart from this, I studied the codebase and made a list of my doubts.I also tried resolving them but I hit a roadblock at some point.
I am trying to co-ordinate with my mentors so that we can clear it at the earliest.

#### Plans for next week

- Migrate in_syslog 
- finish out_tcp2

---

## Week 10

**Work done**

- External TCP plugin
    - I was stuck on the external tcp plugin for almost a week because of a roadblock. The problem was that even after
    I loaded the `.so` file I was unable to use the external plugin. After discussion with Masoud, over a meeting, I understood
    that the problem was I had not mentions `Plugins_File plugins.conf` in my configuration file. However, this information was not there in the documentation and I submitted a [PR](https://github.com/fluent/fluent-bit-plugin/pull/4) to take this detail into account.

    - After, I could test the plugin, I worked on out_tcp2 external plugin and wrote code to integrate it with fluent-bit. I managed to successfully send the logs to a TCP port but valgrind is still showing some errors which I need to fix. I also need to handle edge cases and failures. Hope to get thie done by the mid of the week.[Link](https://github.com/fluent/fluent-bit-plugin/pull/5)
    
- out-azure plugin
    - Worked on out-azure plugin. Review is still in progress. I am making changes according to review on a rolling basis.

- out-azure Plugin
  - Made changes as requested by fujimotos. Checked existing parameter handlings one by one and removed assignments of some parameters
  to leverage the config map. 
  - Updated the documentation for out-azure. Added missing parameter time_key. [Link](https://github.com/fluent/fluent-bit-docs/pull/283). 
  - Removed trailing whitespaces. Found this cool [article](https://stackoverflow.com/questions/3372822/git-trim-whitespace) on the same. 
  
- External out-tcp plugin in [fluent-bit/plugins](https://github.com/fluent/fluent-bit-plugin/pulls)
  - Added gitignore file in the repository. [Link](https://github.com/fluent/fluent-bit-plugin/pull/6)
  - Updated my [PR](https://github.com/fluent/fluent-bit-plugin/pull/5) for the external plugin. Took care of memory leaks, assignments,
  case when tcp server is not found as well as added comments to make the code more readable. Waiting for review on this PR.

#### Plans for next half week

- finish out-azure reviews.
- finish out_tcp2

---

## Week 11

**Work done**

- [Developer Guide](https://github.com/fluent/fluent-bit/blob/master/DEVELOPER_GUIDE.md)
  - While writing [documentation for the out_tcp2 plugin](https://github.com/fluent/fluent-bit-plugin/blob/c83d745ac5f47718c78319006765285e93e8f884/README.md
  ) I came across the developer guide in fluent-bit repository. I was so surprised that I missed it earlier.
  - I proceeded to add a link to the README which sends a beginner to the guide. I also corrected a typo in the guide.(Merged)
  - I went through the guide in detail as well as the external links and libraries mentioned. This took me almost 1.5-2 days but it
  was worth it because I gained a lot of knowledge as well as consolidated my existing knowledge.
  - I then proceeded to add documentation about config maps in the developer guide. [PR Link](https://github.com/fluent/fluent-bit/pull/2060/files
)


---

## Week 12

**Work done**

- [Developer Guide](https://github.com/fluent/fluent-bit/blob/master/DEVELOPER_GUIDE.md)
  - Worked on reviews for adding documentation of config maps to developer guide.
  - In reference to this PR, I added documentation for the properties used in config map in stdout plugin. [Link](https://github.com/fluent/fluent-bit/pull/2075/files)

- Finished up existing PRs and work. 

---
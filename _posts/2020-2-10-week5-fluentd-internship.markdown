---

title: "CNCF/Fluentd Internship: Week 5/12"
layout: post
date: 2020-02-10 12:07
tag:
- fluentd
- cncf
category: blog
author: atibhi
description: Description of week-5 of fluent-d internship

---

#### Week 5 of the internship

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
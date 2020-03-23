---

title: "CNCF/Fluentd Internship: Week 10/12"
layout: post
date: 2020-03-24 12:00
tag:
- fluentd
- cncf
category: blog
author: atibhi
description: Description of week-10 of fluent-d internship

---

#### Week 10 of the internship

**Work done**

- I was stuck on the external tcp plugin for almost a week because of a roadblock. The problem was that even after
I loaded the `.so` file I was unable to use the external plugin. After discussion with Masoud, over a meeting, I understood
that the problem was I had not mentions `Plugins_File plugins.conf` in my configuration file. However, this information was not
there in the documentation and I submitted a PR(https://github.com/fluent/fluent-bit-plugin/pull/4) to take this detail into account.

- After, I could test the plugin, I worked on out_tcp2 external plugin and wrote code to integrate it with fluent-bit. I managed 
to successfully send the logs to a TCP port but valgrind is still showing some errors which I need to fix. I also need to handle
edge cases and failures. Hope to get thie done by the mid of the week.(https://github.com/fluent/fluent-bit-plugin/pull/5)
    
- Worked on out-azure plugin. Review is still in progress. I am making changes according to review on a rolling basis.

#### Plans for next week

- finish reviews.
- finish out_tcp2

---

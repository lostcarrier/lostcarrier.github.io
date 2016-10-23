---
layout: post
title:  "OSX + Tor + Privoxy (with random user-agent)"
date:   2016-10-15 10:14:34 -0400
author: "lostcarrier"
categories: posts
---
{% highlight python %}
#!/usr/local/bin/python

from user_agent import (generate_user_agent, generate_navigator,
                        generate_navigator_js,
                        UserAgentRuntimeError, UserAgentInvalidRequirements)

ua = generate_user_agent()

ua_1 = "{+hide-accept-language{en-en} \\"
ua_2 = " +hide-user-agent{%s} \\" %(ua)
ua_3 = "}"
ua_4 = "/"

f1=open('/usr/local/etc/privoxy/user-agent.action', 'w+')
f1.write("%s\n%s\n%s\n%s" %(ua_1, ua_2, ua_3, ua_4))

{% endhighlight %}

---
layout: post
title:  "OSX + Tor + Privoxy (with random user-agent)"
date:   2016-10-23 13:31:34 -0400
author: "lostcarrier"
categories: posts
---

```
brew install tor
brew install privoxy
```
in /usr/local/etc/privoxy/config, place the line `actionsfile user-agent.action` 
in between the actionsfile default.action and actionsfile user.action lines.

search /usr/local/etc/privoxy/config for the following lines, and uncomment them all:

```
...
forward-socks5t   /               127.0.0.1:9050 .
...
forward         192.168.*.*/     .
forward            10.*.*.*/     .
forward           127.*.*.*/     .
...
forward           localhost/     .
...
```

i have the following python script in ~/bin:
ranua.py

```python
#!/usr/local/bin/python

from user_agent import (generate_user_agent, generate_navigator,
                        generate_navigator_js,
                        UserAgentRuntimeError, UserAgentInvalidRequirements)

ua = generate_user_agent()

ua_1 = "{+hide-accept-language{en-en} \\"
ua_2 = " +hide-user-agent{"
ua_3 = "} \\"
ua_4 = "}"
ua_5 = "/"

f1=open('/usr/local/etc/privoxy/user-agent.action', 'w+')
f1.write("%s\n%s%s%s\n%s\n%s" %(ua_1, ua_2, ua, ua_3, ua_4, ua_5))
```

now edit your cron file (crontab -e) to include the line: `*/15 * * * * /Users/your_user_name/bin/ranua.py` 
change the your_user_name to whatever your user name is.

(this will run the ranua.py every 15 minutes, and change the user agent that privoxy sends with each http request.)

now in the terminal:

```
brew services start tor
brew services start privoxy
```

in your browser, find your proxy settings, and set your proxy server to 127.0.0.1 port 8118


if, for some reason, this doesnt work for you, and completely fucks your connection, just remove the proxy settings in your browser. you'll be fine.

if you're pissed that it screwed something up and you want to remove proxify/tor, open your teminal and:

```
brew services stop proxify
brew services stop tor
brew remove proxify
brew remove tor
```



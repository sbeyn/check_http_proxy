# Nagios HTTP Proxy Plugin

I've written in python of a nagios plugin to check HTTP Proxies. The plugin includes testing:

- time of response (timeout and warning in the more recent python version, just warning in the older)
- http proxy and port with or without authentication
- expected content for a given URL

In all places I've endeavoured to capture the errors that might occur and return them in a way that will produce useful information within Nagios.

Usage looks like this:
```
$ check_http_proxy --proxy=proxy:port --auth=user:pass --url=url --timeout=5 --warntime=3 --expect=content
```

While the Nagios configuration I'm using looks like:
```
define command{
        command_name    check_http_proxy
        command_line    /usr/lib/nagios/lib_custom/check_http_proxy "--proxy=$ARG1$" "--auth=$ARG2$" "--warntime=$ARG3$" "--expect=$ARG4$" "--url=$ARG5$"
}
```

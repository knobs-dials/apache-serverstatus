# apache-serverstatus
A live CLI view on apache's mod_status.

Proof of concept version, and currently mainly parses status output for prefork.

# screenshot
![screenshot](https://raw.githubusercontent.com/scarfboy/apache-serverstatus/main/screenshot.png)

# arguments


```
Usage: apache-serverstatus [options]

Options:
  -h, --help            show this help message and exit
  -i INTERVAL, --interval-sec=INTERVAL
                        Poll interval, in seconds. Defaults to 0.25
  -p, --no-chop-port    By default we chop post off vhost for readability. Use
                        this if you want to see those.
  -v VCHOP, --chop-vhost=VCHOP
                        Chop off parts from the end of vhost. Defaults to 1,
                        aiming to remove .com or such. Will refuse to remove
                        everything, so a high value shows the first part of
                        every name.
  -u HOST, --host=HOST  We basically fetch http://THIS/server-status  so this
                        defaults to 127.0.0.1
```

# TODO:
- deal with non-ExtendedStatus output too
- look at parsing outputs for other MPMs (it's currently aimed at prefork)
- summarize acc, conn, child, and slot (currently omitted because they're more about reuse than current requests)
- make columns configutable
- adapt vhost column size to maximum presented length

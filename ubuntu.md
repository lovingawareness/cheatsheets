# Ubuntu cheatsheet

* `sudo apt-get remove _packagename_` / `sudo apt-get purge _packagename_` - Removes a package named _packagename_. This supports wildcards. I accidentally installed postgresql when I didn't need it on the server, so I was able to remove it easily with `sudo apt-get purge postgresql*`.
* `lsof -i :80` - List the process listening on port 80.

## References:

1. [How can I uninstall software? on AskUbuntu](https://askubuntu.com/a/1144)
1. [3 Ways to Find Out Which Process Listening on a Particular Port](https://www.tecmint.com/find-out-which-process-listening-on-a-particular-port/)

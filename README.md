# Intro
Some day-to-day stuff and references...

* [Install sngrep on CentOS-7](#S-sngrep)
* [Simple File/Http Server on linux](#S-fileserver)
* [Yum IPv4 Setting](#S-yumipv4)
 
### <a name="S-sngrep"></a>Install sngrep on CentOS-7
create `/etc/yum.repos.d/irontec.repo` w/ following contents

```sh
[irontec]
name=Irontec RPMs repository
baseurl=http://packages.irontec.com/centos/$releasever/$basearch/
```

Then...

```sh
$ rpm --import http://packages.irontec.com/public.key
$ yum install sngrep
```

### <a name="S-fileserver"></a>Simple File/Http Server on linux
```sh
$ cd /tmp
$ python -m http.server 8000
```

Now files in `/tmp` folder can be viewed/downlaoded in browser using http://\<ip\>:8000

### <a name="S-yumipv4"></a>Yum IPv4 Setting

yum update/list does not work – throws errors like
```sh
Timeout on http://mirrorlist.centos.org/
http://mirror.centos.org/centos/5/os...ta/repomd.xml: [Errno 12] Timeout: <urlopen error timed out>
Trying other mirror.
```

This is because yum tries to connect to IPv6 addresses return by DNS and sometimes IPv6 are not configured on these mirror sites. 
Solution is to tell yum to resolve to only IPv4 addresses. 

Add following setting in `/etc/yum.conf`
```sh
ip_resolve=IPv4
```

Ref/Credits:

https://unix.stackexchange.com/questions/444746/yum-fails-because-http-mirrorlist-centos-org-release-7arch-x86-64repo-os-is

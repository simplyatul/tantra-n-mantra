# Intro
Some day-to-day stuff and references...

* [Install sngrep on CentOS-7](#S-sngrep)
* [Simple File/Http Server on linux](#S-fileserver)
 
### <a name="S-sngrep"></a>Install sngrep on CentOS-7
create /etc/yum.repos.d/irontec.repo w/ following contents

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

Now file in /tmp folder can be viewed in browser using http://<ip>:8000

# ANSIBLED


```
╭─ keelah     ~/Documents/Dev/S8-Devops/TP1    main !4 ?1 
╰─ ansible all -m ping         
alexis.lonchambon.takima.cloud | UNREACHABLE! => {
    "changed": false,
    "msg": "Failed to connect to the host via ssh: keelah@alexis.lonchambon.takima.cloud: Permission denied (publickey,gssapi-keyex,gssapi-with-mic).",
    "unreachable": true
}
```

```
╭─ keelah     ~/Documents/Dev/S8-Devops/TP1    main !4 ?1 
╰─ ansible all -m ping --private-key=../.ssh/id_rsa3 -u centos
alexis.lonchambon.takima.cloud | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/libexec/platform-python"
    },
    "changed": false,
    "ping": "pong"
}
```

```
╭─ keelah     ~/Documents/Dev/S8-Devops/TP1    main !4 ?1 
╰─ ansible all -m yum -a "name=httpd state=present" --private-key=../.ssh/id_rsa3 -u centos --become
alexis.lonchambon.takima.cloud | CHANGED => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/libexec/platform-python"
    },
    "changed": true,
    "msg": "",
    "rc": 0,
    "results": [
        "Installed: mod_http2-1.15.7-5.module_el8.6.0+1111+ce6f4ceb.x86_64",
        "Installed: centos-logos-httpd-85.8-2.el8.noarch",
        "Installed: httpd-filesystem-2.4.37-47.module_el8.6.0+1111+ce6f4ceb.1.noarch",
        "Installed: mailcap-2.1.48-3.el8.noarch",
        "Installed: apr-1.6.3-12.el8.x86_64",
        "Installed: apr-util-1.6.1-6.el8.x86_64",
        "Installed: httpd-tools-2.4.37-47.module_el8.6.0+1111+ce6f4ceb.1.x86_64",
        "Installed: apr-util-bdb-1.6.1-6.el8.x86_64",
        "Installed: apr-util-openssl-1.6.1-6.el8.x86_64",
        "Installed: httpd-2.4.37-47.module_el8.6.0+1111+ce6f4ceb.1.x86_64"
    ]
}
```


WE WERE 3RD !!!
```
╭─ keelah     ~/Documents/Dev/S8-Devops/TP1    main !4 ?1 
╰─ ansible all -m service -a "name=httpd state=started" --private-key=../.ssh/id_rsa3 -u centos --become
alexis.lonchambon.takima.cloud | CHANGED => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/libexec/platform-python"
    },
    "changed": true,
    "name": "httpd",
    "state": "started",
    "status": {
        [...]
    }
}
```



## __FONRT_

Belle reflexion


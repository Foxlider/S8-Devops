# ANSIBLED

```
╭─ keelah     ~/Documents/Dev/S8-Devops/TP1    main !5 ?1 
╰─ ansible all -i ansible/inventories/setup.yml -m ping                                                
alexis.lonchambon.takima.cloud | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/libexec/platform-python"
    },
    "changed": false,
    "ping": "pong"
}
```


╭─ keelah     ~/Documents/Dev/S8-Devops/TP1    main !5 ?3 ▓▒░                                                                                                              ░▒▓ ✔  13:57  
╰─ ansible all -i ansible/inventories/setup.yml -m setup -a "filter=ansible_distribution*"
alexis.lonchambon.takima.cloud | SUCCESS => {
    "ansible_facts": {
        "ansible_distribution": "CentOS",
        "ansible_distribution_file_parsed": true,
        "ansible_distribution_file_path": "/etc/centos-release",
        "ansible_distribution_file_variety": "CentOS",
        "ansible_distribution_major_version": "8",
        "ansible_distribution_release": "Stream",
        "ansible_distribution_version": "8",
        "discovered_interpreter_python": "/usr/libexec/platform-python"
    },
    "changed": false
}



╭─ keelah     ~/Documents/Dev/S8-Devops/TP1    main !5 ?3 ▓▒░                                                                                                              ░▒▓ ✔  13:58  
╰─ ansible all -i ansible/inventories/setup.yml -m yum -a "name=httpd state=absent" --become
alexis.lonchambon.takima.cloud | CHANGED => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/libexec/platform-python"
    },
    "changed": true,
    "msg": "",
    "rc": 0,
    "results": [
        "Removed: mod_http2-1.15.7-5.module_el8.6.0+1111+ce6f4ceb.x86_64",
        "Removed: httpd-2.4.37-47.module_el8.6.0+1111+ce6f4ceb.1.x86_64"
    ]
}



```
╭─ keelah     ~/Documents/Dev/S8-Devops/TP1    main !5 ?3 ▓▒░                                                                                                            ░▒▓ 1 ✘  14:01  
╰─ ansible-playbook -i ansible/inventories/setup.yml ansible/playbook.yml

PLAY [all] ******************************************************************************************************************************************************************************************

TASK [Test connection] ******************************************************************************************************************************************************************************
ok: [alexis.lonchambon.takima.cloud]

PLAY RECAP ******************************************************************************************************************************************************************************************
alexis.lonchambon.takima.cloud : ok=1    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
```

```
╭─ keelah     ~/Documents/Dev/S8-Devops/TP1    main !5 ?3
╰─ ansible-playbook -i ansible/inventories/setup.yml ansible/playbook.yml --syntax-check

playbook: ansible/playbook.yml
```




```

╭─ keelah     ~/Documents/Dev/S8-Devops/TP1    main !5 ?3 ▓▒░                                                                                                              ░▒▓ ✔  14:04  
╰─ ansible-playbook -i ansible/inventories/setup.yml ansible/playbook.yml               

PLAY [all] ******************************************************************************************************************************************************************************************

TASK [Clean packages] *******************************************************************************************************************************************************************************
changed: [alexis.lonchambon.takima.cloud]

TASK [Install device-mapper-persistent-data] ********************************************************************************************************************************************************
changed: [alexis.lonchambon.takima.cloud]

TASK [Install lvm2] *********************************************************************************************************************************************************************************
changed: [alexis.lonchambon.takima.cloud]

TASK [add repo docker] ******************************************************************************************************************************************************************************
changed: [alexis.lonchambon.takima.cloud]

TASK [Install Docker] *******************************************************************************************************************************************************************************
changed: [alexis.lonchambon.takima.cloud]

TASK [install python3] ******************************************************************************************************************************************************************************
changed: [alexis.lonchambon.takima.cloud]

TASK [Pip install] **********************************************************************************************************************************************************************************
changed: [alexis.lonchambon.takima.cloud]

TASK [Make sure Docker is running] ******************************************************************************************************************************************************************
changed: [alexis.lonchambon.takima.cloud]

PLAY RECAP ******************************************************************************************************************************************************************************************
alexis.lonchambon.takima.cloud : ok=8    changed=8    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   

```



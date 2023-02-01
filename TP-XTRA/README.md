# AWS is broken, let's do something else

## __Load Balancing__

For redundancy we simply need to duplicate the backend part of our docker-compose, rename it, change the port and voilà.

## __Actual Load Balancing__

Documentation says the following :
```conf
<Proxy "balancer://mycluster">
    BalancerMember "http://192.168.1.50:80"
    BalancerMember "http://192.168.1.51:80"
</Proxy>
ProxyPass        "/test" "balancer://mycluster"
ProxyPassReverse "/test" "balancer://mycluster"
```

It was really buggy. We had to clean the images, wipe the volumes and restart anew. Some weird cache stuff was preventing us to start it correctly.  
We added some modules too : `mod_proxy_connect`, `mod_proxy_balancer`, `mod_slotmem_shm`, `mod_slotmem_plain`, `mod_lbmethod_byrequests`, `mod_lbmethod_bytraffic`


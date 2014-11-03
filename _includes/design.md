- Out of the box performance enhancements made to Magento, Apache,
PHP, and Galera. This includes PHP object caching, Memcached integration,
Apache performance configuration settings, and more.

- Network isolation and security group isolation at various levels
within the stack provide enhanced Cloud security. The database servers are
isolated from the web tier DMZ, and only available through a bastion
gateway load balancer to further protect data.

- We have found that centralized network file servers have higher
failure rates in cloud environments, are more difficult to ensure data
integrity, and almost always suffer performance loss. Our architecture 
utilizes csync2 and lsyncd to push data to other servers on creation events.
This minimizes data traffic and allows for substantially more application
servers to participate in the cluster. We also utilize sticky
sessions on the front end load balancer to maintain user experience while the 
sync events are taking place.

- SSL termination at the load balancer allows for secure customer
transactions while not having the added CPU overhead of computing SSL
on application instances. Network isolation and firewalling keeps
non-ssl traffic isolated from outside networks.

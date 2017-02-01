# cluster.proxy.squid
Docker images to implement egress caching in Nemesis

Build thusly:```
cd egress-gateway
docker build -t registry.service.consul:5000/cluster-proxy-squid-egress-gateway . 
docker push registry.service.consul:5000/cluster-proxy-squid-egress-gateway
```

with names chosen to go with [the Puppet config](https://github.com/epfl-sti/cluster.coreos.puppet/blob/master/manifests/gateway.pp)

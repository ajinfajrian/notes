edit proxy on container layer,
`vi /etc/systemd/system/docker.service.d/override.conf`
```bash
Environment="HTTP_PROXY=http://<floating_ip>:80"
Environment="HTTPS_PROXY=http://<floating_ip>:80"
Environment="NO_PROXY=172.18.217.17,clusterip/16,.local,.svc,localhost,.domain.co.id,.io,k8s-haproxy,k8s-registry,k8s-master-01,k8s-master-02,k8s-master-03,k8s-worker-01,k8s-worker-02,k8s-worker-03"
```

edit os environment, 
`vi /etc/environment`
```
http_proxy=http://172.18.216.71:80
https_proxy=http://172.18.216.71:80
no_proxy="172.18.217.17,10.96.0.0/12,10.244.0.0/16,10.40.41.26,10.40.41.16,10.40.41.159,10.40.41.214,10.40.41.53,10.40.41.87,10.40.41.201,10.40.41.132,.local,.svc,localhost,.bri.co.id"
```

- systemctl daemon-reload
- systemctl restart docker

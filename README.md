# k3s HA Cheat Sheet (wop)

Random notes how to copy'n'paste together a k3s HA cluster.

Deploy 3 vps' within a private network with following init scripts:

The first server's (aks master or control-plane) init:

```
curl -sfL https://get.k3s.io | \
  INSTALL_K3S_CHANNEL=latest \
  INSTALL_K3S_VERSION=v1.21.0+k3s1 \
  sh -s - \
  --cluster-init \
  --token superlametoken
```

The following servers' (aka master or control-plane) init:

```
curl -sfL https://get.k3s.io | \
  INSTALL_K3S_CHANNEL=latest \
  INSTALL_K3S_VERSION=v1.21.0+k3s1 \
  sh -s - \
  --server http://<private IP of the first server>:6443 \
  --token superlametoken
```

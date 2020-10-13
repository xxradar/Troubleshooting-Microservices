# Troubleshooting Microservices on K8S and Calico

## Get to know your cluster
### Internode connectivity
```
sudo calicoctl node status
```
### IPPools settings (NatOutgoing, Encapsulation, pool cidr and block 
```
calicoctl get ippools

ex. calicoctl get ippools default-ipv4-ippool -o yaml
```
### Verify the IP address assignemt
```
calicoctl ipam show --show-blocks
```
### Verify pool annotations
Annotate a namesmace to use an specific ippool (should be already done)
```
kubectl annotate namespace wwwdemo "cni.projectcalico.org/ipv4pools"='["demo-ipip-ippool"]'
```
or/and to verify
```
kubectl get ns wwwdemo -o yaml
```

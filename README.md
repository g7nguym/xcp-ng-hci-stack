# XCP-NG HCI STACK
A HCI Stack based on:
- XCP NG (Xen-based Hypervisor)
- Linstor (Software Defined Storage)
- Talos Linux (for Kubernetes Cluster)
## XCP-NG Installation ##
Install XCP-NG is straightforward, you can follow the official link here: https://docs.xcp-ng.org/installation/install-xcp-ng/  
This setup incudes 03 nodes cluster.
## XOA Installation ##
After XCP-NG is installed, you can access https://vates.tech/deploy/ and deploy XOA appliance. The process is very easy.
![image](https://github.com/user-attachments/assets/f1bb172e-a505-4053-8dff-d25bdf2999d2)  

## XCP-NG Cluster Setup ##
The XOA Appliance is accessible over `https:{ip_set_during_install}`  
* Register and update the appliance 
![image](https://github.com/user-attachments/assets/1dbffdb1-715e-4ae7-9b7a-b53609ba53b4)
* Rename the pool (optional)
Go to Home >> Pools >> Click on the pool
![image](https://github.com/user-attachments/assets/ea1fdd15-3fca-4610-917d-ee6e94649a89)
* Add remaining hosts into XOA
Go to New >> Server
![image](https://github.com/user-attachments/assets/885d6635-889e-459c-86a9-a9dedab4fda5)
* Add hosts into pool to form a cluster
Go back to Home >> Pools >> Select the pool that was renamed earlier
![image](https://github.com/user-attachments/assets/a00071d5-01a8-48aa-b56b-5f0814c819d7)
After all 03 hosts have been added into the pool, it should include all the hosts now
![image](https://github.com/user-attachments/assets/93b0417f-a678-4c7e-a8e5-87340140284c)
* Create network for the cluster
For this setup
  - 2x 1Gbps network will be used for management and VM traffic
  - 2x 10Gbps network will be used for storage synchronization
Go to New >> Network and create needed networks
![image](https://github.com/user-attachments/assets/54319370-7c46-4cd8-b0e7-23eb9aad53e6)
Each host should have 02 networks with necessary IPs as below
![image](https://github.com/user-attachments/assets/4f39a16b-6a6d-4a8b-8e7d-145d1bd33932)
* Create XOSTOR (Linstor) Storage
Go to XOSTOR and create XOSTOR storage.
At the time of this writing, XOSTOR only supports ThinLVM Pool. `/dev/sdb` will be used on the nodes to provide shared storage and `sync-net` is used for storage synchronization between the nodes.
![image](https://github.com/user-attachments/assets/ca1cc3a4-7b17-4927-b74f-a415e91bd5bc)

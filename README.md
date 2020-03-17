# OpenShift Service Mesh - Advanced Development - Homework







## Summary

**Main function**

Ansible playbook file **homework.yaml** is entry point for the prcess, which includes all operational tasks .

1. Install a ServiceMeshMemberRoll with a single member: bookinfo
Ensure that bookinfo project now includes the appropriate service mesh related labels.

2. Add service mesh data plane auto-injection annotation to bookinfo deployments.
Ensure that all of your bookinfo deployments now include the envoy sidecar proxy.

3. mTLS traffic between all services of the bookinfo application. 
If the bookinfo deployments include liveness and readiness probes, then customize them to use equivalent command based probes.

4. Create a Policy object for the deployments of the bookinfo namespace. Specify a mTLS mode of: STRICT.

5. Create appropriate TLS certs, DestinationRules, VirtualService, etc for your bookinfo application.  


## Engagement journal 

### Basic Requirements

User **admin** can log in as administrator on the master console.  The password is **r3dh4t1!**

User **user1** is bookinfo app admin.  The password is **r3dh4t1!**

Registry console URL is https://console-openshift-console.apps.cluster-$GUID.$GUID.sandbox235.opentlc.com.
These are related resources below

```shell
├── homework.yaml
├── hosts
├── mtls
│   └── cert.cfg
└── resources
    ├── bookinfo-service-gateway.yml
    ├── bookinfo-service-policy.yml
    ├── bookinfo-virtualservice.yaml
    ├── bookinfo.yaml
    ├── destination-rule-all-mtls.yaml
    ├── service-mesh-installation.yaml
    ├── service-mesh-roll.yaml
    └── service-mesh.yaml
```

## **Installation**

1. First execute the **sudo** command to ensure that you have operational execution authority, and then clone the prepared script from GitHub to the local environment.

```shell
[xxxx@bastion ~]$ sudo -i
[root@bastion ~]# git clone https://github.com/SammZhu/ServiceMeshHomework.git
```

2. Then go into the working directory and execute the Ansible playbook script to install the environment. The entire installation will take about an hour.

```shell
[root@bastion ~]# cd ServiceMeshHomework
[root@bastion ~]# ansible-playbook homework.yaml -e passwd=r3dh4t1! -i hosts
```

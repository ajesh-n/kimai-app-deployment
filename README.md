# kimai-app-deployment
Kimai is a multi-container timesheet management application deployment EKS

### Resources
- Amazon eks cluster
- Node group
- Dynamic provisioning EBS volume in cluster.
- Pod for kimai
- Pod for mysql

### Infra topology
[kimai eks](./kimai-infra.jpg)

- kimai service deployed as Kubenretes deployment containing the persistent volume AWS EBS to store HTML/php pages.
- MySQL service deployed as Kubenretes deployment containing Persistent volume AWS EBS to store MySQL data.
- Load balacer on the top application. The Load balancer will route the traffic to app pod, and pod will store data in MySQL pod by routing it via MySQL service.

#### Prerequisites
- The aws-ebs-csi-driver installed.

### Deployment

```kubectl apply -k .```
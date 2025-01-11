# MongoDB-helm-chart
A helm chart for Mongodb deployment with its replication feature.

![images](https://github.com/user-attachments/assets/1538d233-4830-4ac7-84b4-607fc34e128f)

## Introduction

Deploying MongoDB on Kubernetes with replication provides a scalable, highly available, and fault-tolerant database solution. This repository uses Helm to demonstrate the steps and configurations required to deploy a MongoDB replica set on Kubernetes. By leveraging Kubernetes' orchestration capabilities, you can ensure seamless failover, load balancing, and automated scaling for your MongoDB clusters.

## Key Features

1. **MongoDB Replica Set:**

  -> A replica set consists of multiple MongoDB instances, ensuring high availability and data redundancy.

  -> Automatic failover: A secondary node is promoted to the primary if the primary node becomes unavailable.

2. **Kubernetes Orchestration:**

  -> Uses StatefulSets for managing MongoDB pods with stable network identities.

  -> PersistentVolumeClaims (PVCs) ensure durable storage for database data.

3. **Scalability:**

  -> Scale the replica set by adjusting the replica count in the values.yaml.

  -> Additional nodes automatically join the replica set when scaled.

4. **Security:**

  -> Secret management using Kubernetes Secrets for sensitive data like passwords.

5. **Automation:**

  -> Configuration scripts or Job containers handle the initialization of the MongoDB replica set.

## Prerequisites

Before you begin, ensure you have the following:
- A Kubernetes cluster (v1.18+)
- Helm (v3.0+)
- The Image Pull Secret of the registry you are using and add the name of the secret in your service account inside values.yaml.

```shell
  serviceAccount:
    imagePullSecrets:
      name1: <name of your Image Pull Secret>
```

## Installation Process

1. **Clone the Helm Repository**

   ```sh
   git clone https://github.com/cyberRuptor/mongodb-helm-chart.git
   ```
   
2. **Make changes inside values.yaml**<br>

   Make the changes if you want to according to your use cases. Like resources, the Password for mongodb inside the secret, and the Type of the service whether it is Headless, ClusterIP, or LoadBalancer. You can define your own security contexts also.

   -> To change the service type in statefulset.

   ```shell
    service:
      type: Headless    #set it as LoadBalancer or ClusterIP if you need to create clusterIP service or to use load balancer for external connectivity.
   ```

   just define type as
   Headless for headless service type<br>
   ClusterIP for clusterIP service type<br>
   LoadBalancer for loadBalancer service type<br>
   






/*In next upgrade we will take care of SCRAM security feature and use Kubernetes probes. also adding flexibility Designed for both development and production environments. Can be deployed on any Kubernetes cluster, including managed services like AKS, EKS, GKE, or OpenShift./*

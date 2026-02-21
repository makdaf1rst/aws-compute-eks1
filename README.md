[README.md](https://github.com/user-attachments/files/25457252/README.md)
<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Launch a Kubernetes Cluster

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-compute-eks1)

**Author:** saqibh49@gmail.com  
**Email:** saqibh49@gmail.com

---

## Launch a Kubernetes Cluster

![Image](http://learn.nextwork.org/grateful_white_lucky_bat/uploads/aws-compute-eks1_e5f6g7h8)

---

## Introducing Today's Project!

In this project, I will launch an EC2 instance, create a Kubernetes cluster, monitor it with CloudFormation, and access it using IAM — all to get hands-on experience with how Kubernetes runs on AWS. I'm doing this project because Kubernetes is a big deal in production environments, and understanding how to set up and manage clusters is essential for any cloud engineer.

### What is Amazon EKS?

### One thing I didn't expect

### This project took me...

---

## What is Kubernetes?

Kubernetes is a container orchestration platform, which basically means it coordinates and manages containers across all your servers. It makes sure containers are running where they should be, scales them up or down automatically based on demand, and restarts them if something crashes.

Companies and developers use Kubernetes because without it, you'd have to manage every container manually — starting them, monitoring them, scaling them one by one, and swapping them out during updates without causing downtime. That's fine for a few containers, but when you're dealing with hundreds or thousands, it becomes impossible to keep up. Kubernetes handles all of that automatically, so you can focus on actually building your app.

I used eksctl to create my Kubernetes cluster on AWS since it simplifies the whole process into a single command instead of having to configure everything manually. The create cluster command I ran defined the cluster name, the region to deploy it in, the type and number of nodes, and the Kubernetes version to use.

I initially ran into two errors while using eksctl. The first one was because eksctl wasn't installed on my EC2 instance yet, so my terminal didn't even recognize the command. The second one was because my EC2 instance didn't have the right IAM permissions to create AWS resources like an EKS cluster, so I had to set up an IAM role with the correct policies before it would work.

![Image](http://learn.nextwork.org/grateful_white_lucky_bat/uploads/aws-compute-eks1_ff9bfc221)

---

## eksctl and CloudFormation

CloudFormation helped create my EKS cluster because when eksctl runs, it actually uses CloudFormation under the hood to provision all the infrastructure the cluster needs. It created VPC resources because every EKS cluster needs its own networking setup — things like subnets, route tables, and security groups — so the cluster's nodes can communicate with each other and the internet.

There was also a second CloudFormation stack for my node group, which is the set of EC2 instances that actually run my containers. The difference between a cluster and node group is that the cluster is the overall Kubernetes control plane that manages everything, while the node group is the actual worker machines that do the heavy lifting of running applications.

![Image](http://learn.nextwork.org/grateful_white_lucky_bat/uploads/aws-compute-eks1_w3e4r5t6)

---

## The EKS console

I had to create an IAM access entry in order to give my IAM user permission to interact with my Kubernetes cluster. An access entry is basically a way of telling EKS which IAM users or roles are allowed to access the cluster and what they can do in it. I set it up by adding my IAM user's ARN and attaching the AmazonEKSClusterAdminPolicy so I'd have full access to view and manage the cluster from the console.

It took about 20 minutes to create my cluster. Since I'll create this cluster again in the next project of this series, maybe this process could be sped up if I saved my eksctl command as a script or used a configuration file so I don't have to type everything out again and can just run it with one command.

![Image](http://learn.nextwork.org/grateful_white_lucky_bat/uploads/aws-compute-eks1_e5f6g7h8)

---

## EXTRA: Deleting nodes

---

---

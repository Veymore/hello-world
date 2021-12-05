Best Practices:
- For basic apps: stick to docker official images for the containers -> evolve from there
- Work on Deployment-Layer, let k8s manage everything beneath it by using etcd data
- Production environments need atleast 2 Master nodes for redundancy - more desired if the enviroment scales up
- There should not be any workload other than the k8s master services running on the master nodes
- All the workload should be handles by the worker nodes

Commands:

- Create
  - kubectl create deployment [name]
- Edit
  - kubectl edit deployment [name]
- Delete
  - kubectl delete deployment [name]

Status:

- kubectl get nodes | pod | services | replicaset | deployment

Debugging:

- Logging
  - kubectl logs [pod name]
- Pod-Terminal
  - kubectl exec -it [pod name] -- bin/bash

Implementation of configuration files:
- Create/Edit
  - kubectl apply -f [file name]
- Delete
  - kubectl delete -f [file name]

*on yaml-files:
- strict indentation
- yaml validator to check for indentation

Structure of configuration files:
- configuration files are split into 3 subparts:
  - metadata        - contains name and labels
  - spec            - contains the targeted status
  - status*         - contains the current status
  *information about the current status are delivered by etcd process on the master nodes
  
  Services:
  - in order to create a service for an underlying pod there has to be a matching label
    - the label binds pod and service together
    - the advantage of using a label for different deployments/pods under a service is that you can have different
      differen deployments under one service
  
  Deployments:
  - in order to deploy a new pod into an existing deployment this need to be done:
    - edit the existing configuration and use k8s selfhealing feature by comparing etcd value
  
 Basic structure of a cluster:
 ![components-of-kubernetes](https://user-images.githubusercontent.com/95536830/144724254-026ca6cd-9aa2-4eb2-9591-1ef65af6f054.png)
 Source and further reference: https://v1-18.docs.kubernetes.io/docs/concepts/overview/components/

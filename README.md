# hello-world

Prerequisites:
(in preparation for the challenge)
Kubernetes Tutorial used:
1. Kubernetes Tutorial for Beginners [FULL COURSE in 4 Hours] - https://www.youtube.com/watch?v=X48VuDVv0do

Exercise 1 - Deploy a Kubernetes Cluster
task:
The cluster can be deployed using Infrastructure as Code, via Script, Playbook or manually. The cluster 
should be reachable from the local machine of the challenge-taker via kubectl and “kubectl get nodes” 
should display at least 2 nodes with Status “Ready”. Any infrastructure (e.g. localhost, local VM, containers, 
Public Cloud) and provisioner (e.g. rancher, k3s, kind, AKS, kube-spray, kubeadm) can be used.
Bonus: The cluster–deployment is automated.

solution:
- Minimum working build:
  - Deciding for a tech-stack:
    - Deployment: manual
    - Infrastructure: local vm, multiple physical hosts (if more resources are needed)
    - Provisioner: minikube
  - points fulfilled:
    - Cluster deployed
    - Cluster reachable from local machine
    - kubectl get nodes shows 2 nodes
      - needs additional configuration für multi-node support, might have to adjust techstack if network troubles arise
    - nodes show status "ready"
    - can be automated via bash-script
  - points open:
    - is not automated

- optimized build for optional tasks:
  - Deciding for a tech stack:
   - to be defined

Exercise 2 - Hello-World Container
task:
A Hello-World container with a webserver of any technology should be deployed to the cluster. The 
webserver should be accessible from the browser of the challenge-takers machine.

solution:
- Minimum working build:
  - Deciding for a tech-stack:
    - Webserver: nginx
    - Image: official image from docker hub
    - HTML commit: manual insertion via ssh
    - Exposing: via loadbalancer
  - points fulfilled:
    - container is deployed
    - accessible from the browser of the challenge-takers machine
  - points open:
    - is not preparing for the next task
    - will need to swap loadbalancer for ingress

Exercise 3 - High-availability & elasticity
The container should be deployed with multiple instances and traffic to the instances should be distributed 
using round-robin.
Bonus: The instances of the container are auto-scaling based on CPU-load.

solution:
- Minimum working build:
  - Deciding for a tech-stack:
    - LoadBalancing: kubeproxy (or hba) -> needs further research on round robin capabilities 
      and if hba can do both and kubeproxy can be ignored?
    - auto-scaling: hba
  - points fulfilled:
    - traffic is distributed evenly
    - scaling will be based on cpu-load
  - points open:
    - none

- optimized build for optional tasks:
  - Deciding for a tech stack:
   - probably wont need any adjusting for optimization as of right now

Exercise 4 - Ingress-Controller
The container should be served through an ingress-controller which terminates TLS and returns a valid 
certificate (self-signed or signed by public CA).
solution:
- Minimum working build:
  - Deciding for a tech-stack:
    - Certificate: self-signed via PowerShell
    - TLS: via yaml-configuration-file
  - points fulfilled:
    - Certificate
    - TLS
    - Ingress deployed
    - Service is served by it
    - Ingress is reachable from local host
  - points open:
    - none

Exercise 5 - Optional: CI/CD-Pipeline
Done tasks 1- 4 into a CI/CD-Pipeline (Gitlab CI, Github Actions, Azure DevOps, Jenkins or a tool from your 
choice).

- optimized build for optional tasks:
  - Deciding for a tech stack:
   - probably wont need any adjusting for optimization as of right now

Exercise 6 - Optional: Network Hardening
The ingress controller should be hardened on a network level using an industry-standard. Hardening should be automated/persisted and a hardened configuration should be deployed by the CI/CD pipeline

- optimized build for optional tasks:
  - Deciding for a tech stack:
   - probably wont need any adjusting for optimization as of right now

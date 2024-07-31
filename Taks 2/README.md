Task 2: K8s App restrictions over network

Description:
my-app-deployment and cache-deployment deployed, and my-app-deployment deployment exposed through a service named my-app-service . Create a NetworkPolicy named my-app-network-policy to restrict incoming and outgoing traffic to my-app-deployment pods with the following specifications:
- Allow incoming traffic only from pods within the same namespace.
- Allow incoming traffic from a specific pod with the label app=trusted
- Allow outgoing traffic to pods within the same namespace.
- Deny all other incoming and outgoing traffic.

Deliverable: All manifest files.


Solution:
    I have created a 2 namespace, 4 pods, a service and a network policy solution to achieve desired goals using single infra.yaml file.

    There are two namespaces 
        1) application :- my-app-deployment and cache-deployment will be deploying here.
        2) verify      :- verify-deployment and trusted-deployment will deploy here to verify incoming and outgoing traffic.
    
    The Manifest file will deploy 4 pods using same Nginx image. (I was not having sample code that can use caching functionality.). Two pods in each NameSpace.

    Let's see the solution to each challenge mentioned in the requirements. (all below references are from my-app-network-policy network policy)


    - Create a NetworkPolicy named my-app-network-policy to restrict incoming and outgoing traffic to my-app-deployment pods
    solution:- We have used "podSelector" with "matchLabels" to only apply network policy for deployment/pod my-app-deployment.(Line number 119 to 121)

    - Allow incoming traffic only from pods within the same namespace.
    solution:- We have used " - podSelector: {}" in "From" section of "ingress" to allow all incoming communication to pod from same namespace. (Line number 123 and 124)


    - Allow incoming traffic from a specific pod with the label app=trusted
    solution:- We have used "podSelector" with "namespaceSelector" to allow traffic from pod with lable "app: trusted" from any namespace. (Line number 125 to 129)

    - Allow outgoing traffic to pods within the same namespace.
    solution:- we have used condition "- podSelector: {}" in "egress" section to allow traffic from only same namespace. (Line number 131,132)

    - Deny all other incoming and outgoing traffic.
    solution:- As we have already applied both Ingress and Egress policy on pod, by default all other traffic will be blocked. In case we want to make additinal rule then we can use below syntax. 

        To block ingress= "- from: []"
        To block egress = "- to: []"




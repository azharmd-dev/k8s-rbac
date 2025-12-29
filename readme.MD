* This command displays the aws-auth ConfigMap, which controls authentication and authorization in an Amazon EKS cluster. 
*** It defines which AWS IAM users and roles are allowed to access the Kubernetes cluster and what permissions they have.
```
kubectl get configmap aws-auth -n kube-system -o yaml
```
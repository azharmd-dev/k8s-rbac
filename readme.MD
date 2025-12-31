* EKS IAM mapping and Kubernetes RBAC setup
    - This command displays the aws-auth ConfigMap, which controls authentication and authorization in an Amazon EKS cluster. 
    - It defines which AWS IAM users and roles are allowed to access the Kubernetes cluster and what permissions they have.
    ```
    kubectl get configmap aws-auth -n kube-system -o yaml
    ```

    - The following command updates the local kubeconfig file to enable access to the specified Amazon EKS cluster.
    ```
    aws eks update-kubeconfig --region us-east-1 --name robomart-dev
    ```
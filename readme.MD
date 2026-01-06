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
    - This command tells you who you are authenticated as in AWS. It’s commonly used to verify credentials, roles, and accounts.
        ```
        aws sts get-caller-identity
        ```
* OpenID connect create
    ```
    eksctl utils associate-iam-oidc-provider --cluster robomart-dev --approve
    ```
* Create service account
    ```
    eksctl create iamserviceaccount --cluster robomart-dev --name secret-reader --namespace robomart --attach-policy-arn arn:aws:iam::522534289017:policy/RoboMartMySQLReader --approve
    ```
* Get secret value
    ```
    aws secretsmanager get-secret-value --secret-id robomart/dev/mysql_password --query SecretString --output text
    ```


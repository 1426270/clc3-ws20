# Exercise 3.5: Using Namespaces

In this exercise, you will create a namespace for your Kubernetes resources (i.e., deployments, services, pods). Afterwards, you will modify the deployment manifest from exercise 3.2, to create a deployment in this particular namespace.

## Instructions

1. Create a file `namespace.yaml` with the following content:

    ```yaml
    apiVersion: v1
    kind: Namespace
    metadata:
      name: demo-environment
    ```

1. Apply the *namespace* to your Kubernetes cluster using: 
    
    ```source
    kubectl apply -f namespace.yaml
    ```

    * This will create the namespace `demo-environment` where you can add Kubernetes resources (i.e., deployments, services, pods) to.

1. Modify the deployment from exercise 2.3. so that the demo app will be deployed in the `demo-environment` namespace. Therefore, extend the `metadata` as follows:
    
    ```yaml
    metadata:
      name: demo
      namespace: demo-environment
    ```

1. Apply the modified deployment by executing: 

    ```console
    kubectl apply -f deployment.yaml
    ```

1. Check the resources in the `demo-environment` namespace with:
    
    ```console
    kubectl get deployments --namespace demo-environment
    ```

    ```console
    kubectl get pods --namespace demo-environment
    ```
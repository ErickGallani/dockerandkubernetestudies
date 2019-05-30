- ## What is Kubernetes
    - Easier to scale
    - Gives more control over the container scaling
    - You can have different container configuration per node

- ## Why use Kubernetes
    - When you need to run many different containers with different images

- ## What's and Why's
![What's and Why's](/assets/what_and_why_kubernetes.png "What's and Why's")

- ## Example of kubernetes cluster
![Kubernetes Cluster](/assets/kubernetes_cluster.png "Kubernetes Cluster")

- ## Api version 
![Api version](/assets/api_version_kubernetes.png "Api version")

- ## Services
    - Have 4 types
        - ClusterIP
        - NodePort
            - Exposes a container to the outside world (only good for dev purposes!!)
        - LoadBalancer
        - Ingress

- ## Kubernetes apply config command
![Kubernetes apply config command](/assets/kubernetes_apply_config_command.png "Kubernetes apply config command")


- ## Kubernetes show pods command
![Kubernetes show pods command](/assets/kubernetes_show_pods_command.png "Kubernetes show pods command")

- ## Check VM Ip command
        $> minikube ip

- ## Declarative vs Imperative deployment strategy
![Declarative vs Imperative deployment strategy](/assets/declarative_imperative.png "Declarative vs Imperative deployment strategye")

- ## Kubernetes describe command - used do inspec objects
![Kubernetes describe command](/assets/kubernetes_describe_command.png "Kubernetes describe command")

- ## Kubernetes some object types example
![Kubernetes some object types example](/assets/kubernetes_object_types.png "Kubernetes some object types example")

- ## Kubernetes delete command
![Kubernetes delete command](/assets/kubernetes_delete_command.png "Kubernetes delete command")

- ## Imperative command to update an object property
        $> kubectl set <property> <object_type>/<object_name> <container_name> = <new_property_value>
        $> (Example)
        $> kubectl set image deployment/my_deployment client_container = mynew/image:v2

- ## To be able to execute docker cli commands on the minikube docker-server, execute the following command on the terminal Ps.: this will change temporaly only the current terminal tab to connect to the minikube docker env
        $> eval $(minikube docker-env)

- ## Kubernetes Object Types
![Kubernetes Object Types](/assets/kubernetes_object_types_clusterip.png "Kubernetes Object Types")

- ## Kubernetes architecture for project example
![Kubernetes architecture for project example](/assets/kubernetes_architecture.png "Kubernetes architecture for project example")

- ## Volumes in kubernetes
![Volumes in kubernetes](/assets/volume_in_kubernetes.png "Volumes in kubernetes")

- ## Persistent Volume access modes
![Persistent Volume access modes](/assets/kubernetes_access_mode_persistent.png "Persistent Volume access modes")

- ## Get storages available
        $> kubectl get storageclass

- ## Get more detailed information about storages available
        $> kubectl describe storageclass

- ##  Storage documentation
    https://kubernetes.io/docs/concepts/storage/storage-classes
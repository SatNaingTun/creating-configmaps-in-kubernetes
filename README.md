# CONFIGMAPS OBJECTS
## WHAT ARE CONFIGMAPS?

1. Configmaps are kubernetes objects that allow us to decouple the configuration
from pods and components
2. So with configmaps, you can apply your custom confiration to pods and containers
and avoiding hardcoding the configuration data in the application code
3. It stores the configuration data as key-value pairs
But configmaps are not designed to store sensitive data like passwords
For that we use another k8s object called SECRETS
4. configmaps must be created before referencing them in pods

## CREATING CONFIGMAPS

### Creating ConfigMaps using the imperative method

We can create configmaps using the imperative method throw the kubectl command kubectl create configmap **configmap-name** **data-source**
data-source can be a directory, afile (--from-file=**path-to-file/dir**) or a literal value (--from-literal=**key=value**)

- From dir:
First, we create the files needed for the configmap in a directory and then we use this command to create the configmap
    kubectl create configmap **configmap-name** --from-file=**path-to-dir**

- From file:
First, we create the file needed for the configmap and then we use this command to create the configmap using the file
    kubectl create configmap **configmap-name** --from-file=**path-to-file**

- Using literal values:
Here we can create configmaps directly by speficying the key-value pairs that we want to store like this
    kubectl create configmap **configmap-name** --from-literal=**key=value**

### Creating ConfigMaps using the declarative method

We can also create configmaps using the declarative methods throw yaml files
First, we create the yaml file needed to create a configmap
- apiVersion: v1
- kind: ConfigMap
- metadata:
    - name: my-app-config
- data:
    - username: "john"
    
then, we use the kubectl create command to create the configmap
                kubectl create -f my-app-config.yaml         

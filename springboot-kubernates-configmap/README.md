# SPRINGBOOT K8 CONFIGMAP 
> Description: \
> springboot application which is using k8 config map \
> for configurations of the application.

----

### TO BUILD THE APPLICATION
* $ mvn clean package

### TO EXECUTE AND TEST LOCALLY
* $ java -jar target/springboot-kubernates-configmap.jar

### Test the end point 
* $ curl localhost:8080/api/message

----

## TO CREATE A DOCKER IMAGE
### To build the docker image and tag
* $ docker build -f Dockerfile -t adarshkumarsingh83/springboot-kubernates-configmap .

### to push the docker image to the docker hub
* $ docker push adarshkumarsingh83/springboot-kubernates-configmap

### TO DO THE DEPLOYMENT OF THE KUBE CONFIG AND SERVICE
* $ kubectl apply -f $(pwd)/kubernates/config.yaml
* $ kubectl apply -f $(pwd)/kubernates/deploy.yaml


### TO VIEW THE DETAILS
* $ kubectl get all

### TO VIEW THE POD DETAILS
* $ kubectl get pod

### TO VIEW THE CONFIG MAP DETAILS
* $ kubectl describe configmap kubernates-configmap-store

### TO VIEW THE LOGS OF THE POD
* $ kubectl logs <pod-name> -f

* $ minikube service springboot-kubernates-configmap
* OR
* $ kubectl port-forward svc/springboot-kubernates-configmap 8080:8080

### TO TEST THE REST END POINT
* $ curl localhost:8080/api/message

### NOTE TO SOME CHANGES IN THE PROPS OF
* config.yml and then do the apply again then reload the config

### TO RELOAD THE CHANGES
* $ curl -d {} -H "Content-Type:application/json" http://localhost:8080/actuator/refresh

### TO TEST THE REST END POINT AFTER CHANGE
* $ curl localhost:8080/api/message

### FOR DELETING DEPLOYMENT AND SERVICE
* $ kubectl delete services springboot-kubernates-configmap
* $ kubectl delete deployment springboot-kubernates-configmap


### TO DELETE ALL THE CONTAINERS WITH VOLUMES
* $ docker rm -vf $(docker ps -a -q)

### TO DELETE ALL THE IMAGES
* $ docker rmi -f $(docker images -a -q)

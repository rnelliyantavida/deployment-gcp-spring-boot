# Deploy Spring boot app on GCP
## **_Deploy On GKE:_**
---
1. Create a springboot application and add Dockerfile to it.
2. Create a jar file and run it on cmd using **_java -jar file_name.jar_** 
3. Open google SDK shell, go to springboot project folder
4. **_gcloud init_**
5. **_docker build -t gcr.io/project_name/image_name:tag ._** // to create docker image
6. **_docker push gcr.io/project_name/image_name:tag_** // push the image to google container registery and check there is a registry in gcp.
7. Create a cluster in kuberenetes engine and Click on connect in kuberenetes engine in gcp
8. **_kubectl create deployment image_name(from container registry on gcp) --image=gcr.io/project_name/image_name:tag_** // create deployment
9. **_kubectl expose deployment image_name --type=LoadBalancer --port 80 --target-port 8080(port_number from springboot project)_** // expose deployment(create service)
10. check service by command **_kubectl get service_** 
11. Copy EXTERNAL-IP and run like http://35.238.224.186:80/hello
12. **_kubectl delete service gke-springboot_** // delete the service
13. **_kubectl delete deployment gke-springboot_** // delete deployment

## **_Deploy on Compute Engine, VM instance:_** 
---
1. Create springboot project and upload it to github
2. Install Java : **_sudo apt-get install openjdk-8-jdk_**
3. Git : **_sudo apt-get install git_**
4. Maven : **_sudo apt install maven_**
5. Curl : **_sudo apt install curl_**
6. Nano(Editor) : **_sudo apt-get install nano_**
7. Clone the Spring Boot project from your Github repository
8. **_mvn spring-boot:run_** // run the spring-boot project on VM
9. Expose 8080 port on the VM to make the Spring App accessible to the Internet :
    - Select View Network details
    - Go to Firewall Settings(Rules)
    - Go to default-http-server and click on the edit button
    - Add the 8080 port to the TCP and click the Save button to make the changes
    - Verify that Spring Boot App is running 



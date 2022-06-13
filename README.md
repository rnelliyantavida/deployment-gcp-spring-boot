# Deploy Spring boot app on GCP
## **_Deploy On GKE:_**
---
	1. Create a springboot application and add Dockerfile to it.
	2. Create a jar file and run it on cmd using java -jar file_name.jar 
        3. Open google SDK shell, go to springboot project folder
        4. gcloud init
        5. docker build -t gcr.io/project_name/image_name:tag . // to create docker image
	6. docker push gcr.io/project_name/image_name:tag // push the image to google container registery and check there 
           is a registry in gcp.
	7. Create a cluster in kuberenetes engine and Click on connect in kuberenetes engine in gcp
        8. kubectl create deployment image_name(from container registry on gcp) --image=gcr.io/project_name/image_name:tag // create deployment
	9. kubectl expose deployment image_name --type=LoadBalancer --port 80 --target-port 8080(port_number from springboot project) // expose
           deployment(create service)
	10.check service by command kubectl get service then you will get a window like this
		NAME             TYPE           CLUSTER-IP     EXTERNAL-IP      PORT(S)        AGE
		gke-springboot   LoadBalancer   10.104.6.106   35.238.224.186   80:30135/TCP   70s
		kubernetes       ClusterIP      10.104.0.1     <none>           443/TCP        92m
	11. Copy EXTERNAL-IP and run with http://35.238.224.186:80/hello
	12. kubectl delete service gke-springboot // delete the service
	13. kubectl delete deployment gke-springboot // delete deployment

## **_Deploy on Compute Engine, VM instance:_** 

	1. Create springboot project and upload it to github
	2. Install Java : sudo apt-get install openjdk-8-jdk
	3. Git : sudo apt-get install git
	4. Maven : sudo apt install maven
	5. Curl : sudo apt install curl
	6. Nano(Editor) : sudo apt-get install nano
	7. Clone the Spring Boot project from your Github repository
	8. mvn spring-boot:run // run the spring-boot project on VM
	9. Expose 8080 port on the VM to make the Spring App accessible to the Internet
		-> Select View Network details
		-> Go to Firewall Settings(Rules)
		-> Go to default-http-server and click on the edit button
		-> Add the 8080 port to the TCP and click the Save button to make the changes
		-> Verify that Spring Boot App is running 



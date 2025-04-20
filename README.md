# Deploy Spring boot app on GCP
## **_Deploy On GKE:_**
---

1. Create a Spring Boot application and add a `Dockerfile` to it.  
2. Build the JAR file and run it using the command: `java -jar file_name.jar`  
3. Open the Google Cloud SDK Shell and navigate to your Spring Boot project directory.  
4. Run `gcloud init` to initialize the Google Cloud configuration.  
5. Build the Docker image using:  
   `docker build -t gcr.io/project_name/image_name:tag .`  
6. Push the Docker image to Google Container Registry using:  
   `docker push gcr.io/project_name/image_name:tag`  
   > Make sure the registry is created and visible in your GCP Console.  
7. In the Kubernetes Engine section of GCP, create a cluster and click **Connect** to access it.  
8. Create a deployment using the following command:  
   `kubectl create deployment deployment_name --image=gcr.io/project_name/image_name:tag`  
9. Expose the deployment as a service:  
   `kubectl expose deployment deployment_name --type=LoadBalancer --port=80 --target-port=8080`  
   > Replace `8080` with the actual port your Spring Boot app is running on.  
10. Check the service status using:  
    `kubectl get service`  
11. Copy the **EXTERNAL-IP** and test the endpoint, e.g., `http://EXTERNAL-IP:80/hello`  
12. To delete the service, run:  
    `kubectl delete service service_name`  
13. To delete the deployment, run:  
    `kubectl delete deployment deployment_name`

---

## **_Deploy on Compute Engine, VM instance:_** 
---
1. Create a Spring Boot project and upload it to GitHub.  
2. Install Java:  
   sudo apt-get install openjdk-8-jdk  
3. Install Git:  
   sudo apt-get install git  
4. Install Maven:  
   sudo apt install maven  
5. Install Curl:  
   sudo apt install curl  
6. Install Nano (text editor):   
   sudo apt-get install nano  
7. Clone the Spring Boot project from your GitHub repository.  
8. Run the Spring Boot project on the VM:  
   mvn spring-boot:run  
9. Expose port 8080 on the VM to make the Spring Boot app accessible over the internet:  
   - Select **View Network Details**  
   - Go to **Firewall Settings (Rules)**  
   - Open **default-http-server** and click the **Edit** button  
   - Add port **8080** to the TCP list and click **Save**  
   - Verify that the Spring Boot app is running  

---



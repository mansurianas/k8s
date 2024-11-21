day 9 task


==========
1. Create a Service named myapp of type ClusterIP that exposes port 80 and maps to the target port 80.

create service.yaml 
![Screenshot 2024-11-21 114552](https://github.com/user-attachments/assets/03fb9f60-c792-4ac4-83b1-dded1289f555)

![Screenshot 2024-11-21 114514](https://github.com/user-attachments/assets/5df71b37-7dd2-46e6-90bb-b713da901189)

==============
2. Create a Deployment named myapp that creates 1 replica running the image nginx:1.23.4-alpine. Expose the container port 80'

   create deployment.yaml
   apiVersion: apps/v1
kind: Deployment
metadata:
  name: myapp
spec:
  replicas: 1
  selector:
    matchLabels:
      app: myapp
  template:
    metadata:
      labels:
        app: myapp
    spec:
      containers:
        - name: myapp
          image: nginx:1.23.4-alpine
          ports:
            - containerPort: 80

   now  kubectl apply -f deployment.yaml
![Screenshot 2024-11-21 120301](https://github.com/user-attachments/assets/4eca7d02-e09b-48ce-aa06-2b22a736429f)



![Screenshot 2024-11-21 120350](https://github.com/user-attachments/assets/e1d4c391-6c8f-4cc0-9b4d-d2ac05b675f4)


3 task - ----------
           Scale the Deployment to 2 replicas.

           
   ![Screenshot 2024-11-21 120743](https://github.com/user-attachments/assets/b3d5426a-9759-4327-82ad-1bf9ccf39d93)


---- task 4 ============

   Create a temporary Pod using the image busybox and run a wget command against the IP of the service.
   ![Screenshot 2024-11-21 133721](https://github.com/user-attachments/assets/dbab60c7-f5b1-455d-b94d-1fc8507e3ec0)


task 5 ----==========


 Change the Service Type
Modify the Service to Use NodePort or LoadBalancer
![Screenshot 2024-11-21 134100](https://github.com/user-attachments/assets/11d734b6-cb55-4e04-8968-ebdb82e9785f)

![Screenshot 2024-11-21 134153](https://github.com/user-attachments/assets/6bcdc630-6f18-4b7b-8971-89b144047d4a)



 Get the Node IP Address
Find the IP Address of the Node
![Screenshot 2024-11-21 134330](https://github.com/user-attachments/assets/aaf1371e-3d75-4573-b620-a7fc4861d0d5)


3: Run the wget Command
Run wget from Outside the Cluster


This command should return the HTML content served by the Nginx server running in your Pods.
![Screenshot 2024-11-21 134626](https://github.com/user-attachments/assets/a191c40a-9201-43dd-835b-100c3c05542f)




task 6 --------------=============


vi service.yaml change type do NodePort 
![Screenshot 2024-11-21 135039](https://github.com/user-attachments/assets/5b3a724b-1d2f-4c09-b916-2da2d360d2c7)


task 7-------------------============
Run a wget command against the service outside the cluster


Get the Node IP Address
Since your nodes do not have external IPs, you will use the internal IP of the node. From the previous command, you can see the internal IP of your node (e.g., 172.30.2.2).

 Run the wget Command


![Screenshot 2024-11-21 135216](https://github.com/user-attachments/assets/43a427df-821e-4c23-b74f-6c13c5f57367)




task 8 ----------------==========
Discuss: Can you expose the Pods as a service without a deployment?

1. create a Pod:
   ![Screenshot 2024-11-21 141015](https://github.com/user-attachments/assets/5f9edc86-e335-4109-a899-e961b88a63d7)
2. create a service Create a Service: After the Pod is running, you can expose it using a Service.
 apiVersion: v1
kind: Pod
metadata:
  name: my-nginx
  labels:
    app: my-nginx  # Add a label to the Pod
spec:
  containers:
    - name: nginx
      image: nginx:latest
      ports:
        - containerPort: 80


kubectl apply -f my-nginx-service.yaml



   
3.Access the Service: 
wget -qO- http://<NodeIP>:<NodePort>

   wget -qO- http://192.168.1.6:80

to seee IP 
![image](https://github.com/user-attachments/assets/bc7582e7-f711-4d64-82bf-bb7ba54e95da)

   






Implications of Exposing Pods Directly
Lack of Resilience: If the Pod crashes, the Service won’t have any Pods to send traffic to. Deployments keep Pods running.

No Scaling: You can't easily create more copies of a single exposed Pod. Deployments allow easy scaling.

Manual Management: Updating a Pod requires deleting it and creating a new one. Deployments automate this.

Limited Load Balancing: Exposing one Pod doesn’t distribute traffic. Deployments manage multiple Pods for load balancing.

When to Expose Pods Directly
Testing and Development: Good for quick tests with a single instance.

Simple Use Cases: Works for basic applications that don’t need reliability.

Learning: Helps understand Kubernetes without complexity.

Summary
Exposing a Pod directly is simple for testing or learning but lacks reliability and scalability. Use Deployments for production.








   

   

Replicaset

Create a new Replicaset based on the nginx image with 3 replicas
![image](https://github.com/user-attachments/assets/8f6ce2cf-f01c-497e-9ec2-ddc4ce348cf3)


![image](https://github.com/user-attachments/assets/3f1c32ac-0e81-4c63-8af2-8ca3eff6253c)



Update the replicas to 4 from the YAML

![image](https://github.com/user-attachments/assets/990ac87e-942f-49b1-aa76-977df69cbdcc)




Update the replicas to 6 from the command line

![image](https://github.com/user-attachments/assets/60e1e0e3-becc-4d2a-b14d-6bbed46077e5)





Deployment

1. Create a Deployment named nginx with 3 replicas. The Pods should use the nginx:1.23.0 image and the name nginx. The Deployment uses the label tier=backend. The Pod template should use the label app=v1.




![image](https://github.com/user-attachments/assets/9ff21bd1-8c45-44b7-8d4c-521c0009c1ef)



2.  List the Deployment and ensure the correct number of replicas is running.

![image](https://github.com/user-attachments/assets/787698de-0a3b-4ea7-a45f-f37c4f26d110)



![image](https://github.com/user-attachments/assets/bd0054b9-1559-49fa-a21d-d755e878c6e5)


Update the image to nginx:1.23.4.

![image](https://github.com/user-attachments/assets/a86e7e15-b9c3-4c5e-ac04-3ef0ef7c12b0)



Verify that the change has been rolled out to all replicas.

![image](https://github.com/user-attachments/assets/0fa12042-7473-4b01-8c99-f7c4e44ef2f3)




Assign the change cause "Pick up patch version" to the revision.

![image](https://github.com/user-attachments/assets/43e9773a-46dc-461c-9c15-dc7df0f150bd)



Scale the Deployment to 5 replicas.


![image](https://github.com/user-attachments/assets/a5233a04-f142-4ee0-9510-3e181517421f)



Have a look at the Deployment rollout history.

![image](https://github.com/user-attachments/assets/66914b1a-45e6-43ca-a7bc-bc64cb5ef89e)



Revert the Deployment to revision 1.


![image](https://github.com/user-attachments/assets/677d4a65-d447-4ff8-9d02-8c1bde735413)






Ensure that the Pods use the image nginx:1.23.0.




![image](https://github.com/user-attachments/assets/67a19d1b-9194-4762-a436-c922b8c581d2)





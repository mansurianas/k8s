day 10 

1=======
Create two namespaces and name them ns1 and ns2

 
 answer :
 
controlplane $ kubectl create namespace ns1
namespace/ns1 created



controlplane $ kubectl create namespace ns2



namespace/ns2 created
controlplane $ kubectl get ns
NAME                 STATUS   AGE
default              Active   14d
kube-node-lease      Active   14d
kube-public          Active   14d
kube-system          Active   14d
local-path-storage   Active   14d
ns1                  Active   25s
ns2                  Active   12s


task 2==============
Create a deployment with a single replica in each of these namespaces with the image as nginx and name as deploy-ns1 and deploy-ns2, respectively


kubectl create deployment deploy-ns1 --image=nginx --namespace=ns1
kubectl create deployment deploy-ns2 --image=nginx --namespace=ns2


task 3=====================

Get the IP address of each of the pods (Remember the kubectl command for that?)

![Screenshot 2024-11-21 165240](https://github.com/user-attachments/assets/bf2ffcf8-e247-4e4e-b98a-623d6cd48ad1)


task 4 ===========
Exec into the pod of deploy-ns1 and try to curl the IP address of the pod running on deploy-ns2


![Screenshot 2024-11-21 165704](https://github.com/user-attachments/assets/f9393212-014c-443f-9dfb-c3aabe780269)


task 5 ==================

Now scale both of your deployments from 1 to 3 replicas.

![Screenshot 2024-11-21 170240](https://github.com/user-attachments/assets/1d28bdbb-c5eb-4114-97cb-9a39740ef758)


task 6====================

Create two services to expose both of your deployments and name them svc-ns1 and svc-ns2

![Screenshot 2024-11-21 171224](https://github.com/user-attachments/assets/1ee2303c-16e0-4ca2-a3b1-c4b92f7ca567)




task 7==========

exec into each pod and try to curl the IP address of the service running on the other namespace.
This curl should work.
![Screenshot 2024-11-21 171953](https://github.com/user-attachments/assets/eb807196-5783-49e8-a11b-e557085f78f8)


task 8===============

Now try curling the service name instead of IP. You will notice that you are getting an error and cannot resolve the host.


![Screenshot 2024-11-21 172027](https://github.com/user-attachments/assets/2387608f-edf5-4b10-bf02-e834767794fc)

task 9==================
Now use the FQDN of the service and try to curl again, this should work.
 fully qualified domain name (FQDN):

![Screenshot 2024-11-21 172141](https://github.com/user-attachments/assets/d4763c5a-2cfb-45f3-9029-89896fea38f6)


task 10================

In the end, delete both the namespaces, which should delete the services and deployments underneath them.
![Screenshot 2024-11-21 172246](https://github.com/user-attachments/assets/fa713592-d854-45c7-9e16-7058657df971)





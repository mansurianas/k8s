this is day 13

===========
Task details
Create a pod and try to schedule it manually without the scheduler.
Login to the control plane node and go to the directory of default static pod manifests and try to restart the control plane components
============
smjh nii aaara ye glt horah 

=================


Create 3 pods with the name as pod1, pod2 and pod3 based on the nginx image and use labels as env:test, env:dev and env:prod for each of these pods respectively.
Then using the kubectl commands, filter the pods that have labels dev and prod.

![Screenshot 2024-11-26 131154](https://github.com/user-attachments/assets/a5484fe3-9169-454e-bc8e-1bf069437a6a)
kubectl get pods
You should see the pod1, pod2, and pod3 pods in the output.

for dev and prod 
kubectl get pods -l env=dev

kubectl get pods -l env=prod

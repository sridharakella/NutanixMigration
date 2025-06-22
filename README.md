The first thing we need to do is set up a jump box, and that jump box is going to basically run the NKP software right as well as some other things and as well as become the initial bootstrap mechanism to actually bootstrap the NKP management cluster. And what happens during the bootstrap process is we load CAPI provider for Nutanix on top of that container running in your container runtime. In my case, I use Docker. 
We can also use you could use pod Man or another container runtime.

prerequistes:

Check the Kubectl and Helm installed . PFA atatched screen shot
<img width="682" alt="Screen Shot 2025-06-22 at 1 16 05 PM" src="https://github.com/user-attachments/assets/c0de7756-1e5b-4ca7-9ce4-8f8e5a41c477" />

we should  a registry, in production we have, in local we have local registry, we use harbor Registry
a local registry, right? or a registry that's that's hosted somewhere that you have control over. like  azure container registry, like acr, or it's elastic container registry, ecr with aws, but for an on prem solution, use harbor  so you can see here I have a harbor registry set up this is actually running on my other cluster, US East core for now.

This On prem service registry helps with Air Gap environment as well

Login to Nutanix portal. In Downloads section;
<img width="746" alt="Screen Shot 2025-06-22 at 1 35 40 PM" src="https://github.com/user-attachments/assets/57101e1d-8341-43d1-b67c-749941a3ad07" />
<img width="755" alt="Screen Shot 2025-06-22 at 1 35 52 PM" src="https://github.com/user-attachments/assets/bcb3d578-c521-4900-9ea0-74525591bc8a" />

You can build on you image as well , on ubuntu 22 , Let's if you wanted to support for GPU , we need to build an image on ubuntu22.
Upload the below images to the Prism Central
<img width="744" alt="Screen Shot 2025-06-22 at 1 39 51 PM" src="https://github.com/user-attachments/assets/63ec247b-df06-45f1-8514-d270cfbd20f8" />
Uploading screen shot to the prism central.


<img width="780" alt="Screen Shot 2025-06-22 at 1 46 46 PM" src="https://github.com/user-attachments/assets/0d5ff6ef-312b-4a51-b52a-27fd7f31d80b" />

We have Jump Box and harbor registry 
<img width="769" alt="Screen Shot 2025-06-22 at 1 50 28 PM" src="https://github.com/user-attachments/assets/33ec11e6-739b-4026-83db-377f0739c1c6" />

Once the VM's are ready

nkp create cluster ( gives a view)

<img width="485" alt="Screen Shot 2025-06-22 at 1 53 23 PM" src="https://github.com/user-attachments/assets/68d60c8d-1c6d-4a7b-a545-391e5d030abf" />

Before creating a NKP cluster, we need to create a Project. I created a NKP Project.
Under the Ham burger Menu, select "APP and Market Place"
<img width="777" alt="Screen Shot 2025-06-22 at 1 59 59 PM" src="https://github.com/user-attachments/assets/c0ac294f-9646-4da2-8787-9822a1b5a1d7" />

Then give the following the details( Project details should from the Project name ( NKP) 

<img width="1365" alt="Screen Shot 2025-06-22 at 1 57 30 PM" src="https://github.com/user-attachments/assets/05b38ff5-228b-4a4a-ac7b-a94d75b5d336" />

Create a user role, access , and make sure  we match VLAN details as part of NKP prject creation

<img width="1594" alt="Screen Shot 2025-06-22 at 2 05 11 PM" src="https://github.com/user-attachments/assets/a0019e4f-2189-4487-a148-f5d5fd92eacb" />

We can Use Traefik for Ingress Controller, in this screen shot, I am not giving any details for Ingress controller
For Registry you can use harbor registry details, I have downloaded the authentication cert in my local and pointing the cert location
For SSH , you can use Konvoy, but using the SSH key that I have created using ssh-keygen
<img width="1629" alt="Screen Shot 2025-06-22 at 2 13 40 PM" src="https://github.com/user-attachments/assets/429e5ede-5820-4f67-b940-8dffb0b6ef7f" />

<img width="1663" alt="Screen Shot 2025-06-22 at 2 19 26 PM" src="https://github.com/user-attachments/assets/41991f0a-9919-4494-9938-28721e1080cb" />

Run the following to get the dashboard URL, it going to expose the credentials

<img width="552" alt="Screen Shot 2025-06-22 at 2 25 34 PM" src="https://github.com/user-attachments/assets/6018f0bf-626d-4754-8204-68f5dd111db1" />

If you have Licensing NCI Pro, NCI ultimate, You can spin the clusters

<img width="1663" alt="Screen Shot 2025-06-22 at 2 31 11 PM" src="https://github.com/user-attachments/assets/d2c6ea39-0fdd-4c86-82e9-7df0d33be5f8" />

Global View : Let say you take Workspace , you can add cluster to the workspace. You can assign RBAC policy to the workspace.
Project , down to namesoace

project associated with application. so for exampoke, I want workspace with group of clusters,



<img width="1026" alt="Screen Shot 2025-06-22 at 2 45 33 PM" src="https://github.com/user-attachments/assets/f0c7d0ad-d93f-4834-9e07-dff746eb3a43" />

You Can use OIDC provider, LDAP provider , default is DAX provider for Nutanix

<img width="1265" alt="Screen Shot 2025-06-22 at 2 53 37 PM" src="https://github.com/user-attachments/assets/dd08c1af-d595-4d9c-a0e9-24165a4e1634" />


You can apply the ultimate licsense , we have tools installed as part of it

<img width="1668" alt="Screen Shot 2025-06-22 at 3 27 03 PM" src="https://github.com/user-attachments/assets/e4334a69-d7e5-486a-8842-e990f25bb848" />

<img width="438" alt="Screen Shot 2025-06-22 at 3 26 40 PM" src="https://github.com/user-attachments/assets/a06cab76-829d-4114-978a-fcfa086687c6" />
























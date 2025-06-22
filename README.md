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


















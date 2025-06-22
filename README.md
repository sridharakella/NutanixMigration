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









The first thing we need to do is set up a jump box, and that jump box is going to basically run the NKP software right as well as some other things and as well as become the initial bootstrap mechanism to actually bootstrap the NKP management cluster. And what happens during the bootstrap process is we load CAPI provider for Nutanix on top of that container running in your container runtime. In my case, I use Docker. 
We can also use you could use pod Man or another container runtime.


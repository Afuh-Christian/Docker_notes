# 2 Virtual Machines vs Containers ....  00:06:24


# ................Virtual Machine ...........................................................................................................................................................................
- An abstraction of a machine(physical hardware)
- <Example ... We can have a mac ...on this mac , we can run two virtual machines ....> 
    - One running  <windows > 
    - The other running <linux>
this is done using a tool called <hypervisor>

# Hypervisor 
- A software used to create and manage virtual machines .... 
- Examples ... 
    - <VirtualBox> (crossplatform) 
    - <VMware> (crossplatform)
    - <Hyper-V> (Windows only)

# Benefits of building virtual machines .....00:07:35 
- Run apps in isolation inside a virtual machine

- <One thesame physical machine we can have two virtual machines> 
    - <Each running a completely different application > 
    - <Each app having the exact dependencies it needs >
    - <App1> 
        - <node 14> 
        - <mongo 4> 
    - <App2> 
        - <node 9> 
        - <mongo 3>


               <Physical machine>
<Virtual machineA>                  <Virtual machineB> 
     <app1>                                <app2> 
    <node 15>                             <node 9>
    <mongo 4>                             <mongo 3>  

- Both running on thesame machine but on different isolated environments .... 



# DisAdvantages of VM model.... 
- Each VM needs a full copy of an Operating system that needs to be licensed , patched and monitored .
- Slow to start (because the entire OS has to be loaded)
- Resource intensive .. (<Each VM takes a slice of the actual physical hardware resources like cpu, memory & disk space>)
    - <For 8gb memory , it has to be divided for the different virtual machines present>
    - We can decide how much memory to alocate to each virtual machine , but <there's a limit to the number of VMs you can run on a machine>

























# ...............Container ............................................................................................................................................................................ 
- An isolated environment for running an application . 



# Advantages of Containers over VMs
- Allow running multiple apps in isolation 
- Are lightweight (Don't need a full OS)
- All <containers> use <OS> of the host (Don't need another OS) 
- Start quickly 
- Need less hardware resources (We can run hundreds of containers side by side ..)




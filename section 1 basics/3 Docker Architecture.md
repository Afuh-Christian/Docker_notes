# 3 Docker Architecture     00:09:37      .... 

- It uses a <Client Server> Architecture ...
    - It has a <Client component> that talks to a <Server component> using a <restful api>

- The <Server> (<Docker Engine>) sits on the background and takes care of <building> and <running> docker containers ... 



<Client>  ---<rest api>-->  <Server>
<Client>  ---<rest api>-->  <Docker Engine> 



# A container .
- Is a process(like processes running on your computer) , but it's a special kind of process 

- All <containers> share the <Kernel>(core of the OS) of the host ....

# Kernel 
- Manages applications and hardware resources ..
- Every OS has it's own kernel or engine and these <kernes have different api's> that's why we can't run  a windows app on linux 
    - because the app needs to communicate with the kernel of the underlying system ... 

# Windows 
- Can run <windows containers> and <Linux containers> 
- because windows 10 now has a custom build <linux kernel>
    - In addition to the <windows kernel> that has always been in windows ...
    - So we can run <linux apps> natively on windows ... 

# Linux 
- Can run <Linux containers> 

# Mac 
- Has it's own kernel different from linux and windows 
- This <kernel does not have native support for containers apps>
- <Docker on mac> uses a lightwieght <Linux VM>  to run linux containers 



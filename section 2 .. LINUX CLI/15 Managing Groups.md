# 15 Managing Groups    01:22:58  ...

- like user , we have similar commands for managing groups .
> groupadd 
> groupmod 
> groupdel 

- we use groups so that users in thesame group have thesame kind of permission 



# ........create a new group ... 
> groupadd <groupname>
> groupadd developers

- group found <in  /etc/group>

> cat /etc/group

developers:x:1001:

1001 = id of group


# Add a user to this group ..... 
- add john to this group ... 

> usermod
  -g, --gid GROUP               force use GROUP as <new 'primary group
  -G, --groups GROUPS           new list <of 'supplementary GROUPS


# GROUPS ... IN LINUX .. 
- Every linux user <has 1 'primary groups and 0 or more 'supplementary groups> 

# why are these groups separated .... 
- E.g Say John is  part of <5 groups> and now he want's to create a new file 
    - <Every 'file is owned by 'one-user__&__one-group > 

# Question , if john is part of 5 groups , which group should be used for owning that new file that john is going to create ? 
- This is why we need <a 'primary group>
- <A 'primary group is auto created when we create a 'new-user , (It's the group with thesame name as the user)>


- User group as  supplementary group and add john to it 


> usermod -G <groupname> <username>
> usermod -G developers john


- <check johns user info> 

> cat /etc/passwd 

- <to see only the record for john(user)> 
- we pipe and use <grep> to search for john 
> cat /etc/passwd | grep john 
# OR .. 
- search for john directly ... 
> grep john /etc/passwd

# Ouput .. 
john:x:1000:1000::/home/john:/bin/bash


<username>:x:<userID>:<primarygroupID>::/home ...:/bin...





# How to see the Groups of a user ...... 

> groups <username> 
e.g 
> groups john 

# Output 
john : john developers

# Ouput explained
<username> : <primarygroup-group> <suplementary-group>









# We can add john to more suplementary groups .... 

#  Json and yml or yaml formats        03:08:29.914

- Add new file in root project .. 

# data.json
- we use {} to represent heirachy 
- we use double qoutes
- use (,) to separate key value pairs


# data.json
{
    "name":"The Ultimate Docker Course" , 
    "price":149 , 
    "is_published":true, 
    "tags": ["sofware","devops"] , 
    "author":{
        "first_name":"Afuh", 
        "last_name":"Hamedani"
    }
}













# yaml 
(---) indicates the begining of a yaml file
- use indentation to represent heirachy 
- No quotes
- User (-) to represent a list or an array
- Easier to read

# data.yml
---
name:The Ultimate Docker Course , 
price:149 , 
is_published:true, 
tags: 
  - sofware,
  - devops , 
author:
  first_name:Afuh, 
  last_name:Hamedani
# 






# NB ... <a 'Parsing 'yaml files is abit slow than 'Parsing 'json files  because the parser can't tell the different primitive data types in a 'yaml file >


# So  .... 

# yaml  
- for configuration files 

# json 
- for sharing data with multiple computers like a client and a server 
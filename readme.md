README

This is the documentation of Ansible Playbook step by step.

1. Create a yml file "exampleapp.yml"

--- 
- name : Deploy exampleapi
  host : api    #group
  task : 
       - name : Copy artifact
	 copy : 
	    src : ~/example.jar
            dest : .


2. Run the playbook 

ansible -playbook -i hosts -u user exampleapp.yml

#hosts file contains command lines and user = current username
#task = copy artifact


3. Remove app "removeapp.yml"
#we can create a book, specially to remove the app

---
- name : Remove exampleapi
  host : api
  tasks : 
        - name : Remove
          file :
	     path : example.jar
	     state : absent


4. Run the playbook 

ansible -playbook -i hosts -u user removeapp.yml

5. For a better reading, put the variable at the book's root in a directory and replace in the yml file 
datas who are suceptible to change at the different run

example : path "{{appli_dir}}"
          owner : "{{owner_user}}"
          group : "{{owner_group}}"

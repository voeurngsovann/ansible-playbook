# ansible-playbooks

this is the ansible playbook for install or upgrade the lasted version of oracle Autonomous Health Framework
logic is that 
1.if it detect the target servers are not yet have oracle AHF then it will install with the lasted version
2.if it detect the target servers are install older version than variable mention it will upgrade to the lasted version
3. Need passwordless as root user from ansible to targetservers which mention in hostsfile 
4. you can set root passwordless from ansible server to target servers with this followed command 

  ansible all -i hosts -k -u root -m authorized_key -a "user=root state=present key=\"{{ lookup('file','/home/ansible/.ssh/id_rsa.pub') }}\""
5.For oracle RAC enviroment install only firstnode it will automatic install in the second nodes unless root passwordless set in oracle rac enviroment


# Date : 27 Dec 2024  
# Note : Before deploy this playbook in production enviroment make sure you are testing in your labs enviroment first  

command run 

# ansible-playbook -i hosts installahf.yml

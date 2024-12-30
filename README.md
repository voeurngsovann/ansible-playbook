# Ansible-playbooks-install&upgrade oracle Autonomous Health Framework
# Autonomous Health Framework can download from below document ID
  	Autonomous Health Framework (AHF) - Including Trace File Analyzer and Orachk/Exachk (Doc ID 2550798.1)
# this is the ansible playbook for install or upgrade the lasted version of oracle Autonomous Health Framework
    Logic  of this playbook
    - software oracle AHF should be downloaded and input in /installer/software or you can put whereever but in ansible playbook you need to change location accordingly 
    - if it detect the target servers are not yet have oracle AHF then it will install with the lasted version  
    - if it detect the target servers are install older version than variable mention it will upgrade to the lasted version
    -  Need passwordless as root user from ansible to targetservers which mention in hostsfile 
    -  you can set root passwordless from ansible server to target servers with this followed command 
# Configure root passwordless between Ansible servers into target hosts
    ansible all -i hosts -k -u root -m authorized_key -a "user=root state=present key=\"{{ lookup('file','/home/ansible/.ssh/id_rsa.pub') }}\""
# For oracle RAC enviroment install only firstnode it will automatic install in the second nodes unless root passwordless set in oracle rac enviroment


# Note : Before deploy this playbook in production enviroment make sure you are testing in your labs enviroment first  
  Check on file
  
    -  cat ansible.cfg
    
        [defaults]
        interpreter_python = auto_legacy_silent
        command_warnings=False
        remote_user = root
        become = True
        host_key_checking = False

        
    # ansible-playbook -i hosts installahf.yml

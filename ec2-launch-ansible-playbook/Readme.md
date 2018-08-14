***** Guidelines to launch EC2 instance using Ansible-Playbook. *****

Step-1: Setup required environment that supports to launch EC2 Instance using Ansible.
 
        1. Python boto library:
                $ sudo pip install --upgrade pip
                $ sudo pip install boto

        2. Ansible:
                $ sudo yum install ansible

        3. Set up the AWS access and secret keys in the environment settings (best is inside the ~./boto):
                We can acheive this in two ways...

                Path-I: Storing the "access-key_id" and "secret_access-key" into boto file.
                        # touch ~/.boto
                        # vim ~/.boto
                        [Credentials]
                        aws_access_key_id = <aws_access_key_id>
                        aws_secret_access_key = <aws_secret_access_key>

                Path-II: Create Environment Variables using "access-key_id" and "secret_access-key".
                        export AWS_ACCESS_KEY_ID=<aws_access_key_id>
                        export AWS_SECRET_ACCESS_KEY=<aws_secret_access_key>
      
Step-2: Execute command to run Ansible-Palybook to launch EC2 Instance using Ansible.

        $ ansible-playbook site.yml -i hosts
        
        
        Thank you...!
      


***** Guidelines to install softwares with Ansible *****

Step-1: To install softwares with Ansible, we have to setup the environment to access the EC2 Instances:

        1. In an “inventory” file, list all the nodes we are going to manage.

                [webserver]
                52.90.220.129
                52.90.220.130

        2. Ansible allows you to ‘become’ another user, different from the user that logged into the machine (remote user). 
           Each allows you to set an option per group and/or host, these are normally defined in inventory but can be used as normal variables.
           
                [webserver:vars]
                ansible_become=true
                ansible_user='ubuntu'
                ansible_become_method='sudo'
                ansible_become_user='root'


        3. Test the setup, whether remote macines are reachable or not.
                $ ansible-playbook webserver -m ping -i hosts
                52.90.220.129 | SUCCESS => {
                "changed": false, 
                "ping": "pong"
                }
                52.90.220.130 | SUCCESS => {
                "changed": false, 
                "ping": "pong"
                }

        * Python sould be installed in the node machines.
        ** Ref: https://www.webagesolutions.com/knowledgebase/kb024/kb024-install-sw-ansible/


Step-2: Install JDK-1.8 using Ansible
















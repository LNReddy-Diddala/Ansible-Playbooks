***** Guide lines to launch EC2 instance using Ansible-Playbook. *****

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
      

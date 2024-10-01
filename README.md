## Launch, Stop, Start, and then Terminate an EC2 instance

1. Launch an ubuntu EC2 instance where you are going to install ansible
    - Name this instance as "master-node"
    - Install steps for ansible (derived from official ansible documentation) <br>
        -- *sudo apt update* <br>
        -- *sudo apt install software-properties-common* <br>
        -- *sudo add-apt-repository --yes --update ppa:ansible/ansible* <br>
        -- *sudo apt install ansible* <br>
        -- *ansible --version* <br>
   
2. Create an IAM Role with EC2 full access, and attach this role to EC2 instance "master-node"
    - Go to **IAM > Roles > Create Role**
    - Select **"Trusted Entity Type: AWS Service"; "Use Case: EC2"** and click **Next**
    - Select **"Permission Policies: AmazonEC2FullAcess"** and click **Next**
    - Give Role Name: **"ansible-role"** and click **Create Role**
    - Now go to your EC2 instance **"master-node"** and select **Actions > Security > Modify IAM Role**
    - From the dropdown, select **"ansible-role"** and click **Update IAM Role**

3. Create 3 playbook files
    - **launch.yml**: To launch an EC2 instance
    - **stop.yml**: To stop an EC2 instance
    - **start.yml**: To start an EC2 instance
    - **terminate.yml**: To terminate an EC2 instance

4. Run following commands
    - To verify syntax of the playbooks
        *ansible-playbook --syntax-check <playbook-file>*
    - To do a dry run of the playbooks
        *ansible-playbok -C <playbook-file>*
    - To run the pplaybooks
        *ansible-playbook <playbook-file>*

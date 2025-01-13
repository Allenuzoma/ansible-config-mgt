

# ANSIBLE-CONFIGURATION-MANAGEMENT

   

   
## Step 1 - Install and Configure Ansible on EC2 Instance

 - First we will rename our initial Jenkins AWS instance to Jenkins-Ansible. We will use this server for all our ansible operations and also to run our playbooks.

   - ![ansible server details](https://github.com/user-attachments/assets/7e5754b8-e233-4276-a909-9ae7afcfeef9)


   - Now we will install ansible on this insatance

```sh
sudo apt update
sudo apt install ansible
ansible --version

```

- ![ansible version](https://github.com/user-attachments/assets/c4f47b45-3145-4274-831d-06bf882baa2c)

## Step 2 - Configure Jenkins build job to archive your repository content 

   - Create a repository on github named `ansible-config-mgt`
   - We will configure our jenkin build to be able to archive contents of our repository content `ansible-config-mgt`.
   - Create a new Freestyle project ansible in Jenkins and point it to your 'ansible-config-mgt' repository.
   - Configure a webhook in GitHub and set the webhook totrigger ansible build.
   - Configure a Post-build job to save all (**) files, like you did it in Project
   - Test your setup by making some change in README.md file in the main branch and make sure that builds starts automatically andJenkins saves the files (build artifacts) in the       
     following folder
```sh

ls /var/lib/jenkins/jobs/ansible/builds/<build_number>/archive/

```
Note: Trigger Jenkins project execution only for main (or master) branch.
Now your setup will look like this:
Tip: Every time you stop/start your Jenkins-Ansible server - you have to
reconfigure GitHub webhook to a new IP address, in order to avoid it, it
makes sense to allocate an Elastic IP to your Jenkins-Ansible server (you
have done it before to your LB server in Project 10). Note that Elastic IP is
free only when it is being allocated to an EC2 Instance, so do not forget to
release Elastic IP once you terminate your EC2 Instance.
Step 2 - Prepare your development environment using Visual
Studio Code
1. First part of 'DevOps' is 'Dev', which means you will require to write
some codes and you shall have proper tools that will make your
coding and debugging comfortable - you need an Integrated
development environment (IDE) or Source-code Editor. There is a
plethora of different IDEs and source-code Editors for different
languages with their own advantages and drawbacks, you can choose
whichever you are comfortable with, but we recommend one free and
universal editor that will fully satisfy your needs - Visual Studio Code
(VSC), you can get it here.
2. After you have successfully installed VSC, configure it to connect to
your newly created GitHub repository.
3. Clone down your ansible-config-mgt repo to your Jenkins-Ansible
instance
git clone <ansible-config-mgt repo link>
 Previous Lesson B

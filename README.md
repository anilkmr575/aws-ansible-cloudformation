#Ansible - AWS CloudFormation
This repo contains Ansible code and AWS CloudFormation templates for the provisioning of AWS resources.

#Steps to work on (see Jenkins file)
Requirements

    Install Ansible.
    Set-up Ansible for authenticating with AWS.

Register domain name

    Register a domain name using AWS Route 53.
    Create a public hosted zone for the domain.
    Uncomment hosted_zone_public_name in group_vars/site/main.yml and insert the public hosted zone domain name.

HTTPS

    Create a certificate for *.hosted_zone_public_name (i.e., name inserted for hosted_zone_public_name in the previous step).
    Uncomment ssl_certificate_id in group_vars/site/main.yml and insert the certificate ARN.

Key name

    Uncomment key_name in group_vars/site/main.yml and insert the name of the EC2 key pair that you want to use to connect to the EC2 instances.

Provision network and site

git clone git@github.com:bendbennett/ansible-aws.git
cd ansible-aws/cloud-formation
ansible-playbook basic-network.yml
ansible-playbook site.yml 

Remove network and site

cd ansible-aws/cloud-formation
ansible-playbook site-down.yml
ansible-playbook basic-network-down.yml

Network

First to deploy network use vpc.yml.

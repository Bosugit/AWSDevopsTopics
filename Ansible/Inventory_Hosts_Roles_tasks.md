/*
Topic:   Ansible Project Structure: A Beginner's Guide to Inventory, Hosts, Roles, and Tasks - Part 3
URL:     https://www.youtube.com/watch?v=qsqpcvzLwf4

github: https://github.com/rahulwagh/ansible-examples

*/



Roles: Roles are a way to organize playbooks and other files in a structured way. A role represents a specific function or a set of tasks, such as installing a specific software package or configuring a service.

2. Hosts: Hosts are the systems that Ansible will manage. The hosts can be specified in an inventory file, which is a plain text file that lists the hostnames or IP addresses of the systems that Ansible should manage.

3. Tasks: Tasks are the individual actions that Ansible will perform on the hosts. Tasks are defined in playbooks, which are written in YAML and specify the order in which tasks should be executed.

4. Inventory file: The inventory file is a plain text file that lists the hostnames or IP addresses of the systems that Ansible should manage. The inventory file can also be used to specify additional information about the hosts, such as the user to connect as or the location of the private key to use for SSH connections.
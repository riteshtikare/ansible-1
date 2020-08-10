# Configuring Parallelism
  Configure parallelism in Ansible using forksAnsible allows much more control over the execution of the playbook by 
  running the tasks in parallel on all hosts. By default, Ansible only fork up to five times, so it will run a particular
  task on five different machines at once. This value is set in the Ansible configuration file ansible.cfg.
  .

    [student@crux~]$ grep forks /etc/ansible/ansible.cfg
    #forks          =  5
.

    • Ruuning tasks in parallel will make Ansible faster
    • Ansible can run tasks in parallel on all hosts
    • By default, tasks can run on 5 hosts at once
    • set forsk = nn in /etc/ansible/ansible.cfg to increase this number
    • Alternetively, use the --forks options with the ansible-playbook or ansible command
    • Use the serial keyword in a playbook to reduce the number of parallel tasks to a value that is lower than what is 
     specified with the forks option. 

# Rolling updates
If there is a website being deployed on 100 web servers, only 10 of them should be updatedat the same time.
The serial key can be set to 10 in the playbook to reduce the number ofsimultaneous deployments (assuming that
the fork key was set to something higher). The serial keyword can also be specified as a percentage which will be
applied to the total numberof hosts in the play. If the number of hosts does not divide equally into the number 
of passes, the final pass will contain the modulus. Regardless of the percentage, the number of hosts per passwill
always be 1 or greater.
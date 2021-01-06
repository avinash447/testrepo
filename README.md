# testrepo
tesetrepo
---
- name: insert line into a file
  hosts: vy-test
  tasks:
    - name: line insert
      lineinfile:
        dest: /etc/nagios/commands.cfg
        line: command[check_net_rxtxdrop_eth0]='/usr/local/nagios/libexec/check_net_rxtxdrop eth0' 
    - name: Restart service  nrpe
      service:
        name: nrpe
        state: restarted
      become: yes

####################
---

- name: run yum update on RHEL servers
  hosts: all
  gather_facts: yes
  strategy: free
  vars:
    patch: true
    eengine: true
    required_packages:
      - jre-8u162-linux-x64.rpm

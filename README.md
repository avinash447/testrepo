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

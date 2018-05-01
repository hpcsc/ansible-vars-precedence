# Ansible Vars Precedence

A sample playbook to demonstrate variables precendence in Ansible

To run:

```
ansible-playbook -i hosts -v precedence.yml -e "var1='from -e'"
```

The playbook includes a sample role and defines variables at multiple levels:

- role defaults (`./roles/sample-role/defaults/main.yml`): define 6 variables from var1 to var6, lowest precedence
- `group_vars` (`./group_vars`): define 5 variables from var1 to var5
- `host_vars` (`./host_vars`): define 4 variables from var1 to var4
- vars in playbook (`./precedence.yml`): define 3 variables from var1 to var3
- vars in role (`./roles/sample-role/vars/main.yml`): define 2 variables from var1 to var2
- `-e` switch (passed in when running `ansible-playbook` command): define var1, highest precedence

The output of running the playbook confirms the variables precendence (.i.e. vars defined at higher precedence places will overwrite lower precendence variables with the same name)


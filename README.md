# Installing MySQL with Ansible
This `ansible` playbook will install MySQL . Make sure you did all steps and then run playbook.  This playbook compatible with Centos/7

## Create digital-Ocean droplet with a token 
1. Create  a token from digital Ocean [Craete token ](https://www.digitalocean.com/docs/api/create-personal-access-token/)
2. Create ssh-key and copy full path 
3. Then run following commands 

```
git clone https://github.com/farkhodsadykov/MySQL-Ansible.git
cd MySQL-Ansible 
sh run_script.sh
ansible-playbook -u root -i hosts install-mysql.yml
ssh root@seversip 
mysql -u root -p Redhat2018
```

4. If everything works you don't have to do other steps.



## Step 1 Cloning repository and creating ssh-key
```
git clone https://github.com/farkhodsadykov/MySQL-Ansible.git
cd MySQL-Ansible 
sed 's/104.248.61.147/yourserversip/g'  -i hosts
ssh-keygen <Follow steps>
```

## Step 2 Coping ssh-key to remote system 
If you are using `ansible` user make sure `ansible` user is in `visudo` file.  If you don't know `visudo` please follow this step [Add user to visudo](https://stackoverflow.com/questions/37333305/ansible-create-a-user-with-sudo-privileges/52173639#52173639)

``` 
ssh-copy-id root/ansible@yourserversip
ansible all -u root/ansible -i hosts 
```

## Step 3 run the playbook 
```
ansible-playbook -u root/ansible -i hosts install-mysql.yml 
ssh root@yourserversip
mysql -u root -p <Redhat2018>
```

If you would like to change the password for MySQL,  go to `install-mysql.yml` change variable `new_passwd` to your new password. 😉 
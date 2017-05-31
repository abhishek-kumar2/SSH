# SSH - Secure Shell 
* A Cryptographic Network Protocall, we use it over an unsecure network for network services. In other words we can say SSH helps to get a secure channel over an unsecured network.
* SSH uses public-key cryptography to authenticate in a client-server architecture, connecting an SSH client application with an SSH server.


###### How to install SSH server for Ubuntu?
> $ sudo apt install openssh-server -y

After installation completed. Make a copy of SSH config file and change file permission
```
the config path may be '/etc/ssh/sshd_config'
```
* Copy command 
> $ sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.factory-define
* File permission change command *
> $ sudo chmod a-w /etc/ssh/sshd_config.factory-define

* Open the config file and uncomment and set as per use, like enable port 22, host 0.0.0.0, hostkey etc. Once edit done you need to restart ssh.
* For Ubuntu 14.04 
> $ sudo restart ssh
* For Ubuntu 15.04 + 
> $ sudo systemctl restart ssh


###### How to generate a ssh key?
* Create a shh hidden folder in your home directory 
> $ mkdir ~/.ssh
* Give the owner permission only 
> $ chmod 700 ~/.ssh
* Now run the keygen command to genertate the file 
> $ ssh-keygen -t rsa
```
This command will ask you file name with path default will 'id_rsa'.
Then it will ask you passphrase twice. Good to provide.
```

* Now your machin is ready to connect over on internet securly using SSH with command.
> $ ssh \<user name\>@\<ip or host\>
* Then it will prompt you for password 


###### SFTP Secure file transfer protocall

* Similar like ssh it is provide a secure file transfering session between client to server.
> $ sftp \<user name\>@\<ip or host\>

* To put your file to server 
> $ put \<file name\>

* To get file(s) from server to client 
> $ get \<file name\>


###### How to git clone with ssh on private git repository?

* First copy your ssh key or certificate and pest to the git reposiroty site.
> cat ~/.ssh/id_rsa.pub | clip

* Now clone the new repository in your local.
> ssh-agent bash -c 'ssh-add ~/.ssh/id_rsa; git clone \<git@git.ssh.url.git\>'

* After mead your changes and addition of files and commite. To push your changes use.
> git push -v origin master

* If you get some error key not found need to turn on shh agent.
> $ eval \`ssh-agent -s\`

* If you using multipe keys need to remove and add required one.
> $ ssh-add -D 

* To list added one use
> $ ssh-add -l

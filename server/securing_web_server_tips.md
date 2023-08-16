1. Create a new user as follows:
> adduser newUserName
> passwd passwordNewUseName

2. Disable root remote login: prevent anyone from logingas root user.
> vim /etc/ssh/config then update
> PermitRootlogin to no then reload ssh
> system reload sshd.

3. Add a public-key Auth:
> Generate a Key Pair => ssh-keygen 
> Copy the Public Key

Automatic Install.
  > Use ssh-copy-id : sshcopy-id userName@server\_ip\_add.

Manually install the Key
  > or cat ~/.ssh/id\_rsa.pub then add it to new remote user 
  > switch to the new user: su - newUser
  > then create a .ssh folder: mkdir .ssh
  > restritct its permissions: chmod 700 .ssh
  > then paste public key: vim .ssh/authorized\_keys
  > last not least, restrict the persmission of the authorized\_keys file: chmod 600 .ssh/authorized\_keys.


4. Configure a basic firewall:
> CentOs ships with a basic firwarll-cmd enables us to config the firewall policies as follows:
 4.1. start the firewall : systemctl start firewalld.
 4.2. To enable ssh daemon: sudo firewalld-cmd -permanent -add -service=ssh
 4.3 enable https/http service: firewall-cmd --permanent --add -service=htpps/http
 4.3 See additional seervices thay you can enable: firewall-cmd -get-services
 4.4. list all the exceptions implemented: firewall-cmd -permanent -list\_all
 4.5. implement all the changes made: firewall-cmd reload
 4.6. start the firewall: sudo systemctl enable firwalld.
 
 5. Disable login by Password. secure your server from brute-force with disabling login by password as follow:
 > open ssh config file : vim /etc/ssh/sshd\_configj
 > challengResponseAuthenticate no
 > PasswordAutho no
 > UsePAM no 
> PermitRootLogin no then restart ssh system reload sshd.

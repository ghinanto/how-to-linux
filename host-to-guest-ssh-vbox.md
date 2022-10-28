# Connect over SSH from your computer to arch running on Virtualbox
Loading arch iso on vbox you get root prompt. Set a password:
```
$ passwd
```
Now:
```
$ vim /etc/ssh/sshd_config
```
and uncomment the line:
```
PasswordAuthentication yes
```
Verify that connection is working connecting to localhost from inside the vbox:
```
$ ssh root@127.0.0.1
```
If not try restarting sshd.
When it works it's time to port forward.
Go to network settings on VirtualBox. Check that type connection is on NAT.
Click Advanced settings and Port Forwarding.
Now set a rule like this:
Protocol: TCP
Host IP: 127.0.0.1
Host port: 8022
Guest IP: 10.0.2.15 (or whatever address is shown running 'ip addr' from inside the vbox)
Guest port: 22 (default port)

So now YOU, from the host machine, can connect over ssh to the port 8022 of localhost and get access to the vbox. Whoever else want to connect to the vbox must connect to the port 8022 of YOUR ip address.
So you can enter the vbox running:
```
$ ssh root@127.0.0.1 -p 8022
```



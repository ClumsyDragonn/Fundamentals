# SSH In Docker

`Disclaimer :` <br> `this documentation is for docker terminal in linux`

1. start the container (make sure it was the operating system for server)

2. Check the IP Address : 
```bash
# if you're in the outside of container
docker inspect -f '{{json .NetworkSettings.Networks}}' <container-name>

# if you're in the container
hostname -I
```
<br>

3. configure the container access using root system :
```bash
docker exec -it <container-name> bash
```
<br>

4. create the user in the environment
<br>
<br>

5. install the sshd in the environmet :
```bash
install openssh-server
```
<br>

6. run this path :

```bash
/usr/sbin/sshd
```
<br>

7. go to your terminal (the outside of container) to using the ssh

```bash
ssh <username>@<IP Address>

#example
ssh rusdi@172.17.0.2
```
<br>
---
### kalau sudah pernah install sshd sebelumnya ?

tinggal jalankan :<br>`sudo systemctl start sshd`<br>`sudo system enable sshd`  

---

### Ingin mematikan ? jalankan : `sudo system stop sshd`

---

### What happen if the IP Address is using the different container ?


```bash
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@ @ 
WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@ 
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY! 
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that a host key has just been changed. The fingerprint for the ED25519 key sent by the remote host is SHA256:HZZsaAost3aK1Oatg18cy4h3tg5vlmxpKtyUDlRp4cQ. Please contact your system administrator.
Add correct host key in /home/rabkacozzy/.ssh/known_hosts to get rid of this message. Offending ED25519 key in /home/rabkacozzy/.ssh/known_hosts:4 Host key for <IP Address> has changed and you have requested strict checking. Host key verification failed.
```
if this happened, just run this command in the outside container environment : 

```bash
ssh-keygen -R <IP Address>
```
it reset the host key and you can use ssh normally again.

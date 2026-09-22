# Samba

## what is samba ?

Samba is a free, open-source software suite that allows Linux and Unix systems to share files and printers with Windows computers.

<br>

- create user in samba (condition : in the pointed device) :

```bash
sudo smbpasswd -a <username>
```

<br>

- deleting the user in samba : 

```
sudo smbpasswd -x <username>
```

<br>

- you can login samba from any device with this command :
```bash
smbclient //<IP Address>/Shared -U <samba-user>
```
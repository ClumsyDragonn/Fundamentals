# LINUX GUIDE - Permission

### 1.1 User create
```bash
useradd -m -s /bin/bash <username>
```
<br>
<b>Jangan lupa untuk memberi password-nya setelah user dibuat 
passwd (name) </b> 

<br>

```bash
passwd <username>
```


---
### 1.2 User Information
`id (username)` --> cek informasi user & klasifikasi group tergabung (kalau ada)

`pwd` --> cek current directory

`whoami` --> cek current identity

---



### 2.1 Checking Permission
`ls -l /` --> menampilkan 3 jenis klasifikasi akses (User (yang sebagai owner file/folder), Group, Other) pada root folder

`rwxrwxrwx`<br>


`r = read -> 4`

`w = write -> 2`

`x = execute -> 1`




```
chmod 770 <Directoy / File Name>
```

kombinasi akses di atas berdasarkan klasifikasi : 

##### User / owner = rwx (ada semua akses)
##### group = rwx / (ada semua akses)
##### Other = --- / (ga ada akses)
---



### 2.2 Modifying Permission
```
chmod (User owner Access + Group access + Other access) <Directory / File Name>
```
### contoh :

```
chmod 640 <Directoy / File Name>
```

- 6 -> 4 (read) + 2 (write) <br> artinya home user punya akses baca dan tulis 

- 4 -> 4 (read) <br> artinya group punya home akses baca saja.

- 0 -> no one access <br> artinya selain home user dan group, tidak ada akses.


---
### 2.3 Moving the owner of Directory / File.

```
chown <username> <Directory / FIle Name>
```




### 3.1 Making group
```
groupadd <Group name>
```

### 3.2 Adding user to the group
```
usermod -aG <Group name> <username>
```

### 3.3 checking user group

```
groups <username>
```
atau :

```
id <username> (bisa dicek di sini)
```

### 3.4 giving the Directoy / File ownership for specified group only 
```
chgrp <existed group name> <file / directory name>
```
 ---

 ### 4.1 Adding more than one group to the file & directory

 jika ingin memberikan akses lebih dari satu group, maka kita gunakan ACL (Access Control List)

 ```bash
 # jalankan ini
 which getfacl
 which setfacl
 ```

 kalau muncul : 
 ```
 /usr/bin/getfacl
 /usr/bin/setfacl
 ```

artinya sudah terinstall, tetapi kalau :
```
... : command not found
```
install dulu package-nya dengan nama package : 
`
acl
`
### 4.2 Giving access using ACL

ACL digunakan ketika kondisi dimana kita ingin memberikan akses lebih dari satu group

ada dua tipe akses, yaitu akses file dan akses direktori. 

<br>

- Akses file dengan ACL : 
```bash
# Enable access to read and write file
setfacl -m g:(group name):rw (file name)


#below was alternative options :

# Enable access to read (r) and execute (x) 
setfacl -m g:(group name):rx (file name) 

# Enable access to write (w) and execute (x)
setfacl -m g:(group name):wx (file name)

# Enable access to write (w) only
setfacl -m g:(group name):w (file name)

# Enable access to read (r) only
setfacl -m g:(group name):r (file name)

# Enable access to execute (x) only
setfacl -m g:(group name):x (file name)
```
<br>

- Akses folder / directory dengan ACL :
```bash

# NOTE ! : 
# the execute (x) access is necessary !
# if the x is unactived, 
# you can't doing anything to the folder 
# (unless you're using the root access)

#Enable access read (r) to the folder
setfacl -m g:(group name):rx (folder name)

#below was alternative options : 

# Enable access write (w) to the folder
setfacl -m g:(group name):wx (folder name)

# Enable all access to the folder 
setfacl -m g:(group name):rwx (folder name)

# Enable execute access only to the folder
setfacl -m g:(group name):x (folder name)

#add the -d for set the default access where you make a new group, all user, or other like guess.

#----------- bonus

#in samba --> mask access
setfacl -m m::rwx (filename)
```
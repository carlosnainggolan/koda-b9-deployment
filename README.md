#Deployment practice with linux

### 1. Initial SetUp
Create User:
```bash
useradd -m -s /usr/bin/bash koda
useradd -m -s /usr/bin/bash dako
```

Create Group:
```bash
groupadd -g 1234 -U koda,dako devteam
```

Project Directory:
```bash
mkdir projectX
```
  
### 2. Make koda the owner and devteam the groupowner in srv/projectX
```bash
chown koda:devteam projectX
```

### 3. Restricting accces 
Ensure that: 
Owner: full access
Group: read $ execute
Others: no access
Using numeric mode 
```bash
cd projectX
chmod 750 .
```

### 4. Create the Structure by koda
```bash
su koda
touch README.md
mkdir src
cd src
touch app.sh

cd ..
mkdir data
cd data
touch input.txt
```

### 5. Fixing Permission for app.sh
Executable for user and owner
```bash
chmod u+X,g+x app.sh
```
No executable for other
```bash
chmod o-x app.sh
```

### 6. Permission for input.txt
Owner can read and write
```bash
chmod u+r,u+w input.txt
```
No one else has any access
```bash
chmod g=---,o=--- input.txt
```

### 7. Allow group collaboration
```bash
chmod koda:devteam -R src
chmod g=rwx -R src
```


### 8. Change ownership in projectX recursively
```bash
chown -R koda:devteam projectX
```

### 9. Permissien
FIle inside the projectX can delete only devteam member
```bash
chmod -R o=r-- projectX
```
Member of devteam can still delete

### 10. README.md (mod numeric)
should be:
1. Readable for everybody
2. Can write only by owner
3. No one can execute
```bash
chmod 644 README.md
```

### 11.  Change owner to dako to all file
```bash
chown -R dako projectX
```

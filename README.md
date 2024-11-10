# Linux-File-IO-Systems-locking
Ex07-Linux File-IO Systems-locking
# AIM:
To Write a C program that illustrates files copying and locking

# DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2:

Write the C Program using Linux IO Systems locking

### Step 3:

Execute the C Program for the desired output. 

# PROGRAM:

## 1.To Write a C program that illustrates files copying 

```
#include<stdio.h>
#include<sys/stat.h>
#include<fcntl.h>
int main()
{
char block[1024];
int in,out;
int nread;
in=open("filecopy.c",O_RDONLY);
out=open("file.out",O_WRONLY|O_CREAT,S_IRUSR|S_IWUSR);
while((nread=read(in,block,sizeof(block))) > 0)
write(out,block,nread);
exit(0);
}
```
## OUTPUT
![Screenshot from 2024-10-17 10-12-52](https://github.com/user-attachments/assets/c03e2c8e-784f-41ad-b722-6a7143764813)
![Screenshot from 2024-10-17 10-45-40](https://github.com/user-attachments/assets/9cac2ae5-db49-40ad-8fd7-7641601acac4)




## 2.To Write a C program that illustrates files locking

```
#include<fcntl.h>
#include<stdio.h>
#include<string.h>
#include<unistd.h>
#include<sys/file.h>
int main(int argc,char* argv[])
{
char* file=argv[1];
int fd;
struct flock lock;
printf("opening %s\n",file);
fd=open(file,O_WRONLY);
if(flock(fd,LOCK_SH)==-1)
{
printf("error");
}
else
{
printf("Acquiring shared lock using flock");
}
getchar();
if(flock(fd,LOCK_EX|LOCK_NB)==-1)
{
printf("error");
}
else
{
printf("Acquiring exclusive lock using flock");
}
getchar();
if(flock(fd,LOCK_UN)==-1)
{
printf("error");
}
else
{
printf("unlocking");
}
getchar();
close(fd);
return 0;
}
```


## OUTPUT

![Screenshot from 2024-10-17 11-50-57](https://github.com/user-attachments/assets/5d5deeea-7495-4083-8cb9-253519bca061)

![Screenshot from 2024-10-17 11-51-09](https://github.com/user-attachments/assets/fc906c8f-540c-4e92-a66c-df70dbcc8838)



# RESULT:
The programs are executed successfully.

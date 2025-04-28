# Linux-Process-API-fork-wait-exec-
Ex02-Linux Process API-fork(), wait(), exec()
# Ex02-OS-Linux-Process API - fork(), wait(), exec()
Operating systems Lab exercise


# AIM:
To write C Program that uses Linux Process API - fork(), wait(), exec()

# DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2:

Write the C Program using Linux Process API - fork(), wait(), exec()

### Step 3:

Test the C Program for the desired output. 

# PROGRAM:

## C Program to print process ID and parent Process ID using Linux API system calls
```
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>

int main() {
    int pid = fork();

    if (pid == 0) { 
        printf("I am child, my PID is %d\n", getpid()); 
        printf("My parent PID is: %d\n", getppid()); 
        sleep(2);  // Keep child alive for verification
    } else { 
        printf("I am parent, my PID is %d\n", getpid()); 
        wait(NULL); 
    }

```


















##OUTPUT


![image](https://github.com/user-attachments/assets/15d13b94-d823-487e-99c7-4b08556f281e)

![image](https://github.com/user-attachments/assets/643c8364-7ed4-4c54-9000-bf6ed8b25da5)
![image](https://github.com/user-attachments/assets/e646f7a6-2e97-4d72-884b-7cdb25b96958)

### RESULT:
Thus the program to implement the creation of a process using fork() API is written and verified using C programming.











## C Program to create new process using Linux API system calls fork() and exit()




```c
~~~c
#include <stdlib.h>
#include <sys/wait.h>
#include <sys/types.h>
int main()
{       int status;
        printf("Running ps with execlp\n");
        execl("ps", "ps", "ax", NULL);
        wait(&status);
        if (WIFEXITED(status))
                printf("child exited with status of %d\n", WEXITSTATUS(status));
        else
                puts("child did not exit successfully\n");
        printf("Done.\n");
printf("Running ps with execlp. Now with path specified\n");
        execl("/bin/ps", "ps", "ax", NULL);
        wait(&status);
        if (WIFEXITED(status))
                printf("child exited with status of %d\n", WEXITSTATUS(status));
        else
                puts("child did not exit successfully\n");
        printf("Done.\n");
        exit(0);}

~~~

```








##OUTPUT

![image](https://github.com/user-attachments/assets/281c83d3-abe2-4fc2-ad97-61a8f67759d9)

![image](https://github.com/user-attachments/assets/ed958a7e-aae2-451f-acb2-e8d75200abe2)



### RESULT:
Thus the program to implement the creation of a process using exec() API is written and verified using C programming.



## C Program to execute Linux system commands using Linux API system calls exec() family

~~~c
#include <stdio.h>
#include <stdlib.h>
#include <sys/types.h>
#include <sys/wait.h>
#include <unistd.h>

int main() {
    int status;
    
    printf("Running ps with execl\n");
    if (fork() == 0) {
        execl("ps", "ps", "-f", NULL);
        perror("execl failed");
        exit(1);
    }
    wait(&status);
    
    if (WIFEXITED(status)) {
        printf("Child exited with status: %d\n", WEXITSTATUS(status));
    } else {
        printf("Child did not exit successfully\n");
    }
    
    printf("Running ps with execlp (without full path)\n");
    if (fork() == 0) {
        execlp("ps", "ps", "-f", NULL);
        perror("execlp failed");
        exit(1);
    }
    wait(&status);
    
    if (WIFEXITED(status)) {
        printf("Child exited for execlp with status: %d\n", WEXITSTATUS(status));
    } else {
        printf("Child did not exit successfully\n");
    }
    
    printf("Done.\n");
    return 0;
}

~~~
##OUTPUT

![image](https://github.com/user-attachments/assets/f27e4fc2-c87a-4474-995a-9b297aae4d67)
![image](https://github.com/user-attachments/assets/940e9b69-531a-453b-b339-d30bfa1d07ff)



### RESULT:
Thus the program to implement the creation of a process using exit() , wait() API is written and verified using C programming.















# RESULT:
The programs are executed successfully.

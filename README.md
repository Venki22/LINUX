### Open Image file using command line
- Become root
- yum install ImageMagick -y
- display image-file.png

### SSH
- Default port is 22
- systemctl status sshd
- rpm -qa|grep sshd

### Access Remote Server without Password(SSH-Keys)
- Generate the key
- By default keys will be store in root/.ssh/id_rsa 
- ssh-keygen
- Copy the key to the server
- ssh-copy-id root@192.178.2.3
- first time it will ask password
- Login from client to server
- ssh root@192.178.2.3
- ssh -l root 192.178.2.3
- ssh 192.178.2.3

### Absolute and Relative Paths
- An absolute path always begins with a "/".This indicates that teh path starts at the root directory 
- An example of an absolute path is

- cd /var/log/message

- A relative path does not begin wit a "/".It identifies a location relative to your current position.
- An example of a relative path is
 
 - cd /var
 - cd log
 - cd message

 ### Find files and Directories
 - find
 - locate


 ## Diff b/w Find and Locate
 - locate command is reliaze on own database
 - find command will not reliaze on own database

 - locate command dont have to specfy the path
 - find command we need to specify the path 

 - find / -name "sshd_config"
 - find . -name "sshd_config"

 - locate sshd_config

 - locate uses a prebuilt database, which should be regularly updated, while find iterates over a filesystem to locate files.Thus, locate is much faster than find, but can be inaccurate if the database( can be seen as a cache) is not updated.
 - To update locate database run **updatedb**

 ### Addint text to file
 3 Simple ways to add text to a file
- vi
- Redirect command output > or >>
- echo > or >>

### Input and output Redirects
- There are 3 redirects in Linux
- Standard input (stdin) and it has file descriptor number as 0
- Standard output (stdout) and it has file descriptor number as 1
- Standard error (stderr) and it has file descriptor number as 2

- Output (stdout) -1
- By default when running a command its output goes to the terminal
- The output of a command can be routed to a file using **>** symbol
- E.g ls -l > listings
      pwd > findpath
- If using the same file for additional output or to append to the same file then use **>>**
- E.g ls -la >> listings

- Input (stdin) - 0
- Input is used when feeding file contents to a file
- E.g cat < listings

- Error (stderr) -2
- When a command is executed we use a keyboard and that is also considered (stdin 0)
- That command output goes on the monitor and that output is (stdout 1)
- If the command produced any error on the screen then it is considered (stderr 2)
- We can use redirects to route errors from the screen
- E.g ls -l /root 2> errorfile

### tee
- "tee" command is used store and view (both at the same time) the output of any command
- echo "hello, welcome"|tee output
- echo "Added content"|tee -a output
- echo "Hello" | tee output1 output2 output2
- tee --version
- tee --help

### cut
Cut is a command line utility that allows you to cut parts of lines from  specified files or piped data and print the result to standard output.It can be used to cut parts of a line by delimieter; bye position,and character

- cut filename = Does not work
- cut --version = check version
- cut -c1 filename = List one character
- cut -c1,2,4 - Pick and chose character
- cut -c1-3 filename = List range of characters
- cut -c1-3,6-8 = List specific of characters
- cut -b1-3 filename = List by byte size
- cut -d: -f 6 /etc/passwd = List first 6th column separated by :
cut -d: -f 6-7 /etc/passwd = List first 6 and 7th column seperated by :
ls -l | cut -c2-4 = Only print user permissions of files/dir




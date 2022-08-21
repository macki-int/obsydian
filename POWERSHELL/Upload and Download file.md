Download under Windows
`pscp.exe username@remoteHost:/remote/dir/file.txt d:\local\dir`

Download under Linux
`scp username@remoteHost:/remote/dir/file.txt /local/dir/`

Upload under Windows
`scp d:\local\dir\file.txt username@remoteHost:/remote/dir/`

Upload under Linux
`scp /local/dir/file.txt username@remoteHost:/remote/dir/`


SFTP
```sftp user@192.168.1.10
Connected to 192.168.1.10.
sftp> dir
file1      file2  file3   
sftp> pwd
Remote working directory: /home/user
sftp> get file2
Fetching /home/user/file2 to file2
/home/user/file2                         100% 3740KB 747.9KB/s   00:05    
sftp> bye```

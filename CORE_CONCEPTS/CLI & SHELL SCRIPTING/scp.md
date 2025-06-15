#bash #powershell 

`scp` (Secure Copy Protocol) is a command-line utility that lets you securely copy files or directories between computers using the SSH protocol to provide both authentication and encryption.
It’s widely used for transferring files between:
- Two local/remote Linux machines
- A local machine and a remote server
- A remote server and your local machine


## Basic Syntax

```bash
scp [options] source destination
```



## Common Use Cases

### 1. Copy a File from Local to Remote

```bash
scp file.txt user@remote_host:/remote/directory/
```

### 2. Copy a File from Remote to Local

```bash
scp user@remote_host:/remote/file.txt /local/directory/
```

### 3. Copy a Directory (Recursively)

```bash
scp -r folder/ user@remote_host:/remote/directory/
```


## Authentication

SCP uses SSH, so it requires:

- SSH access (port 22 by default)
- Either a password or SSH key authentication

Example with a key file:

```bash
scp -i ~/.ssh/id_rsa file.txt user@remote_host:/remote/path/
```


## Common Options

|Option|Description|
|---|---|
|`-r`|Recursively copy directories|
|`-P`|Specify the remote port (capital `P`)|
|`-i`|Identity file (SSH private key)|
|`-v`|Verbose mode (debugging info)|
|`-C`|Enable compression during transfer|


## Security Notes

- Uses SSH for encryption
- Better than `ftp` or `rsh` for secure file transfer
- SCP is being replaced in some cases by more modern tools like `rsync` or `sftp`, which offer more flexibility

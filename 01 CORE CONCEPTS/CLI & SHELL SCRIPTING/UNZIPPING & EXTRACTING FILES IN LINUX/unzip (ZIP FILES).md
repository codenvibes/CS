
**Check if `unzip` is installed**

```bash
unzip -v
```

**Install `unzip` (if needed)**  
**Debian/Ubuntu:**

```bash
sudo apt update
sudo apt install unzip
```

**RHEL/CentOS/Fedora:**

```bash
sudo yum install unzip
# or
sudo dnf install unzip
```

**Unzip a file**

```bash
unzip file.zip
```

**Unzip to a specific directory**

```bash
unzip file.zip -d /path/to/destination
```

**List contents without extracting**

```bash
unzip -l file.zip
```

**Unzip specific files**

```bash
unzip file.zip file1.txt file2.txt
```


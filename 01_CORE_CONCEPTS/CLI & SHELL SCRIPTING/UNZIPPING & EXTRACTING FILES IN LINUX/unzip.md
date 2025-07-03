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


---

#### 📂 **3️⃣ RAR Files**

- **Install `unrar`**
    
    ```bash
    sudo apt install unrar       # Debian/Ubuntu
    sudo yum install unrar       # RHEL/CentOS
    sudo dnf install unrar       # Fedora
    ```
    
- **Extract `.rar`**
    
    ```bash
    unrar x file.rar
    ```
    

---

**📝 Tips**

- `x` means extract.
    
- `v` means verbose (show files while extracting).
    
- `z` is for gzip-compressed tarballs.
    
- `j` is for bzip2-compressed tarballs.
    

---

**Done!** Copy this as-is and you’re set.  
Want me to make a **printable PDF** version too? 🚀
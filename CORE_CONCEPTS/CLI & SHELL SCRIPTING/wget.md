#powershell #bash

## What is `wget`?

`wget` is a **non-interactive command-line tool** to download files from the web using:
- **HTTP / HTTPS**
- **FTP**
It’s useful in scripts, automation, and downloading files without a browser.

## Common `wget` Examples

### 1. Download a single file

```bash
wget https://example.com/file.zip
```

### 2. Download and save with a different name

```bash
wget -O newname.zip https://example.com/file.zip
```

### 3. Resume a broken download

```bash
wget -c https://example.com/largefile.zip
```

### 4. Download in the background

```bash
wget -b https://example.com/file.zip
```

### 5. Limit download speed

```bash
wget --limit-rate=200k https://example.com/file.zip
```

### 6. Download multiple files from a list

Create a text file (`urls.txt`) with one URL per line, then:

```bash
wget -i urls.txt
```


---

## References
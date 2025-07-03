**`curl`** is a command-line tool for transferring data to or from a server using various protocols (HTTP, HTTPS, FTP, etc.). It’s commonly used for testing APIs, downloading files, and more.

---

## Basic syntax

**Bash (Linux/macOS) and PowerShell (Windows)** are similar — the main difference is quoting and some syntax.

```bash
curl [options] [URL]
```

---

## Basic GET request

**Bash:**

```bash
curl https://example.com
```

**PowerShell:**

```powershell
curl https://example.com
```

➡️ Note: In **PowerShell**, `curl` is an alias for `Invoke-WebRequest` by default. To run the real `curl` executable, use `curl.exe` or install it via `winget`.

Example:

```powershell
curl.exe https://example.com
```

---

## Save output to a file

**Bash:**

```bash
curl -o output.html https://example.com
```

**PowerShell:**

```powershell
curl.exe -o output.html https://example.com
```

---

## Follow redirects

Many websites redirect HTTP to HTTPS — add `-L` to follow:

```bash
curl -L http://example.com
```

Same in PowerShell:

```powershell
curl.exe -L http://example.com
```

---

## Add headers

**Add custom headers (e.g., API key):**

```bash
curl -H "Authorization: Bearer YOUR_TOKEN" https://api.example.com/data
```

PowerShell:

```powershell
curl.exe -H "Authorization: Bearer YOUR_TOKEN" https://api.example.com/data
```

---

## POST request with JSON data

**Bash:**

```bash
curl -X POST -H "Content-Type: application/json" \
     -d '{"name":"ChatGPT"}' \
     https://api.example.com/endpoint
```

**PowerShell:**

```powershell
curl.exe -X POST -H "Content-Type: application/json" `
     -d '{"name":"ChatGPT"}' `
     https://api.example.com/endpoint
```

_(Note: In PowerShell, the backtick ` is the line continuation character)_

---

## Download multiple files

```bash
curl -O https://example.com/file1.txt -O https://example.com/file2.txt
```

---

## Show verbose output (debug)

```bash
curl -v https://example.com
```

---

## Quick test

Try:

```bash
curl https://api.github.com
```

Or in PowerShell:

```powershell
curl.exe https://api.github.com
```



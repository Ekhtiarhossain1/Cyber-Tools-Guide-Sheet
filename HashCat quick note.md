### **Command Structure**

> For Linux `hashcat` and for windows portables `./hashcat.exe`

hashcat -m <hash-mode> -a <attack-mode> <hashfile> <wordlist/mask> [options]

**Example:**

hashcat -m 160 -a 0 hash.txt rockyou.txt -o cracked.txt

* `-m 160` → HMAC-SHA1 (key = salt)
* `-a 0` → Dictionary attack
* `-o cracked.txt` → Save recovered passwords

---

### **Hash Modes (-m)**

* `0` → MD5
* `100` → SHA1
* `110` → SHA1($pass.$salt)
* `120` → SHA1($salt.$pass)
* `160` → HMAC-SHA1(key=salt)

> Full list: `hashcat.exe -h` → `-hh`


### **Attack Modes (-a)**

| Mode | Type                 |
| ---- | -------------------- |
| 0    | Dictionary           |
| 1    | Combination          |
| 3    | Brute-force          |
| 6    | Hybrid Wordlist+Mask |
| 7    | Hybrid Mask+Wordlist |
| 9    | Association          |

---

### **Common Options**

* `-o <file>` → output file
* `--show` → show cracked hashes from potfile
* `-O` → optimized kernels (faster, limited password length)
* `-w 3` → workload profile (1–4, high = more GPU usage)
* `--status` → real-time status
* `--force` → ignore warnings (use with caution)

---

### **Hash File Format**

* **Without salt:**

```
5f4dcc3b5aa765d61d8327deb882cf99
```

* **With salt:**

```
hash:salt
```

* **HMAC-SHA1 example:**

```
e5d8870e5bdd26602cab8dbe07a942c8669e56d6:tryhackme
```

---

### **Wordlist / Mask**

* Wordlists: `rockyou.txt`, `custom.txt`
* Masks: `?l?l?l?l?d?d` → 4 letters + 2 digits
* Custom charset: `-1 ?l?d`

---

### **Quick Examples**

**Dictionary attack:**

```powershell
hashcat.exe -m 0 -a 0 hash.txt rockyou.txt
```

**Brute-force 6 chars (letters + digits):**

```powershell
hashcat.exe -m 0 -a 3 hash.txt ?l?l?l?l?d?d
```

**Save results to file:**

```powershell
hashcat.exe -m 160 -a 0 hash.txt rockyou.txt -o results.txt
```

**Show already cracked hashes:**

```powershell
hashcat.exe --show hash.txt
```

---

### **Tips**

* Check hash mode before cracking → prevents errors
* Use optimized kernel `-O` for speed if password is short





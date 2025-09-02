The Harvester
TheHarvester is an open-source reconnaissance tool commonly used in OSINT and cybersecurity to collect publicly available information about a target domain. It gathers:
Subdomains
Email addresses
IP addresses
Hostnames
Virtual hosts
Open ports & banners
Employee names
It pulls data from multiple sources—including search engines, PGP key servers, threat feeds, and IoT indexes—while operating in a passive, stealthy manner

# **TheHarvester Syntax Cheatsheet**

---

## **Basic Syntax**
theharvester -d <domain> -b <source> [options]
```

* **`-d`** → Target domain (e.g., `example.com`)
* **`-b`** → Data source(s) to query (`google`, `bing`, `shodan`, `all`, etc.)
* **`[options]`** → Extra flags for limits, exporting, DNS brute force, etc.

---

## **Main Command Options**

| **Flag** | **Purpose**                           | **Example Command**    | **Expected Output**                       |
| -------- | ------------------------------------- | ---------------------- | ----------------------------------------- |
| `-d`     | Target domain name                    | `-d example.com`       | Sets the investigation scope              |
| `-b`     | Choose source(s)                      | `-b google` / `-b all` | Google-only or multi-source scan          |
| `-l`     | Limit results                         | `-l 200`               | Only collect 200 results from each source |
| `-s`     | Start from result X                   | `-s 50`                | Skip first 50 results                     |
| `-f`     | Save output to file (HTML, XML, JSON) | `-f results.html`      | Creates `results.html` in working dir     |
| `-v`     | Verify virtual hosts                  | `-v`                   | Confirms subdomains via DNS               |
| `-c`     | DNS brute force                       | `-c`                   | Attempts to find hidden subdomains        |
| `-n`     | Reverse DNS lookup                    | `-n`                   | Finds domain names from IPs               |
| `-p`     | Port scan & takeover check            | `-p`                   | Scans for open ports & vulnerabilities    |
| `-h`     | Show help menu                        | `-h`                   | Lists all options with usage              |

---

## **Source Options**

You can run TheHarvester against a single source or multiple at once.

**Popular sources**:

* `google`
* `bing`
* `duckduckgo`
* `linkedin`
* `shodan`
* `yahoo`
* `hunter` *(requires API key)*
* `pgp`
* `crtsh`
* `threatcrowd`
* `otx`
* `all` *(runs all available sources)*

---

## **Example Commands & Outputs**

### **1. Basic Email & Subdomain Search**

```bash
theharvester -d example.com -b google -l 200
```

**Output:**

```
[*] Emails found:
    admin@example.com
    contact@example.com

[*] Hosts found:
    mail.example.com -> 192.168.1.10
    shop.example.com -> 192.168.1.12
```

---

### **2. All Sources + HTML Report**

```bash
theharvester -d example.com -b all -l 500 -f report.html
```

**Output:**

```
[*] 25 emails found
[*] 42 hosts found
[*] 5 IP addresses found
[*] Report saved to report.html
```

---

### **3. DNS Brute Force + Virtual Host Check**

```bash
theharvester -d example.com -b bing -c -v
```

**Output:**

```
[*] Discovered hidden subdomain: test.example.com
[*] Verified via DNS lookup
```

---

### **4. Shodan for IoT Device Search**

```bash
theharvester -d example.com -b shodan
```

**Output:**

```
[*] Host: cam1.example.com -> Open ports: 80, 554
[*] Banner: "IP Camera Web Interface"
```

---

### **5. API Integration with Hunter.io**

```bash
theharvester -d example.com -b hunter --api-key YOUR_API_KEY
```

**Output:**

```
[*] Emails found via Hunter.io:
    john.doe@example.com
    jane.smith@example.com
```

---

## **Best Practices for Mastery**

* Always combine **multiple sources** (`-b all`) for broader coverage.
* Use **`-f`** to export results for later analysis.
* Start with **passive collection** (Google, Bing, DuckDuckGo) before moving to semi-active sources (Shodan).
* Rotate queries and use proxies if your IP gets rate-limited.
* Validate all results manually before drawing conclusions.

---
Got it — here’s the **extended list of TheHarvester commands** beyond the basic ones I already gave, including the more advanced, less commonly discussed flags and parameters.

These are useful if you want **full mastery** of TheHarvester for OSINT work.

---

##  **TheHarvester Advanced Command Reference**

| **Flag / Parameter** | **Purpose**                                                                                   | **Example**                   |
| -------------------- | --------------------------------------------------------------------------------------------- | ----------------------------- |
| `-t`                 | Sets the type of DNS brute force wordlist to use (default list in `/theHarvester/wordlists/`) | `-c -t subdomains.txt`        |
| `-e`                 | Exclude sources from the search                                                               | `-b all -e shodan,yahoo`      |
| `-g`                 | Use Google Dorks mode (queries crafted for recon)                                             | `-d example.com -b google -g` |
| `-r`                 | Perform reverse IP lookup via Bing                                                            | `-d example.com -b bing -r`   |
| `-m`                 | Set the delay between requests (seconds) to avoid being blocked                               | `-m 5`                        |
| `--dns-lookup`       | Perform standard DNS resolution on discovered hosts                                           | `--dns-lookup`                |
| `--dns-tld`          | Enumerate domains based on TLDs in a list                                                     | `--dns-tld tlds.txt`          |
| `--dns-brute`        | Brute-force subdomains with DNS wordlists                                                     | `--dns-brute`                 |
| `--dns-resolver`     | Specify a custom DNS resolver for lookups                                                     | `--dns-resolver 8.8.8.8`      |
| `--vhost`            | Attempt virtual host discovery                                                                | `--vhost`                     |
| `--takeover`         | Check if subdomains are vulnerable to takeover                                                | `--takeover`                  |
| `--shodan-api`       | Specify Shodan API key (required for `-b shodan`)                                             | `--shodan-api <API_KEY>`      |
| `--api-key`          | Use API keys for specific services like Hunter.io or Censys                                   | `--api-key <API_KEY>`         |
| `--source-list`      | Display all available data sources TheHarvester can use                                       | `--source-list`               |
| `--screenshot`       | Take screenshots of discovered hosts (requires Selenium & browser driver)                     | `--screenshot`                |
| `--limit-hosts`      | Limit number of hosts returned per source                                                     | `--limit-hosts 10`            |
| `--limit-emails`     | Limit number of emails returned per source                                                    | `--limit-emails 20`           |
| `--company`          | Use a company name instead of a domain for LinkedIn searches                                  | `--company "Acme Corp"`       |
| `--timeout`          | Set timeout for HTTP requests (seconds)                                                       | `--timeout 10`                |
| `--screenshot-dir`   | Save screenshots to a specific directory                                                      | `--screenshot-dir ./screens`  |

---

### 📌 **Notes on Advanced Flags**

* **`--takeover`** → This is particularly important for cybersecurity OSINT, as it detects whether an unused subdomain points to a third-party service that could be hijacked.
* **`--screenshot`** → Useful for visual OSINT reports; takes a snapshot of the target’s homepage or subdomains.
* **`--dns-tld`** → Helps find domains in multiple TLD variations (e.g., `.com`, `.net`, `.org`).
* **`-g` (Google Dork mode)** → Combines dorks like `site:example.com` automatically for richer recon.
* **`-m`** → Good for avoiding rate limits, especially with aggressive data sources like Google or Bing.

---
Alright — I’ll walk you through **all the advanced & less-known TheHarvester commands** I just listed, explaining them like a teacher would in class, so you not only *know what they do* but also *when and why to use them* in OSINT investigations.

---

## 📖 **TheHarvester – Advanced Commands Explained**

---

### **1. `-t` (Custom Wordlist for DNS Brute Force)**

* **What it does:**
  When you brute-force subdomains (`-c` or `--dns-brute`), TheHarvester uses a default wordlist.
  `-t` lets you **specify your own list** of potential subdomains.
* **Why it matters:**
  Your investigation may be more effective if you have industry-specific subdomain names (e.g., `vpn`, `intranet`, `mail`).
* **Example:**

  ```bash
  theharvester -d example.com -b bing -c -t subdomains.txt
  ```
* **OSINT Tip:**
  A good wordlist can uncover *hidden services* the default list would miss.

---

### **2. `-e` (Exclude Sources)**

* **What it does:**
  Runs against all sources except the ones you name.
* **Why it matters:**
  Some sources return too much irrelevant data or require an API you don’t have.
* **Example:**

  ```bash
  theharvester -d example.com -b all -e shodan,yahoo
  ```
* **OSINT Tip:**
  Speeds up scans when avoiding noisy or redundant data feeds.

---

### **3. `-g` (Google Dork Mode)**

* **What it does:**
  Automatically uses crafted Google search operators for recon.
* **Why it matters:**
  This applies **Google Dorking** principles directly from within TheHarvester.
* **Example:**

  ```bash
  theharvester -d example.com -b google -g
  ```
* **OSINT Tip:**
  Great for finding exposed documents, config files, or login pages.

---

### **4. `-r` (Reverse IP Lookup via Bing)**

* **What it does:**
  Finds other domains hosted on the same IP.
* **Why it matters:**
  May reveal **affiliated sites** or poorly secured subdomains.
* **Example:**

  ```bash
  theharvester -d example.com -b bing -r
  ```
* **OSINT Tip:**
  Useful for mapping an organization’s *entire* online footprint.

---

### **5. `-m` (Delay Between Requests)**

* **What it does:**
  Adds a pause (in seconds) between queries to avoid rate-limiting or IP bans.
* **Why it matters:**
  Crucial when querying Google, Bing, or APIs with strict limits.
* **Example:**

  ```bash
  theharvester -d example.com -b google -m 5
  ```
* **OSINT Tip:**
  For very large scans, always set a delay.

---

### **6. `--dns-lookup`**

* **What it does:**
  Resolves discovered hostnames to IP addresses.
* **Why it matters:**
  Links virtual names to real infrastructure.
* **Example:**

  ```bash
  theharvester -d example.com -b google --dns-lookup
  ```
* **OSINT Tip:**
  Helpful for identifying hosting providers or geographic server locations.

---

### **7. `--dns-tld`**

* **What it does:**
  Enumerates the same domain name across different TLDs.
* **Why it matters:**
  Organizations sometimes register multiple variations (`example.com`, `example.org`).
* **Example:**

  ```bash
  theharvester -d example -b google --dns-tld tlds.txt
  ```
* **OSINT Tip:**
  Good for finding *look-alike domains* used in phishing.

---

### **8. `--dns-resolver`**

* **What it does:**
  Uses a specific DNS resolver (e.g., Google’s `8.8.8.8`).
* **Why it matters:**
  Helps avoid DNS poisoning and speeds up lookups.
* **Example:**

  ```bash
  theharvester -d example.com -b bing --dns-resolver 8.8.8.8
  ```

---

### **9. `--vhost`**

* **What it does:**
  Checks for virtual hosts running on the same IP.
* **Why it matters:**
  Identifies **multiple websites** on a single server.
* **Example:**

  ```bash
  theharvester -d example.com -b all --vhost
  ```

---

### **10. `--takeover`**

* **What it does:**
  Checks for subdomains that could be hijacked (DNS points to unused service).
* **Why it matters:**
  Critical for security assessments and bug bounties.
* **Example:**

  ```bash
  theharvester -d example.com -b all --takeover
  ```
* **OSINT Tip:**
  Use only on domains you own or have permission to test.

---

### **11. `--shodan-api`**

* **What it does:**
  Sets your Shodan API key for IoT & exposed service scanning.
* **Why it matters:**
  Enables deeper recon by revealing open ports, banners, and device types.
* **Example:**

  ```bash
  theharvester -d example.com -b shodan --shodan-api <API_KEY>
  ```

---

### **12. `--source-list`**

* **What it does:**
  Displays all available data sources.
* **Why it matters:**
  Lets you explore lesser-known OSINT feeds supported by TheHarvester.
* **Example:**

  ```bash
  theharvester --source-list
  ```

---

### **13. `--screenshot`**

* **What it does:**
  Takes screenshots of discovered hosts.
* **Why it matters:**
  Adds visual evidence for OSINT reports.
* **Example:**

  ```bash
  theharvester -d example.com -b all --screenshot
  ```

---

### **14. `--company`**

* **What it does:**
  Uses a company name instead of a domain (mainly for LinkedIn searches).
* **Why it matters:**
  Targets people and profiles instead of infrastructure.
* **Example:**

  ```bash
  theharvester --company "Tesla Inc" -b linkedin
  ```

---

### **15. `--timeout`**

* **What it does:**
  Sets a maximum wait time (seconds) for HTTP requests.
* **Why it matters:**
  Avoids hanging if a source is slow.
* **Example:**

  ```bash
  theharvester -d example.com -b all --timeout 10
  ```

---

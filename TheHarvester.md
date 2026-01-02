# **The Harvester**
TheHarvester is an open-source reconnaissance tool commonly used in OSINT and cybersecurity to collect publicly available information about a target domain. 

It gathers: Subdomains, Email addresses, IP addresses, Hostnames, Virtual hosts, Open ports & banners, Employee names. 
It pulls data from multiple sources—including search engines, PGP key servers, threat feeds, and IoT indexes—while operating in a passive, stealthy manner

# **TheHarvester Syntax Cheatsheet**

## Basic Syntax

```bash
theHarvester -d <domain> -b <source>
````

Example:

```bash
theHarvester -d example.com -b google
```

---

## Common Options

### `-d <domain>`

Target domain to search.

```bash
theHarvester -d example.com -b bing
```

---

### `-b <source>`

Data source to use.

**Common Sources:**

* google
* bing
* yahoo
* duckduckgo
* baidu
* linkedin
* twitter
* github
* shodan
* censys
* crtsh
* all

```bash
theHarvester -d example.com -b all
```

---

### `-l <limit>`

Limits the number of results.

```bash
theHarvester -d example.com -b google -l 200
```

---

### `-s <start>`

Starts search from a specific result number.

```bash
theHarvester -d example.com -b google -s 100
```

---

### `-f <filename>`

Saves results to a file (HTML and XML).

```bash
theHarvester -d example.com -b bing -f results
```

---

### `-h`

Displays help menu.

```bash
theHarvester -h
```

---

## Advanced Usage

### Gather Subdomains and Emails

```bash
theHarvester -d example.com -b google,bing,duckduckgo
```

---

### Shodan Integration

Requires Shodan API key.

```bash
theHarvester -d example.com -b shodan
```

---

### Censys Integration

Requires Censys API credentials.

```bash
theHarvester -d example.com -b censys
```

---

### GitHub Reconnaissance

```bash
theHarvester -d example.com -b github
```

---

### LinkedIn Employee Enumeration

```bash
theHarvester -d example.com -b linkedin
```

---

## Output Formats

* HTML report
* XML report

Files are saved using the `-f` flag.

---

## Useful Combos

### Full Recon Scan

```bash
theHarvester -d example.com -b all -l 500
```

---

### Save and Review Later

```bash
theHarvester -d example.com -b google -l 300 -f example_report
```

---

## Notes

* Some sources require **API keys**
* Excessive querying may lead to **temporary blocking**
* Use only for **authorized and ethical OSINT investigations**


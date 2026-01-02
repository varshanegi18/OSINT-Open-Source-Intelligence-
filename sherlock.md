# Sherlock Guide

Sherlock is a popular Open-source OSINT reconnaissance/information gathering Tool. which is used to find accounts with specific username from across multiple platform.

---

# Flags used in sherlock

### - version
This flag find and provide the output of the installed version of the sherlock in the system.  
```bash
sherlock - version
```

### --verbose / -v / --debug
This flag provides more information about the search process.
```bash
sherlock --verbose <username>
```

### {?}
This helps to search for similar usernames.
```bash
sherlock <username>{?}
```

### --dump-response
This option allows us to see the full HTTP response returned by each website that Sherlock queries, such as:
HTTP status code (200, 404, 302, etc.)
HTTP headers
Raw HTML response body
```bash
sherlock <username> --dump-response
```

### --timeout <seconds>
By default, the timeout is 60 seconds for each website request. With this option, we can change the timeout according to the need.
This helps reduce total scan time and avoid long waits on slow websites.
```bash
sherlock <username> --timeout 4
```

### --print-all
By default, Sherlock only shows websites where the username exists.
This flag displays every website it checks, including where the username is not found.
```bash
sherlock <username> --print-all
```

### --print-found
This flag displays only those sites where the username is found.
```bash
sherlock <username> --print-found
```

### --browse
After Sherlock discovers accounts linked to the username, this option automatically opens the found profile URLs in the default web browser.
```bash
sherlock <username> --browse
```

### --nsfw
By default, Sherlock avoids NSFW (Not Safe For Work) websites, meaning adult or explicit content sites.
Using the --nsfw flag tells Sherlock to include NSFW websites in the search.
```bash
sherlock <username> --nsfw
```

### --exclude
Prevents Sherlock from checking certain websites.
```bash
sherlock <username> --exclude reddit facebook
```

### --output <filename>
Saves the results of your search into the specified file.
```bash
sherlock <username> --output result.txt
```

### --folderpath <path>
Saves all output files to a custom directory instead of the default sherlock/results/.
```bash
sherlock <username> --folderpath /home/user/sherlock_results/
```

### --threads <number>
Sets the number of threads Sherlock uses.
More threads = faster search (depending on your CPU and network connection).
```bash
sherlock <username> --threads 20
```

### --async
Runs Sherlock in asynchronous mode.
This dramatically increases speed by sending multiple requests at once.
```bash
sherlock <username> --async
```

### --proxy <url>
Routes Sherlock requests through an HTTP proxy.
Useful for maintaining anonymity.
```bash
sherlock <username> --proxy http://127.0.0.1:8080
```

### --local
Runs Sherlock using local site data.
```bash
sherlock <username> --local
```

### --unique-tor / -u
Makes requests over Tor with a new Tor circuit after each request.
This increases runtime and requires Tor to be installed and available in the system path.
```bash
sherlock johndoe --unique-tor
```

### --csv
Creates a Comma-Separated Values (CSV) file.
```bash
sherlock <username> --csv
```

### --xlsx
Creates the standard file format used by modern Microsoft Excel.
```bash
sherlock <username> --xlsx
```
---

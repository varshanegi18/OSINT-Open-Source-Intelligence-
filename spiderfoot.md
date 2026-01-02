# Spiderfoot Cheat Sheet 

| Command | Description | Example |
|--------|------------|---------|
| `-h`, `--help` | Show help message and exit | `python3 sf.py -h` |
| `-V`, `--version` | Display SpiderFoot version and exit | `python3 sf.py --version` |
| `-d`, `--debug` | Enable debug output | `python3 sf.py -d -s example.com` |
| `-q` | Disable logging (also hides errors) | `python3 sf.py -q -s example.com` |
| `-s TARGET` | Specify target for the scan | `python3 sf.py -s example.com` |
| `-l IP:port` | IP and port to listen on (Web UI) | `python3 sf.py -l 127.0.0.1:5001` |
| `-max-threads <num>` | Maximum modules to run concurrently | `python3 sf.py -s example.com -max-threads 10` |
| `-m mod1,mod2` | Enable specific modules | `python3 sf.py -s example.com -m sfp_dnsresolve,sfp_whois` |
| `-M`, `--modules` | List available modules | `python3 sf.py -M` |
| `-u {all,footprint,investigate,passive}` | Auto-select modules by use case | `python3 sf.py -s example.com -u footprint` |
| `-x` | Strict mode (only direct-consume modules) | `python3 sf.py -s example.com -x` |
| `-t type1,type2` | Event types to collect | `python3 sf.py -s example.com -t DOMAIN_NAME,IP_ADDRESS` |
| `-T`, `--types` | List available event types | `python3 sf.py -T` |
| `-f` | Filter out non-requested event types | `python3 sf.py -s example.com -t IP_ADDRESS -f` |
| `-F type1,type2` | Show only selected event types | `python3 sf.py -s example.com -F EMAILADDR,USERNAME` |
| `-C scanID` | Run correlation rules on a scan ID | `python3 sf.py -C 123456789` |
| `-o {tab,csv,json}` | Output format (default: tab) | `python3 sf.py -s example.com -o json` |
| `-H` | Do not print field headers | `python3 sf.py -s example.com -o csv -H` |
| `-n` | Strip newlines from output data | `python3 sf.py -s example.com -n` |
| `-r` | Include source data field in output | `python3 sf.py -s example.com -o csv -r` |
| `-S LENGTH` | Maximum data length to display | `python3 sf.py -s example.com -S 100` |
| `-D DELIMITER` | CSV delimiter (default: ,) | `python3 sf.py -s example.com -o csv -D ';'` |

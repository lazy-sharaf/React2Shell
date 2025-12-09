**React2Shell** is a proof-of-concept scanner/exploit helper for **CVE-2025-55182 (React Server Components RCE)**. It is intended for **authorized security testing and research only**.

## Features
- Multi-target scanning via file input (`-f targets.txt`)
- Default recon command chain when `-c` is omitted: `whoami`, `cat /etc/passwd`, `ls -la /var/www`
- Silent failures: only successful results are printed
- Activity spinner so you know scans are in progress
- Normalizes targets with/without schema

## Quick Start
```bash
# Single target, default recon chain
python exploit.py -t https://example.com

# Single target, custom command
python exploit.py -t https://example.com -c "id"

# Multiple targets from file (one per line, # comments allowed)
python exploit.py -f targets.txt
```

## Usage
```
usage: exploit.py [-h] [-t URL] [-c CMD] [-f FILE]

options:
  -h, --help         show this help message and exit
  -t, --target URL   Target URL or domain (default: https://example.com)
  -c, --command CMD  Command to execute on target; if omitted runs default set
  -f, --file FILE    Path to file containing targets (one per line)
```

**Default commands when -c is not set**
- `whoami`
- `cat /etc/passwd`
- `ls -la /var/www`

## Output behavior
- Shows a spinner while each target/command is running
- Prints results only on success
- After all scans, prints a notice if nothing succeeded

## Disclaimer
This tool is for educational and authorized security testing only. You are responsible for complying with all applicable laws and obtaining proper permissions before testing any systems. The authors are not liable for misuse or damage. Use responsibly.
# Sublist3r (fork by Mazen Nafee)

**Fork of** aboul3la/Sublist3r — maintained by Mazen Nafee.  
This fork focuses on robustness, tests, and developer ergonomics:

- Defensive DNSdumpster CSRF extraction (regex + BeautifulSoup fallback).  
- Validation and safe handling of nameserver entries to avoid dnspython errors.  
- Unit tests and small repro scripts for the fixes.  
- GitHub Actions CI to run tests on push and pull requests.

---

## About

Sublist3r is a Python tool for enumerating subdomains using OSINT. It helps penetration testers and bug hunters collect subdomains for a target domain by querying search engines and public services. Sublist3r supports multiple sources including Google, Yahoo, Bing, Baidu, Ask, Netcraft, VirusTotal, ThreatCrowd, DNSdumpster, and ReverseDNS.

Subbrute is integrated to increase coverage via bruteforce using an improved wordlist. Credit for subbrute goes to TheRook.

---

## Quick start

```bash
# clone the fork
git clone https://github.com/mazennafee/Sublist3r.git
cd Sublist3r

# create and activate a virtual environment
python -m venv .venv
source .venv/bin/activate

# install editable and test dependencies
pip install --upgrade pip
pip install -e .
pip install -r requirements.txt || true

# run tests
pytest -q

Usage

Command line

# basic usage
python3 ./sublist3r.py -d example.com

# use the console script after activating venv
sublist3r -d example.com -t 10 -o results.txt

Options

-d, --domain Domain name to enumerate subdomains of

-b, --bruteforce Enable the subbrute bruteforce module

-p, --ports Scan found subdomains against specific TCP ports

-v, --verbose Enable verbose mode and display results in realtime

-t, --threads Number of threads to use for bruteforce or lookups

-e, --engines Comma separated list of search engines to use

-o, --output Save results to a text file

-h, --help Show help and exit

Examples

# show help
python3 sublist3r.py -h

# enumerate subdomains
python3 sublist3r.py -d example.com

# enumerate and scan ports 80 and 443
python3 sublist3r.py -d example.com -p 80,443

# enable bruteforce
python3 sublist3r.py -b -d example.com


Using Sublist3r as a module

import sublist3r

subdomains = sublist3r.main(
    domain="example.com",
    no_threads=40,
    savefile="example_subdomains.txt",
    ports=None,
    silent=False,
    verbose=False,
    enable_bruteforce=False,
    engines=None
)

print(len(subdomains), "unique subdomains found")

Return value The main function returns a set of unique subdomain strings.

Dependencies and supported Python versions
Supported Python This fork targets Python 3.8 or newer.

Key dependencies

requests

dnspython

beautifulsoup4

Install dependencies with:
pip install -r requirements.txt
Add or update requirements.txt with pinned minimums for reproducible installs.

Tests and CI
This fork includes unit tests and small repro scripts under tests/ and a GitHub Actions workflow at .github/workflows/ci.yml that runs pytest on push and pull requests.

Run tests locally:
pytest -q

License
This project is licensed under the GNU GPL v2. See the LICENSE file for details.

Credits

TheRook — subbrute integration and bruteforce approach

Bitquark — inspiration for the subbrute wordlist

Ahmed Aboul-Ela — original Sublist3r project

Contributing

If you want to contribute, please:

Fork the repository and create a feature branch.

Add tests for new behavior.

Open a pull request with a clear description and reproduction steps.

See CONTRIBUTING.md for more details.

Changelog
Unreleased

Defensive DNSdumpster CSRF extraction and fallback parsing.

Nameserver validation to avoid dnspython errors.

Unit tests and CI added.

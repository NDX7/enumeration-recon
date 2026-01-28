## FFUF Cheatsheet

# Fast Fuzzer U Fool (FFUF) is a high-performance web fuzzer used for discovering hidden content and subdomains. 
FFUF is a powerful tool for security professionals to test the security of web applications and infrastructure. It helps identify vulnerabilities by systematically sending requests to a target and analyzing the responses. 
Here are some ways FFUF can be used in a security testing context:

# 1. Directory & File Discovery

Identifying exposed directories and files can reveal potential entry points or sensitive information. 
Basic Web Server Content Scan:
ffuf -u http://target.com/FUZZ -w /path/to/common_paths_wordlist.txt
Finding Common Web Application Files:
ffuf -u http://target.com/FUZZ -w common_files.txt -e .bak,.orig
Testing for Directory Traversal with Recursive Scanning:
ffuf -u http://target.com/FUZZ -w directories.txt -recursion 

# 2. Subdomain Identification
Discovering subdomains helps understand the attack surface of an organization's online presence.
Publicly Accessible Subdomain Discovery:
ffuf -u http://FUZZ.target.com -w /path/to/subdomain_wordlist.txt
Identifying Subdomains with Specific Headers (VHosts):
ffuf -u http://target.com -H "Host: FUZZ.target.com" -w vhost_wordlist.txt 

# 3. Optimizing Security Scans
Efficiently running scans and filtering results is crucial for effective security testing.
Ignoring Default Error Pages: Use -fs <size> to filter out responses of a specific size, often used for default 404 pages.
Focusing on Potential Success or Redirects: Use -mc 200,301,302 to only show responses indicating successful requests or redirects.
Managing Scan Speed: Adjust the number of threads with -t or limit requests per second with -rate to avoid overloading the target or triggering security defenses during testing.
Saving Scan Results for Analysis: Use -o results.txt to save the output in a file

# Offensive Tools 1
This is my notes about several tools used in Offensive Security on TryHackMe, like Gobuster, nmap, Metasploit. I am also looking at web security books while at it.

# Basic Pentesting
Rules of Engagement: the rules for what is allowed and what is not allowed while pentesting the system, written out concretely.

For example, what do you do if you gain access to sensitive data? When do you perform your attacks? Who will be involved? Where will it be at?

Both sides agree to the terms and are to stay in the bounds of their agreement. 

The 5 stages of pentesting include:
1. Information Gathering: OSINT, finds as much information as possible from publicly available source about the target (for example, social media).
    - There is passive reconaissance, which is to find information quietly, and active reconaissance, in which you reaches out to your target to gain information, such as phishing.
2. Enumeration/Scanning: scans the target systems and gets even more information, using networking scanning, port scanning, system scanning (for example, OS information).
3. Exploitation: starts creating payloads and performing attacks on the target system. 
4. Privilege Escalation: tries to get higher privilege, moving laterally through the networks and systems. 
5. Aftermath: Essentially lessons learned. Tries to cover tracks, sets a backdoor, examines the networks more, and report on vulnerabilities.

There are also frameworks for cybersecurity testing across web apps, network communications, etc. 

Testing Types:
1. Black Box: do not know the internals of the application.
2. Grey Box: know only partial information about the application. 
3. White Box: know all the setups of the application.

# Web Security 
## Basic Application
### View Page Source
`View Page Source`: looks at the response returned by the server in form of HTML, CSS, JS, so on. 

This does not give the same output as in `Inspect`, which shows the state of the DOM after running all the code, even if both are HTMLs. 

Comments and other details here can tell us about the tools used to build the website, including their versions, known as `frameworks`. Also, try to probe and find secret links and directories.

The `Directory Listing Feature` allows us to list all files under a subdirectory of the website if enabled.

### Inspect 
In `Inspect`, it shows the current state of the DOM after running the code. 

You can add or delete parts of the HTML, CSS, JS in anyways client-sided, which will be reflected in the current webpage.

In the `Debugger` tab, where you have your CSS and JS files, you can set breakpoints by clicking on the line number. Then refresh the page and there would be a popup to control whether the debugger runs the code or pauses.

Sometimes, JS code can be `minimized` and `obfuscated`, as in being in one line and encoded. Use the `Pretty-Print` option which looks like a pair of brackets {} to spread the code out to different lines.

In the `Network` tab, any packets that you send (via sending data in forms) will be shown in the packet list, which shows all packets received and all packets sent in this webpage. 

## Finding Information
There is 3 types, which is manually, automated, and OSINT (open-source intelligence) for finding more information on webpages.
### Manual
`robots.txt`: Can be accessed as a hidden file in the current directory. Tells which pages are allowed or not allowed to be seen when searching on browsers.
`Favicon`: It is a small icon to represent the brand. When building from a framework, the favicon is defaulted as representing that framework if not changed during development. `OWASP` has a database on favicons (their `hash` value) and their frameworks. Favicons are the `favicon.ico`.
`sitemap.xml`: Unlike robots.txt, this file shows which directories the browser can list.
`HTTP headers`: To look for this, we can look at the packets in the `Network` tab, which shows the HTTP headers, or we could use any terminal commands for sending packets, like curl, Netcat, so on.
`Framework`: For getting more information on framework, we could do a Google search on that framework and that version. 

### OSINT
`Google Dorking`: basically utilizing the Google search engine to the fullest. You can add filters like `site:`, `filetype:`, etc along with your search.
`Wappalyzer`: to identify the technologies that a website uses.
`Wayback Machine`: an archive of old websites. You could look up old websites for a certain domain and perhaps those websites are still available.
`Github`: a version control system. You can search for the company's repositories here and find any left-open source code.
`S3 Buckets`: this is a storage service by AWS for saving files and contents. The URL is in the form of https://{name}.s3.amazonaws.com, where it is the name of the bucket.

# Automation
`Directory enumeration`: tools such as ffuf, dirb, and gobuster. Gobuster is quite commonly used to brute-force find files and paths via a wordlist of common directory and file names.

Example command formats:

    gobuster dir --url <URL> -w <path-to-wordlist>

    gobuster --help

    gobuster dir --help


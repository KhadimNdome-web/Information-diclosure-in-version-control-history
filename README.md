# Information-diclosure-in-version-control-history
Information disclosure in version control history

#Description

I opened the Website´s URL `https://0a43004b04b325c6806ae96c00630034.web-security-academy.net/` and logged the code `./feroxbuster -u https://0a3d00b304a1402783b651e500700038.web-security-academy.net/ -w Desktop/common.txt` into the Windows Command Line Interface using Linux as the operating system, to find files or directories that could expose vulnerabilities.

After reviewing the code shown by the CLI, i decided to log in the web browser all the files containing `.git` which lead presumably to files shared or stored using Git. 

Of all the directories this one `https://0a43004b04b325c6806ae96c00630034.web-security-academy.net/.git/` contained a file named "COMMIT_EDITMSG". I entered and the prase `Remove admin password from config` was shown, message that could be indicating developers sharing the Adminstrator´s password through Git.

In another file named `config` i found the email and name of the user, another finding that exposes the user account and credentials to even bigger threat than the already found vulnerabilities.

After inspecting each file contained in the directory, i downloaded all the files through the CLI by typing `wget -r` and name of the URL from where the files are found:

`wget -r https://0a43004b04b325c6806ae96c00630034.web-security-academy.net/.git/`




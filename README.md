# Information-diclosure-in-version-control-history
Information disclosure in version control history

#Description

I opened the Website´s URL `https://0a43004b04b325c6806ae96c00630034.web-security-academy.net/` and logged the code `./feroxbuster -u https://0a3d00b304a1402783b651e500700038.web-security-academy.net/ -w Desktop/common.txt` into the Windows Command Line Interface using Linux as the operating system, to find files or directories that could expose vulnerabilities.

After reviewing the code shown by the CLI, i decided to log in the web browser all the files containing `.git` which lead presumably to files shared or stored using Git. 

Of all the directories this one `https://0a43004b04b325c6806ae96c00630034.web-security-academy.net/.git/` contained a file named "COMMIT_EDITMSG". I entered and the prase `Remove admin password from config` was shown, message that could be indicating developers sharing the Adminstrator´s password through Git.

In another file named `config` i found the email and name of the user, another finding that exposes the user account and credentials to even bigger threat than the already found vulnerabilities.

After inspecting each file contained in the directory, i downloaded all the files through the CLI by typing `wget -r` and name of the URL from where the files are found:

`wget -r https://0a43004b04b325c6806ae96c00630034.web-security-academy.net/.git/`

I then procedeed to use Git Gui by choosing to open an existing file repository, in this case the previously downloaded file `.git`, which showed the code:

`deleted file mode 100644
@@ -1 +0,0 @@
-ADMIN_PASSWORD=env('ADMIN_PASSWORD')`

This `-ADMIN_PASSWORD=env('ADMIN_PASSWORD')` can be intepreted as ``-ADMIN_PASSWORD=variable` and
written in red indicates that the file has been recently modified.

I chose then the option `Visualize Mater´s History` from the `Repository` window of Git, that showed me the hard-coded or included password of the old application written in red:

`-ADMIN_PASSWORD=2dkmzbvabovv232i0tjj`

And again, but this time in color green, the info about the file that has just been modified:

`+ADMIN_PASSWORD=env('ADMIN_PASSWORD')`

Assuming that the user didn´t change his/her password, I copied and pasted the password in the login page of the target website, after trying to guess with more attempts the name of the username, that resulted as being registered as `administrator`, thus making possible the login in the administrator´s account.





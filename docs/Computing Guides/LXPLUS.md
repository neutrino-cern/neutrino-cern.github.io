# LXPLUS

## Obtaining a CERN Computing Account
...

## Accessing LXPLUS

### Via the Terminal
On Linux and MacOS systems, you can connect via the terminal by typing:

```ssh yourusername@CERN.CH```

You will then be prompted to enter your password. On Windows systems, we recommend using [Windows Subsystem for Linux](https://learn.microsoft.com/en-us/windows/wsl/install). After installing you can connect the same way as described above.


### With Visual Studio Code

You may use [Visual Studio Code](https://code.visualstudio.com/) as a way of accessing [LXPLUS](https://lxplusdoc.web.cern.ch/) interactive logon service with the full benefits of using an Integrated Development Environment (IDE). 

After installing, go to the extensions tab (left sidebar at the bottom) and find the Remote - SSH extension and install it. Then, you can open the command palette `(ctrl + shift + p)` and go to `Remote - SSH: Connect to Host`, then `+ Add New SSH Host...` then you can connect as you would in the terminal.

#### Extensions for Debugging and Linting
 - Officially supported extensions for [C++](https://code.visualstudio.com/docs/languages/cpp) and [Python](https://code.visualstudio.com/docs/languages/python) 
 - ROOT macros linting and debugging have a look at this [blogpost](https://root.cern/blog/root-on-vscode/)

## Setting up Passwordless Access

#### Linux and MacOS
We can edit the `ssh` config located in `/home/username/.ssh/config`. Insert the following into the file by replacing `username` with your CERN username and `vm` with the host that we are trying to connect to. This configuration allows us to set up a jump connection using the `lxtunnel` host if we are not on the CERN network, for example, if we are working remotely.

```
Host vm
  HostName vm.cern.ch

Host *.cern.ch
    # your CERN username
    User username
    GSSAPITrustDns yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials yes

Match host *.cern.ch,!lxtunnel*.cern.ch,!lxplus*.cern.ch !exec "hostname -A | grep -q '.cern.ch '"
  ProxyJump lxtunnel.cern.ch 
```

Now using the terminal we can get a Kerberos ticket by the command: 

```
kinit username@CERN.CH
```

Then you should be able to connect via the terminal using VSCode without having to enter your password.

#### Windows
Since there is no official support from the Remote SSH extension to use WSL, by default it uses the Windows ssh client. There is however a hacky way of using WSL to make the `ssh` connection instead. We need to create a `.bat` file with the following content. 

```
C:\Windows\system32\wsl.exe ssh %*
```

To point Remote-SSH extension to use that `.bat` file, we begin by opening the commmand pallete using `ctrl + shift + p` and selecting `> Remote-SSH: Settings`. From there we find the `Remote.SSH: Path` setting and add the absolute path of the `.bat` file. 

To make this work seamlessly, we must make sure the contents of the ssh config files are the same in WSL and the default one in Windows. In Windows that file is usually located in `C:\Users\username\.ssh\config` and in WSL, it is usually located in `/home/username/.ssh/config`. After this, this configuration should let you connect to lxplus or any virtual machines behind the CERN firewall.



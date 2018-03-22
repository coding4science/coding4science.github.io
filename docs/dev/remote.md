# Access to a remote server by SSH

## The SSH protocol


## Local connection to computation servers 

```sh
ssh your_login@calcul_server
```

You will be connected to. Then, the following commands will be usefull:

-   ```ls``` -- list directory contents;
-   ```cd``` -- change the working directory;
-   ```mkdir``` -- create new directories;
-   ```man``` -- read the manual;
-   ```matlab``` or ```python``` -- execute your scripts;
-   ```top``` -- display the running process;
-   ```exit``` or ```ctrl + d``` -- close the ssh connection.

### On windows
Use putty

## SCP -- secure copy of remote file

Another way to copy files to the computation servers is to use ```scp``` on your computer (without ssh connection):

```sh
scp /path/to/the/file/on/your/computer.extension your_login@calcul_server:/path/on/the/server/where/you/want/to/copy/the/file.extension  
```

On the contrary, if you want to copy a file from the server to your computer, you will enter (without ssh connection):

```sh
scp your_login@calcul_server:/path/to/the/file/on/the/server.extension /path/on/your/computer/where/you/want/to/copy/the/file.extension  
```

Note that the ```-r``` can be used to copy recursively all the files of a directory.
Windows users can also use [winSCP][] which provides a graphical interface.

[winSCP]: http://winscp.net


## Remote connection with a VPN or a ssh tunnel

As the access to some resources may be limited from outside your institution network, you may need to put in place secure connections before being able to access these resources.
There are mainly two ways that your insitution may provide.

### VPN
The first way of secure remote access is a Virtual Private Network or VPN.

### SSH Tunneling

The second way is using SSH Tunneling if your institution provides at least one server that is accessible from the outside (a "gateway").

It is possible to reach the computation servers with any computer, even your personal one. You have to open a SSH tunnel in a first terminal, and then in a second terminal, you can copy file with ```scp``` command or open a SSH connection.

The SSH tunnel:
```sh
ssh -N -L 22000:calcul_server:22 your_login@gateway
```
Once authenticated, the command will not prompt anything. It looks like the command is stopped, but it is not the case. Do not close this terminal! 

Then, you can copy file or open a SSH connection:
```sh
scp -P 22000 /path/to/the/file/on/your/computer.extension your_login@localhost:/path/on/the/server/where/you/want/to/copy/the/file.extension  
ssh -p 22000 your_login@localhost
```

## Authentication key

Tired of typing your password? Use the key authentication! Follow the following process (while your computer is connected to the Gipsa network) and the password prompt will not show again. [More details here][PuTTY:key] for Windows user using PuTTY. 

1.  Generate on your computer a couple of public and private keys:
```sh
ssh-keygen
```
2.  Do not share your private key! 
3.  Copy the public key on the servers:
```sh
cat ~/.ssh/id_rsa.pub | ssh your_login@calcul_server "cat - >> ~/.ssh/authorized_keys"
```

If you want more information about key authentication, you can read [this][source].

[source]: http://doc.fedora-fr.org/wiki/SSH_:_Authentification_par_clé
[PuTTY:key]: http://www.howtoforge.com/ssh_key_based_logins_putty


## Virtual terminals

```screen``` and ```tmux``` are terminal multiplexers: you can manage several terminal from a single window. The virtual terminals may be detached from the screen and continue to run in background. It is possible to attach them again, later. You can even turn off your computer while the virtual terminal is running on the server.

1.  Create a virtual terminal:

```sh
screen -S myVirtualTerminalName
```

2.  Launch your computations;
3.  Detach the virtual terminal: press simultaneously ```ctrl + a``` and then ```d```;
4.  List the running virtual terminals and attach one of them:

```sh
screen -ls
screen -x myVirtualTerminalName
```


## Tips

If you absolutely need a graphical interface for the Matlab launched on the server, you should specify the ```-X``` option when opening the ssh connection:

```sh
ssh -X calcul
```

I didn't put ```your_login@``` in front of ```calcul``` here. In fact, by default ```ssh``` will use the local login to log on the server. If there are identical, there is no need to specify it. 

Other tips:

-   you can work locally on the server to increase your script performances (especially if you read/write lots of files). Create a directory in ```/tmp/``` and copy your scripts and data here.
-   do not display any figure in the script you launched on the server; by default there is no graphical interface and your code will crash.
-   do not forget to use ```sreen``` or ```tmux```.

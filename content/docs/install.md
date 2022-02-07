---
title: Installation
weight: 1
---
# Installation

WiTTY runs on Linux (ARM and x86), macOS, and WSL2 (Windows subsystem for Linux, basically Linux). You can install from the pre-built binary or from the source code. 


{{< tabs "install_method" >}}
{{< tab "From Binary" >}} 
1. Visit the release page of WiTTY at [https://github.com/syssecfsu/witty/releases](https://github.com/syssecfsu/witty/releases)
2. Download the release for your system
3. Decompress the binary with the following command at selected location.
   
   ```tar -xzvf witty_vx.x.x_xxx.tar.gz```

   >For example, use `tar -xzvf witty_v1.1.1_linux_amd64.tar.gz` to decompress release v1.1.1 for Linux on AMD64.

{{< /tab >}}
{{< tab "From Source Code" >}} 
1. Install the [go](https://go.dev/) compiler. __Make sure you have go 1.17 or higher.__ 



2. Download the source code release and unzip it, or clone the repo
   
   ```git clone https://github.com/syssecfsu/witty.git```

3. Go to the root directory of the source code and build the program with 
    
    ```./build.sh```

    This shell script will build WiTTY and copy the binary with other needed files to the `release/` directory. You can move the `release/` directory to other places you want. __Run WiTTY from this directory.__

  {{< hint info >}}
  macOS users can install go with [homebrew](https://brew.sh/). Note that macOS has its own version of golang installed. Do not remove it. Just add the path of newly installed golang at the beginning of the PATH environment variable. 
  {{< /hint >}} 
  
  {{< hint danger >}}
  WiTTY uses [go:embed](https://pkg.go.dev/embed) to embed assets in the binary. Remember to re-build WiTTY after changing templates. 
  {{< /hint >}}
{{< /tab >}}

{{< /tabs >}}


# Post-installation Configuration
1. WiTTY uses TLS to protect its traffic. You can request a free [Let's Encrypt](https://letsencrypt.org/) cert or use a self-signed cert. Here is how to create a self-signed cert in the ```tls``` sub-directory:
   
   \# Generate a private key for a curve

    ```openssl ecparam -name prime256v1 -genkey -noout -out private-key.pem```

    \# Create a self-signed certificate

    ```openssl req -new -x509 -key private-key.pem -out cert.pem -days 360```

2. Add a user to the user accounts, follow the instructions on screen to provide the password
   
   ```./witty adduser <username>```

   {{< hint info >}}
   WiTTY uses sub-commands for different functions. See details [here]({{< relref "/docs/ui" >}})
   {{< /hint >}}

3. Start the server and specify the command-line (CLI) program to run when user connects. 

   ```./witty run bash``` 

   {{< hint info >}}
   If so desired, you can disable user authenticate with ```-n/-naked```, (not recommended). In the following example, WiTTY will run the `ls` command without user authentication:

   ```./witty run -naked ls```    
   {{< /hint >}}

   {{< hint info >}}
   WiTTY normally listens on port 8080. It can be overridden with the ```-p/-port``` option:
   {{< /hint >}}

4. Connect to the server with your browser at port 8080 or the one specified in step 6, for example

   ```https://<witty_server_ip>:8080```


# Example Use Case

WiTTY doesn't support Windows because Windows doesn't have [PTY](https://en.wikipedia.org/wiki/Pseudoterminal). You can still use WiTTY to access Windows terminal through a proxy. 

Here is how to do it. We can run WiTTY on a Raspberry Pi running [Raspbian](https://www.raspberrypi.com/software/) (at address `192.168.1.2`). When a user connects via browser to `https://192.168.1.2:9000`, WiTTY will start a new `ssh` session to the Windows machine (at address `192.168.1.3`) running a SSH server. The command to run WiTTY on the RPI is as follows:

   ```./witty run -p 9000 ssh 192.168.1.3 -l user_name```

The user can use any compatible browsers, such as that on a phone, to connect to the Windows machine without install a SSH client.

{{< mermaid >}}
graph LR
A[user on a phone] -- browser --> B[RPI: 192.168.1.2 <br /> runs WiTTY]
B -- ssh --> C[Windows: 192.168.1.3 <br /> runs SSH server ]
{{< /mermaid >}}

## Configure and connect to remote Ipython kernel with Spyder3

### 1. Launch Ipython kernel on remote machine and create associated json file in the specified dir (-f command)

```
ipython kernel --matplotlib 'inline' -f ~/myremotemachine.json
```

### 2. Copy the json file to your local machine (scp will do!)
Now that the json file is on both machines, you can launch and connect to this kernel.
Launch it on your remote with command in 1 and go to step 3.

### 3. IMPORTANT: Local port forwarding, must be done at each session
When the kernel is active on your remote, launch the following locally:

```
for port in $(cat myremotemachine.json | grep '_port' | grep -o '[0-9]\+'); do ssh user@xxx.xxx.xx.xxx -f -N -L $port:127.0.0.1:$port done;  done
```

where 1. **user** = **your istitutional username**, 2. **xxx.xxx.xx.xxx** = the ip adress of the server you are connecting to.

### 4. Connect Spyder editor to the remote kernel using myremotemachine.json

In (local) Spyder3 IDE go to **Consoles**, **Connect to an existing kernel**, **connection info** and browse for myremotemachine.json

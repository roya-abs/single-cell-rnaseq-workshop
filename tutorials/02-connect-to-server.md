# Connecting to the Linux Server
Processing raw sequencing files can require substantial computational resources.

Instead of running Cell Ranger on our personal laptops, we will use an Amazon EC2 instance, a remote Linux computer hosted on Amazon Web Services (AWS).

Each participant will receive:
- The **server IP address**.
- A unique Linux **username** which is your **first name**.
- A **password** for connecting to the server.
- A **personal working directory** for storing results.

Each participant has an individual Linux account and a personal home directory on the server.

**Important**: Your username and password are personal. Do not share them with other participants or upload them to GitHub.

All participants will process the same input dataset independently.

Cell Ranger is already installed and the required input files are prepared.

## Important guidlines for using the shared server
During this workshop, approximately 10 participants will use the same server simultaneously.
To ensure that everyone can complete the exercise successfully:

1. Connect to the server only during your assigned group session.

2. Use only your own Linux account.

3. Run Cell Ranger only when instructed.

4. Do not modify or delete files in the shared data directories.

5. Do not run the same Cell Ranger command multiple times.

### 1. Open a terminal

**macOS**
1. Press Command + Space to open Spotlight.
2. Type Terminal.
3. Press Enter.

**Windows**
1. Open the Start menu.
2. Search for PowerShell or Windows Terminal.
3. Open the application.

### 2. Connect to the server using SSH

In your terminal type:

```
ssh YOUR_USERNAME@SERVER_IP
```
example:
```
ssh roya@203.0.113.42
```
When connecting to a server for the first time, you may see a message similar to:
```
The authenticity of host 'SERVER_IP' can't be established.
ED25519 key fingerprint is SHA256:...
Are you sure you want to continue connecting (yes/no/[fingerprint])?
```

type: 
```
yes
```
You will then be asked for your password. Enter the provided password and press Enter.
**Important:** When typing your password, no characters, dots, or asterisks will appear on the screen. This is normal and is a security feature of the terminal.
If the password is correct, you will be logged in to the server.

After successfully connecting, you should see a command prompt similar to:
```
roya@203.0.113.42:$
```
The exact appearance may differ.


**Note:** 
Some institutional, university, or public Wi-Fi networks restrict outgoing connections to external servers, including SSH connections (typically using port 22).
If you are connected to such a network, you may receive an error such as:
```
ssh: connect to host 203.0.113.42 port 22: Connection timed out
```
In this case, try connecting through a different network, such as your mobile hotspot.





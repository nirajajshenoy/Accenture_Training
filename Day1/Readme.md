# Installing the Dependencies

Note: If any of the following dependencies are available on your laptop, then no need to install it.

## Update Packages

In case of a fresh Ubuntu 22 installation, use the following command to update the packages before installing other dependencies.  
```
sudo apt update
```

## cURL
Install curl using the command
```
sudo apt install curl -y
```

## Git
Install git using the command
```
sudo apt install git -y
```

## NodeJS (Ver 18.x) using NVM
Step 1: Install NVM (Node Version Manager), open a terminal and execute the following command.
```
wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.5/install.sh | bash
```
Step 2: Then execute the following command to install NodeJs
```
nvm install 18
```
Now make if it says NMV not found then close the terminal and open a new one.  

Step 3: Check  the version of nodeJS installed
```
node -v
```

Step 4: Check  the version of npm installed
```
npm -v
```

## Docker
Step 1: Download the install script
```
curl -fsSL https://get.docker.com -o get-docker.sh
```
Step 2: Execute permission for the script
```
sudo chmod +x get-docker.sh
```
Step 3: Execute the script
```
./get-docker.sh
```
Step 4: Remove the script
```
rm get-docker.sh
```
Step 5: To manage Docker as a non-root user
```
sudo usermod -aG docker $USER
```

## JQ
INstall JQ using the following command
```
sudo apt install jq -y
```

## Build Essential
Install Build Essential uisng the commnad
```
sudo apt install build-essential
```

## Go
Step 1: Download Go
```
wget https://go.dev/dl/go1.24.2.linux-amd64.tar.gz
```
Step 2: Extract
```
sudo tar -C /usr/local -xzf go1.24.2.linux-amd64.tar.gz
```

Step 3: Add /usr/local/go/bin to the PATH environment variable. Open the /etc/environment file
```
sudo gedit /etc/environment
```
Or
```
sudo nano /etc/environment
```
Step 4: Append the following to the end of `PATH` variable and save
```
:/usr/local/go/bin
```

## Visual Studio Code
Download and install the latest version of VS code from here: https://code.visualstudio.com/download

To install, either launch it by providing execution permission, or execute the following command
```
sudo dpkg -i [filename]
```

## Restart
Finally, restart the system to make the changes permanent.

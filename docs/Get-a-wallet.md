# XDAG Wallets how-to

Quick links:
1. Windows
	1. [GUI](#gui)
	2. [CLI](#cli)
2. [MacOS](#macos)
3. [Linux](#linux)

## GUI

### 1. Download the appropriate zip archive

64bit (x64) Windows Console and GUI executables or
32bit (x86) Windows Console and GUI executables.

Type | Link
|------------|--------------
64bit | https://github.com/XDagger/xdag/files/2586909/XDag.x64.zip
32bit | https://github.com/XDagger/xdag/files/2586912/XDag.x86.zip

Download the **Source** if you want to build the software using MS Visual Studio.

Type | Link
|------------|--------------
zip | https://github.com/XDagger/xdag/archive/0.3.0.zip
tar.gz | https://github.com/XDagger/xdag/archive/0.3.0.tar.gz

You can also find the latest releases [here.](https://github.com/XDagger/xdag/releases)

### 2. Unpack the archive in any folder of your choice on your PC

### 3. Run xdagwallet.exe for GUI version. If you wish to use CLI version, please scroll down to [CLI version](#cli)  

![Xdagwallet Executable](https://i.imgur.com/ucaWYNm.png)

### 4. Search a pool

Click on "Select a pool", on the right, at website [https://xdag.io/pools](https://xdag.io/pools)

### 5. Paste the address of your favorite pool in the corresponding box (Pool: poolip:port) and then click the **Connect** button

![Pool input](https://i.imgur.com/t6bOVZ8.png)

### 6. Set a password

After clicking the **Connect** button, the wallet will ask you to set up a password, and a confirmation of it. You can let the password be blank at your own risk. Save this password in a secure location. If you lose the password, you will not be able to access your funds.  

![Password1](https://i.imgur.com/jJrZxhl.png)
![Password2](https://i.imgur.com/OF2x0Of.png)

### 7. Set random key

After you have setup your password, you will be asked to enter a random character sequence. It is recommended to choose a truly random or pseudo-random sequence.

![RandomKey](https://i.imgur.com/LzpN7NC.png)

The entered characters will be used to generate random keys. After that, the program will create the file dnet_key.dat with a random key for the RSA algorithm of the transport layer within a few minutes. In addition, the file dnet_key.dat will be used to generate random data after each subsequent start of the program. The program will also create the wallet.dat file with private keys for the ECDSA signature algorithm. Files dnet_key.dat and wallet.dat should be kept in secret.
  
![New files in folder](https://i.imgur.com/b6egFQf.png)

During this process, the wallet may not respond during a short time. Depending on the technical specification of your computer, it can take several minutes.  

### 8. Done

Now your wallet is running. You can see your address showed in the corresponding box (Account:). 

![Finished](https://i.imgur.com/Sl4nWvl.png)

<a name="cli"></a>

## CLI

### 1. Download the appropriate zip archive

64bit (x64) Windows Console and GUI executables or 
32bit (x86) Windows Console and GUI executables.

Type | Link
|------------|--------------
64bit | https://github.com/XDagger/xdag/files/2586909/XDag.x64.zip
32bit | https://github.com/XDagger/xdag/files/2586912/XDag.x86.zip

Download the **Source** if you want to build the software using MS Visual Studio.

Type | Link
|------------|--------------
zip | https://github.com/XDagger/xdag/archive/0.3.0.zip
tar.gz | https://github.com/XDagger/xdag/archive/0.3.0.tar.gz

You can also find the latest releases [here.](https://github.com/XDagger/xdag/releases)

### 2. Unpack the archive in any folder of your choice on your PC

### 3. Search a pool

Click on "Select a pool", on the right, at website [https://xdag.io/pools](https://xdag.io/pools)

### 4. Create a bat file for ease of use

Copy and paste the following in a Notepad document. Feel free to use your favorite pool address instead of the one we provide here.

```bat
xdag -m 0 insert_here_pool_address
```

Save this document as run.bat in the same folder as the wallet files you extracted earlier. When you want to start the wallet, you simply have to double click the bat file.

![Create bat file](https://i.imgur.com/VBjtebt.png)

### 5. Run the CLI by double clicking the bat file

### 6. Create a password
After running the bat file, the wallet will ask you to set up a password, and a confirmation of it. You can let the password be blank at your own risk. Save this password in a secure location. If you lose the password, you will not be able to access your funds.  

Type in your password. Please note that it will not show up for security reasons.
![CLIPassword1](https://i.imgur.com/EzHQ4d9.png)
![CLIPassword2](https://i.imgur.com/VFlK4NT.png)

### 7. Set random key

After you have setup your password, you will be asked to enter a random character sequence. It is recommended to choose a truly random or pseudo-random sequence.

![CLIRandomKey](https://i.imgur.com/BDWHQSL.png)

The entered characters will be used to generate random keys. After that, the program will create the file dnet_key.dat with a random key for the RSA algorithm of the transport layer within a few minutes. In addition, the file dnet_key.dat will be used to generate random data after each subsequent start of the program. The program will also create the wallet.dat file with private keys for the ECDSA signature algorithm. Files dnet_key.dat and wallet.dat should be kept in secret.
  
![New files in folder](https://i.imgur.com/b6egFQf.png)

During this process, the wallet will show the text *Generating host keys...*. Depending on the technical specification of your computer, it can take several minutes. Do note close the window until this has finished.

![CLIGeneratingHostKey](https://i.imgur.com/7JsUtoN.png)

### 8. Done

Once the generation of host keys has finished, you will see the following output:

![CLIFinished](https://i.imgur.com/OeU1ZaS.png)

### 9. Help

Use the help command to access the help documentation in the CLI. It is copied here for your convenience:

```xdag> help
Commands:
  account [N] - print first N (20 by default) our addresses with their amounts
  balance [A] - print balance of the address A or total balance for all our addresses
  block [A]   - print extended info for the block corresponding to the address or hash A
  exit        - exit this program (not the daemon)
  help        - print this help
  keygen      - generate new private/public key pair and set it by default
  level [N]   - print level of logging or set it to N (0 - nothing, ..., 9 - all)
  miners      - for pool, print list of recent connected miners
  mining [N]  - print number of mining threads or set it to N
  net command - run transport layer command, try 'net help'
  pool [CFG]  - print or set pool config; CFG is miners:fee:reward:direct:maxip:fund
  run         - run node after loading local blocks if option -r is used
  state       - print the program state
  stats       - print statistics for loaded and all known blocks
  terminate   - terminate both daemon and this program
  xfer S A    - transfer S our XDAG to the address A
```

<a href="macos"></a>

## MacOS

### 1. Install

Download binary file from [release page](https://github.com/XDagger/xdag/releases).  
Unzip the zip file to what folder you want.

### 2. Search a pool

Click on "Select a pool", on the right, at website [https://xdag.io/pools](https://xdag.io/pools)

### 3. Run

For example: the miner with 2 CPU mining threads, in daemon mode, connected to the pool put.xdag.server.here:13654

	$ ./xdag insert_here_pool_address
	Enter random characters: [enter]
		

### 4. Already have an account

Copy your wallet.dat, dnet_key.dat and storage folder in this folder.
Then run below command
		
	$./xdag insert_here_pool_address

### 5. See if you are connected to the pool

	xdag> state
	[see state]

### 6. See your balance

	xdag> balance
	[balance]

### 7. See your address

	xdag> account
	[address]

### 8. Transfer funds to another address:

	xdag> xfer [amount] [address]

### 9. Terminate xdag process:

	xdag> exit

### 10. Backup your wallet

	Copy you wallet folder in a safe place, that isn't the same computer!
	Just wallet.dat file alone isn't enough to be able to restore the wallet!
	Try that even your backup works and that shows the same wallet address of
	your original wallet.

<a href="linux"></a>

## Linux

### 1. Install dependencies

	$ sudo dnf install git gcc openssl-devel libgmp3-dev
	   or
	$ sudo apt-get install git gcc libssl-dev libgmp3-dev

### 2. Clone from the git repository

	$ git clone https://github.com/XDagger/xdag

### 3. Make

	$ cd xdag/client
	$ make

### 4. Search a pool

Click on "Select a pool", on the right, at website [https://xdag.io/pools](https://xdag.io/pools)

### 5. Run

For example: the miner with 2 CPU mining threads, in daemon mode, connected to the pool put.xdag.server.here:13654

	$ ./xdag insert_here_pool_address
	Enter random characters: [enter]

### 6. Already have an account

	Put your wallet.dat, dnet_key.dat and storage folder in this folder.
	Then run below command
	$./xdag insert_here_pool_address

### 7. See if you are connected to the pool

	xdag> state
	[see state]

### 8. See your balance

	xdag> balance
	[balance]

### 9. See your address

	xdag> account
	[address]

### 10. Transfer funds to another address

	xdag> xfer [amount] [address]

### 11. Terminate xdag process

	xdag> exit

### 12. Backup your wallet

	Copy you wallet folder in a safe place, that isn't the same computer!
	Just wallet.dat file alone isn't enough to be able to restore the wallet!
	Try that even your backup works and that shows the same wallet address of
	your original wallet.
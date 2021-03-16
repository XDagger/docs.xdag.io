## Topic
- [Installation and Connecting](#installation)
- [Usage (Windows GUI)](#usage-gui)
- [Usage (command line)](#usage-cli)
- [Backup and Recovery](#backup-recovery)
- [Set up a pool](#pool-setup)  
- [Set up a test network environment](#testnet-setup)

## <a name="installation"></a> Installation and Connecting

### Binaries for Windows and MacOS

* Download the binary from the [release page](https://github.com/xdagger/xdag/releases)
* Unextract the software
* XDAG is run from and saves files within its own directory
* For the command line version on Windows, please run from a `cmd` window
* For MacOS, run from a `terminal` window


### Building from source for MacOS

* Install dependencies

        $ brew install openssl libtool gmp autoconf
    
* Clone from the git repository

        $ git clone https://github.com/XDagger/xdag

* Build the client
  
    With make

        $ cd xdag/client
        $ make
        
    With automake

        $ cd xdag/automake
        $ autoreconf -if
        $ ./configure
        $ make
        $ cd ../client

    With cmake

        $ mkdir build
        $ cd build
        $ cmake .. -DBUILD_TAG=mac
        $ make


* With the error of missing "libsecp256k1"

Install libsecp256k1 with following commands

```
libsecp256k1 is built using autotools:

    $ ./autogen.sh
    $ ./configure
    $ make
    $ ./tests
    $ sudo make install  # optional
```

### Building from source for Linux

* Install dependencies

        fedora $ sudo dnf install git gcc openssl-devel libgmp-dev libtool autoconf

    or

        debian $ sudo apt-get install git gcc libssl-dev libgmp-dev libtool autoconf
 
** Attention: please use gcc 4.9+ **
* Clone from the git repository

        $ git clone https://github.com/XDagger/xdag

* Build the client

    With make (old method)

        $ cd xdag/client
        $ make
        
    With automake (new method)

        $ cd xdag/automake
        $ autoreconf -if
        $ ./configure
        $ make
        $ cd ../client

    PS:if happened  -bash: autoreconf: command not found, you should install autoconf,automake tools:
    sudo apt-get install autoconf automake libtool

## <a name="usage-gui"></a> Usage (Windows GUI)

todo


## <a name="usage-cli"></a> Usage (command line)

* Connecting to a pool

    * Windows

            xdag -m 0 pool.address.here:13654

    * MacOS and Linux

            ./xdag -m 0 pool.address.here:13654

* First run
    * Upon the first run, you will be prompted to `enter random characters`.
      
      Do so. Make it long and very random. This is not a password.

    * You will then be prompted for a wallet password. Enter one if desired, then hit OK.

    * Generation will take some time; please be patient.

    * When the software is ready, you will be presented with an `xdag >` prompt.

* Get the pool connection status

      state
      [software state is shown]

* Retrieve your balance

      balance
      [balance info is shown]

* Show your XDAG address

      account
      [address with balance is shown]

* Transfer funds to another address

      xfer <amount> <address>
        
* Exit the software

      terminate


## <a name="backup-recovery"></a> Backup and Recovery

* It is advised to back up the entire working directory, and store read-only.

* The important files to keep are `wallet.dat`, `dnet_key.dat` and the `storage` folder.

* To recover, place the above noted files in your newly extracted or compiled client directory.        

## <a name="pool-setup"></a> Set up a pool  
Todo

## <a name="testnet-setup"></a> Set up test network environment

- Build  
        Build your own version.  

- Setup internal testnet  
        1. Plan your testnet topology.  
        2. Modify netdb-testnet.txt and netdb-white-testnet.txt with your IPs.  
        3. Launch your hosts with `-t -disable-refresh` options.  
        4. Launch your miner/wallet with `-t` option.  
        5. Currently only command line miner/wallet able to join testnet.  


## <a name="faq"></a> FAQ

Q1: Cannot make xdag successfully due to secp256k1 errors on Ubuntu 18.x   
A1: Please run following commands.
```
cd secp256k1
./autogen.sh
./configure

cd ..
cd automake
autoreconf -if
./configure
make
```
The detail issue is described in [https://github.com/XDagger/xdag/issues/514](https://github.com/XDagger/xdag/issues/514)

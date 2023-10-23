# Ucrypt 
###### Data Encryption Software

    git clone https://github.com/rcastrucci/ucrypt.git

<br>

![profile image](https://github.com/rcastrucci/ucrypt/blob/main/dist/docs/ucrypt_architecture.png#gh-dark-mode-only)

### Description:

<b>Ucrypt</b> is a versatile encryption tool, written in Python and designed to meet the demands of the most 
security-conscious software users.<br>

### Key Features:

* <b>AES 256-bit</b>: AES encryption standard with 256-bit keys to ensure an exceptional level of data security.

* <b>Random Key Generation</b>: Create random symmetric keys to protect your data, making it virtually impervious to breaches.

* <b>Key Derivation with Passwords</b>: Enhance security by generating keys derived from passwords, requiring both the key and the password for decryption.

* <b>AES and RSA Hybrid mode</b>: Add an extra layer of security by encrypting the AES key with RSA, allowing decryption only with the corresponding RSA private key.


## Linux install
    ./install-linux
###### The installation process has made easy to install and uninstall at any time.


## Mac install
    ./install-mac
###### All it does is to create configuration files and check for dependencies.

## Options
![profile image](https://github.com/rcastrucci/ucrypt/blob/main/dist/docs/options.png#gh-dark-mode-only)

## Usage
###### The basic approach would be to encrypt using a symmetric key. This can be done with one line command     
#### Encryption
    ucrypt --generate-key personal.key --encrypt myFiles --save-as myFilesSecure --key personal.key
#### Decryption
    ucrypt --decrypt myFilesSecure --save-as myFiles --key personal.key
###### All these options have short versions such as: -g -e -s -k -d


## Second Factor
To enhance security of your symmetric keys. It is possible to encrypt data using a second factor authentication.
Setting up a password on Ucrypt conf file to be used automatically each time you encrypt data. This could be done
as follows:

#### Setting up password
    ucrypt --auth
###### This will prompt a input text hidden to type and confirm your password. The password will be saved in a conf file with a Hash SHA-256.

#### Enabling Second Factor
    ucrypt --enable-factor
###### short version: ucrypt -ef

Done! Now each time you encrypt data, Ucrypt will use your password to derivative a key. That means, to decrypt data, one must have the key and must know the password. 

### But do I need to generate a key each time?
    # What if I want to perform an automatic task every day to encrypt data, and don't want to have thousands of keys?
    # It is possible to set up a default key configuration and with second factor enabled, there are no worries.


## Set up default key
    ucrypt --generate-key
###### That by itself will generate a random key and save at the Ucrypt key folder.
With a password created, a second factor enabled and your default key set up. To encrypt myData and save as mySecureData, is simple as that:

#### Encryption
    ucrypt -e myData -s mySecuredData
#### Decryption
    ucrypt -d mySecuredData -s myData
###### Then will be necessary to type your password.


## Check Ucrypt status
    ucrypt --status
###### short version: ucrypt -t
The command above will display if you have your password set up correctly, if second factor is enabled or disabled and show you which key is set as default.


## Change Default Key
    ucrypt --default-key personal.key
###### short version: ucrypt -dk personal.key

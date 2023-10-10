# Hive Payout Script For CTP

2 Python script files, one will create the payout data, and the other will do the payout.

*Please note that this software is in early Beta stage, and that you need to know what you are doing to use it.*

## Installation

For Ubuntu and Debian install these packages:
```
sudo apt-get install python3-pip build-essential libssl-dev python3-dev python3-setuptools python3-gmpy2
```

### Install Python Packages

Install needed packages by (you may need to replace pip3 by pip):
```
sudo pip3 install -U beem hiveengine pandas datetime
```

## Configure And Run The Script

Clone the Github repository to your home directory:
```
cd ~
git clone https://github.com/flaxz/ctppay
```

Make the bash files executable:
```
cd ~/ctppay
chmod u+x getpay.sh pay.sh reset.sh
```

Edit the settings for getting the payout data, then save and close the file.

```
sudo apt install nano 
cd ~/ctppay
ls
nano getindex.py
```

token = Base token for the payout (CTP).

getHolders = Accounts to remove, separated by comma.

payToken = Token to pay out (INDEX).

payAmount = Amount to pay out (10.0).

payMemo = Memo for the payout.

minOwnedStake = The minimum owned stake of CTP needed to get a payout (1.0).

minDecimal = The minimum decimal for the token to be paid out (INDEX 8 decimals = 0.00000001)

### Run the Script

Run the script to get the payout data.

```
cd ~/ctppay
./getpay.sh
```

View the files in nano.

```
cd ~/ctppay/pay
ls
nano filename.csv
```

## Run the payout

Before the first run, set a wallet password for beempy.

```
beempy
changewalletpassphrase
```

Enter new password twice, and.

```
exit
```

After getting the payout data, then run the payout.

```
cd ~/ctppay
ls
./pay.sh
```

1. Enter account name.
2. Enter wallet password for beempy (on the first run you will be also be prompted to import the Active Key).

Now the payout will run to completion, if no issues arise, it will automatically check for sufficient funds in the account, and exit if it's not, and if so add funds and then restart with.

```
./pay.sh
```

There is no need to edit anything as all the payouts are saved in the database, and it will resume where it stopped.

After successful run check the account to see that it has paid out correctly.

You do not have to delete anything, but if need be for whatever reason you can delete all CSV files and the database with the command below.

```
cd ~/ctppay
./reset.sh
```

That is it, and remember that it is beta level code.

Coders: 
@flaxz
@bambukah
@sc-steemit
@captaincryptic

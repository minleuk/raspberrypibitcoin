ASIC Bitcoin Mining on Raspberry Pi Image
=========================================

Welcome to Raspberry Pi for ASIC bitcoin mining.  This is a convenience image for getting started with running your USB ASIC bitcoin miner with Raspeberry Pi.  Everything done here can be done off the shelf, but hopefully this saves you a little time.  

This image preconfigures:

1. Raspberrian

2. cgminer (https://github.com/ckolivas/cgminer)

3. cgminer dependencies

If you find any of this valuable, please consider tipping at this address:

Luke Duncan (www.lukejduncan.com)

![Alt text](/bitcoin-tip-address.png "Bitcoin tip address")

1B5VGMpGsTfFJPn2VpKZ5ABbD7qeZstxC1

You can also find the address for the author of cgminer at the github page provided above.

Installation Requirements
-------------------------

1. Raspberry Pi, preferaby with a case, power source and required SD Card - Can be bought on Amazon and Tindie (https://www.tindie.com/search/?q=Raspberry%20Pi)

2. ASIC bitcoin miner - This has been tested with the Butterfly Labs 10 GH/s Bitcoin Miner https://products.butterflylabs.com/homepage/10-gh-s-bitcoin-miner.html

3. Join a mining pool.  This example assumes Slushes Pool.  You can learn more about pooled mining and joing Slushes Pool here http://mining.bitcoin.cz/

4. Setup a wallet and associate it with a mining pool.  Online wallets exist such as Coinbase.

Starting to mine
-------------------------

1. Format the SD Card using this tool (or similar) https://www.sdcard.org/downloads/formatter_4/

2. Copy these files to the root directory of your SD Card and plug it into your Raspberry Pi.  It should boot without issues.  You can log in and play around with the username "pi" and the password "password".  You can start a GUI by typing "startx".

3. Plug in your Raspberry Pi with your ASIC miner and ethernet connection.  You will need to plug your pi into a HDMI capable monitor to see what IP address you are using.

4. Ssh into your pi with the username "pi" and password "password".  example: "ssh pi@192.168.0.110"

5. Change your password to something you're comfortable with. Execute "passwd"

6. Update the mine.sh file in your home directory  change the url, username, and password to match your credentials of your mining pool.

7. Execute: "dmesg | tail".  You should see the words "FTDI USB Serial Device converter now attached to ttyUSB0"  If you don't then run through the instructions here https://forums.butterflylabs.com/showwiki.php?title=Tutorials:ASIC+Mining+on+Ubuntu+and+other+Linux+distros.  Raspberrian should have all of the drivers you need pre-installed already.

8. Start mining!  Execute: "cd ~; ./mine.sh;"

9. (Optional) You'll need to make sure you don't kill your mining operations when you disconnect from ssh.  You can do this a number of ways.  I prefer to use tmux.  To do so, before you start mining, start a tmux session with "tmux".  Next perform step 6.  Then detach from the session with the key combination "ctrl+b, d".  You can then reconnect now or in the future with "tmux attach -t 0" or you can see all tmux sessions running with "tmux ls".

Keeping your software up to date
---------------------------------

1. Keep Raspberrian up-to-date via the normal apt tool.  You can find more about Raspberrian at http://www.raspberrypi.org/

2. Keep cgminer up-to-date by pulling the latest from git and rebuilding.  This step will take a while.  "cd ~/projects/bitcoin/cgminer; git pull; ./autogen.sh; configure; make; sudo make install" 

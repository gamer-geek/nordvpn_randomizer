# nordvpn_randomizer

This Bash script was created for simply randomize the available [NordVPN](https://nordvpn.com/) OpenVPN UDP files for a specific country choosen by the user. This script is also provided AS-IS and is a work in progress when I have some time over.

It assumes you have followed the [instructions](https://nordvpn.com/tutorials/linux/openvpn/) for the shell installation method. What that page doesn't add is that you can create a file named *auth.txt*  in */etc/openvpn/* (as root) and use it for bit of automation regarding connecting to the VPNs provided by NordVPN.

```
$> sudo nano /etc/openvpn/auth.txt
```

- Now add your NordVPN **username** on the first row and your NordVPN **password** on the second row.

- Save and exit nano by pressing X and confirm.

```
$> sudo chmod 0600 /etc/openvpn/auth.txt
```

The problem now is that each NordVPN OpenVPN UDP files provided doesn't understand that is should use the file you just created. However, this script takes care of that automagically so you don't have to worry about it.


Let's clone this puppy to your workstation/server.

```
$> mkdir ~/sources && cd ~/sources

$> git clone https://github.com/damianrath/nordvpn_randomizer.git
```

Now just put a symbolic link to *~/sources/nordvpn_randomizer/nordvpn_randomizer* somewhere in your path. Preferably in *~/bin/*.


After you have run the script (as root) it will ask you for a country-code. If you don't know which country-codes that are available you can just press ENTER and a list will be provided for you.

When you have choosen a country-code the script will proceed to randomly pick a VPN server for you and connect to it. After a few seconds it will inform you what VPN IP address you now have and exit.

You kill your OpenVPN process with:  `sudo killall openvpn`


That's it!



## TODO

- Add more error checking for the shellscript-challenged people.

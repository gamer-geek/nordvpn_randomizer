# nordvpn_randomizer

This Bash script was created for simply randomize the available [NordVPN](https://nordvpn.com/) OpenVPN UDP files for a specific country choosen by the user. This script is also provided AS-IS and is a work in progress when I have some time over.

This particular script is for users *without* Network-Manager and/or server owners. The version for Network-Manager can be found [here](https://github.com/damianrath/nordvpn_randomizer-nm).

```

$> sudo apt-get update
$> sudo apt-get install unzip dnsutils ca-certificates openvpn -y
$> cd /etc/openvpn
$> sudo wget https://downloads.nordcdn.com/configs/archives/servers/ovpn.zip
$> sudo unzip ovpn.zip
$> sudo rm ovpn.zip
$> sudo nano auth.txt   # Add your NordVPN username on the first line and your password on the second line.
$> sudo chmod 0600 auth.txt
$> sudo chmod 0700 ovpn_udp ovpn_tcp
$> mkdir ~/sources && cd ~/sources   # If you have a different git dir just exchange 'sources' with yours.
$> git clone https://github.com/damianrath/nordvpn_randomizer.git
$> sudo ln -s ~/sources/nordvpn_randomizer/nordvpn_randomizer /usr/local/bin/
$> sudo nordvpn_randomizer
```

The script also accepts command line arguments. List them with:  nordvpn_randomizer --help


After you have run the script (as root) it will ask you for a country-code. If you don't know which country-codes that are available you can just press ENTER and a list will be provided for you.

When you have choosen a country-code the script will proceed to randomly pick a VPN server for you and connect to it. After a few seconds it will inform you what VPN IP address you now have and exit.

You kill your OpenVPN process with:  `sudo killall openvpn`


That's it!


I highly recommend adding [speedtest-cli](https://github.com/sivel/speedtest-cli) to your system so you can check out latency and actual VPN network throughput (Listing of the quickest VPNs for the choosen county will be added soon(tm)).


## TODO

- Add more error checking for the shellscript-challenged people.
- Add more features.
- Add multiple country -feature for randomization choices.
- Rewrite this README.


## Disclaimer

I'm not affiliated with NordVPN in any way except being a normal customer that enjoys their services.

##  This is a note on how to fix the "Wifi Adaptor not Found" problem in Ubuntu. 
### It is a personal note for future reference.

Before running the below commands, I did gather information from different sources on the web and did consult ***Stack Exchange*** also.

I did follow <a href="https://askubuntu.com/questions/990378/wi-fi-not-working-on-lenovo-thinkpad-e570-realtek-rtl8821ce" target="_blank">this</a> solution and it worked for me. 
Below there are the steps I have followed after logging in as a **super user** in the command line.

```
sudo-i
```

Run sudo -i. This will give you an interactive root shell. Note that the $ at the end of your prompt has changed to a #, indicating that you have root access. But you fall in the root home directory (/root/). From here you can run any sequence of commands as root, or run the command exit to leave the root shell.

After logging as a **super user**, run the following commands:
 
```
sudo apt-get install --reinstall git dkms build-essential linux-headers-$(uname -r) 
git clone https://github.com/tomaspinho/rtl8821ce 
cd rtl8821ce 
chmod +x dkms-install.sh 
chmod +x dkms-remove.sh 
sudo ./dkms-install.sh
```

After this is completed successfully, you should reboot and find that your Wifi is working.
You also want to make sure SecureBoot is Disabled in the BIOS settings or it won't let you load the unsigned self-complied kernel module.

Thanks to all the support and answer I found out there on the web. 
Hope someone will benefit of this little note. 
Although quick wins sometimes are good, I really reccomend to search a bit out there and understand the steps.

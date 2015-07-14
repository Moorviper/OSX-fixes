# OSX-fixes
wlan (DNS) fix for yosemite after Oct 16 2014 


=== Usage: ===

Clone Repo and go into the Folder.

then:
```
cp ./mDNSResponder /usr/sbin/mDNSResponder
cp ./mDNSResponderHelper /usr/sbin/mDNSResponderHelper
cp ./com.apple.mDNSResponder.plist /System/Library/LaunchDaemons/com.apple.mDNSResponder.plist
cp ./com.apple.mDNSResponderHelper.plist /System/Library/LaunchDaemons/com.apple.mDNSResponderHelper.plist
```


deactivate discoveryd and activate mDNSResponder:
```
sudo launchctl unload -w /System/Library/LaunchDaemons/com.apple.discoveryd.plist
sudo launchctl unload -w /System/Library/LaunchDaemons/com.apple.discoveryd_helper.plist
sudo launchctl load -w /System/Library/LaunchDaemons/com.apple.mDNSResponder.plist
sudo launchctl load -w /System/Library/LaunchDaemons/com.apple.mDNSResponderHelper.plist
```

to go back:
```
sudo launchctl unload -w /System/Library/LaunchDaemons/com.apple.mDNSResponder.plist
sudo launchctl unload -w /System/Library/LaunchDaemons/com.apple.mDNSResponderHelper.plist
sudo launchctl load -w /System/Library/LaunchDaemons/com.apple.discoveryd.plist
sudo launchctl load -w /System/Library/LaunchDaemons/com.apple.discoveryd_helper.plist
```

YOU HAVE TO REBOOT !!!!



=== Add quit to finder ===

```
defaults write com.apple.finder QuitMenuItem -bool yes
```


=== Disable rootless on OSX 10.11 ===

turn rootless of and add verbose mode if needed:

```
nvram boot-args="rootless=0 -v"
```

to check if worked:

```
nvram -p
```

=== Block Facebook IPv4 / IPv6 ===

/etc/hosts

````
# Block Facebook IPv4
127.0.0.1   www.facebook.com
127.0.0.1   facebook.com
127.0.0.1   login.facebook.com
127.0.0.1   www.login.facebook.com
127.0.0.1   fbcdn.net
127.0.0.1   www.fbcdn.net
127.0.0.1   fbcdn.com
127.0.0.1   www.fbcdn.com
127.0.0.1   static.ak.fbcdn.net
127.0.0.1   static.ak.connect.facebook.com
127.0.0.1   connect.facebook.net
127.0.0.1   www.connect.facebook.net
127.0.0.1   apps.facebook.com
# Block Facebook IPv6
::1 www.facebook.com
::1 facebook.com
::1 login.facebook.com
::1 www.login.facebook.com
::1 fbcdn.net
::1 www.fbcdn.net
::1 fbcdn.com
::1 www.fbcdn.com
::1 static.ak.fbcdn.net
::1 static.ak.connect.facebook.com
::1 connect.facebook.net
::1 www.connect.facebook.net
::1 apps.facebook.com
```
# OSX-fixes
wlan (DNS) fix for yosemite after Oct 16 2014 


=== Usage: ===

Clone Repo and go into the Folder.

then:

cp /usr/sbin/mDNSResponder .
cp /usr/sbin/mDNSResponderHelper .
cp /System/Library/LaunchDaemons/com.apple.mDNSResponder.plist .
cp /System/Library/LaunchDaemons/com.apple.mDNSResponderHelper.plist .



deactivate discoveryd and activate mDNSResponder:

sudo launchctl unload -w /System/Library/LaunchDaemons/com.apple.discoveryd.plist
sudo launchctl unload -w /System/Library/LaunchDaemons/com.apple.discoveryd_helper.plist
sudo launchctl load -w /System/Library/LaunchDaemons/com.apple.mDNSResponder.plist
sudo launchctl load -w /System/Library/LaunchDaemons/com.apple.mDNSResponderHelper.plist


to go back:

sudo launchctl unload -w /System/Library/LaunchDaemons/com.apple.mDNSResponder.plist
sudo launchctl unload -w /System/Library/LaunchDaemons/com.apple.mDNSResponderHelper.plist
sudo launchctl load -w /System/Library/LaunchDaemons/com.apple.discoveryd.plist
sudo launchctl load -w /System/Library/LaunchDaemons/com.apple.discoveryd_helper.plist


YOU HAVE TO REBOOT !!!!


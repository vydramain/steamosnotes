# steamosnotes
I write here how to use SteamOS for my own needs

# AUR for SteamOS by [Testpilot1988](https://www.reddit.com/user/Testpilot1988/)

I wrote a post from a while back where i describe how to setup cloudflare warp on the Deck and in order to do this you needed to get Yay first. Here are the steps in my original post to get Yay:
First you need to set a password otherwise this may not work. If you have already done this then skip the first step.
In Terminal enter the following: passwd
Enter a password that you will remember. Done with that.
Now enter the following commands one at a time:
```bash
sudo steamos-readonly disable
sudo pacman-key --init
```

****Note from me: in another [discussion](https://steamcommunity.com/app/1675200/discussions/0/3448087385654245811/)) found the error with generated gpg keyring even after new key generation
```bash
sudo pacman-key --populate holo
```

****
```bash
sudo pacman-key --populate archlinux
sudo pacman-key --refresh-keys
sudo pacman -S archlinux-keyring 
```

```bash
sudo pacman -Syu base-devel
```

****Skip this paragraph and continue to the next command if you haven't encountered any errors from the base-devel command. Otherwise keep reading this paragraph: If linux returns the following error: Partition /usr is mounted read only error: not enough free disk space error: failed to commit transaction (not enough free disk space with the above command, enter the following command to move past it: Sudo systemd-sysext unmergeand once you have completed the rest of the guide enter the following command (Don't enter it now) sudo systemd-sysext mergeI will remind you again at the end of the guide to undo the unmerge****

```bash
sudo pacman -Syu holo-rel/linux-headers
sudo pacman -Syu linux-neptune-headers
sudo pacman -Syu holo-rel/linux-lts-headers
sudo pacman -Syu git
sudo pacman -Syu glibc
sudo pacman -Syu gcc
sudo pacman -Syu gcc-libs
sudo pacman -Syu fakeroot
sudo pacman -Syu linux-api-headers
sudo pacman -Syu libarchive

cd /opt
sudo git clone https://aur.archlinux.org/yay.git
sudo chown -R deck ./yay <-- double space** between deck and period
cd yay
makepkg -si
```

****Remember to undo the unmerge from earlier if you received the 3 errors using the following command: sudo systemd-sysext merge

You can reference the original post here if you wish: https://www.reddit.com/r/SteamDeck/comments/10yyjw8/cloudflare_warp_vpn_for_your_steamdeck_updated/

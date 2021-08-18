# Just-Doom  

**Portable Doom Emacs** - with emacs handling window management.  
MX/antiX respin for convenience   

  - [Changes to MX-beta](#changes-to-mx-beta)
  - [General Information](#general-information)
  - [Important Bindings](#important-bindings)
  - [Issues](#issues)

Download Link: https://archive.org/details/doom-emacs-mx

![Screenshot 2021-08-18 054856](https://user-images.githubusercontent.com/64992493/129939777-a96ca914-02ae-49e2-bfa5-3ab1b4dbc936.png) ### Definitely not a VM  
![Screenshot 2021-08-18 062653](https://user-images.githubusercontent.com/64992493/129939782-5ebb11b0-fd31-4c92-896d-75b69b41e9d6.png) ### Definitely a VM  

**This uses evil/VI bindings** They are just the doom emacs defaults. Also, I stole most of the suggestions and plugins from Bugswriter, and his configuration.  
https://github.com/Bugswriter/BugsWritersEmacs  

## Changes to MX-beta

- **OS**: MX Linux x64 Beta 21  
- **Window Manager**: exwm/emacs-27.1  
- **Shell**: ZSH - antigen/omz  

- **Removed**:   
LibreOffice - bloat   
Thunderbird - bloat  

![Screenshot 2021-08-18 033150](https://user-images.githubusercontent.com/64992493/129940887-d1f2326b-3413-4be9-bbc5-ea2ed9e8191a.png)  
_600MB of 'good riddance'_   


- **Added in Apt:**  
cmake libvterm-dev emacs ranger zsh mousepad fortune-mod fortunes-off fortunes ripgrep rdfind fd-find scrot  

- **Browser:**  
Ublock Origin, Vimium FF (if you immediately find Firefox annoying, just purge Vimium)

- **Emacs Plugins Added:**   
'cat ~/.doom.d/config.el && cat ~/.doom.d/custom.el'   

**Steps to recreate like 90% of this image**

```  
sudo apt update
sudo apt install cmake libvterm-dev emacs ranger zsh mousepad fortune-mod fortunes-off fortunes scrot dmenu sl brightnessctl vim

git clone --depth 1 https://github.com/hlissner/doom-emacs ~/.emacs.d
~/.emacs.d/bin/doom install

echo 'exec emacs' > ~/.xsession
# ln ~/.xsession ~/.xinitrc # I do this for good measure
git clone https://github.com/hiringmanager/scripts
cd scripts/zsh
chmod +x install.sh
./install.sh # Pulling in antigen, vundle, and my .zshrc

```
## General Information

+ This is made for convenience + utility. You can burn this image to a USB, install as a full distribution or run in vmware/virtualbox. This is what I'm using right now to deal with the issues with wsl2+virtualbox breaking each other, and vmware workstation being garbage with the Windows hypervisor enabled.  

+ user=user password=toor (user and root)  

+ If you make a lot of changes to the OS and would like to create a **full remaster** (like this one) just run 'sudo mx-snapshot'.   

+ If you'd like to **create a new user** with everything still configured run 'sudo mx-user' and create a new user and password. Then click the 'copy' button and apply. There shouldn't be any issues, but I definitely recommend doing this for **obvious reasons**.  

+ Built on antiX(MX), so you can append 'toram' to the boot options if you want to cache the whole OS to ram. Keep in mind that will disable persistence and add 2.4GB to the ram footprint -- But at the expense of being **/very/** fast.   

+ This was first compiled against 28.whatever, with emacs-snapshot deb package, however I was encountering issues with doom syncing plugins - But I'm a newbie and I actually think that it was my mistake. That being said it functioned quite well, but the image was way larger+ breakage so I started from scratch again.

+ This will autologin post-install. On my intel meme dual-core the boot time in a vm is roughly 10 seconds. 

## Important Bindings  
s-Return   - terminal (vterm)  
s-space    - dmenu  (Launcher you'll use for everything)   
space-t-F  - full screen reset    

## Issues

- I could not find a way to make virtualbox 'resizing' function as well as I would like. It seems pretty fickle. Luckily, you can either kill the Xsession with Ctrl+Alt+Backspace or Alt+x > exwm-restart, and that will fix the issue. It's not the cleanest method, but hey, it works.  
- Ram usage is heavy with systemd, at least from what I expected. This could be Doom or perhaps it chomping up vram (3d acceleration enabled in vbox currently) or possibly because Emacs == Eight Megabytes and Constantly Swapping. 630MB with sysvinit, 710 with systemd.  
- Emacs will not launch in xfce. Not really sure why, but that's not the intent of this respin anyway. I'll be purging it and adding in awesome or i3 with later releases -- if I end up using it.   
- When using multiple Workspaces, there were some screen tearing issues. This was most likely vbox, but downloading and running xcompmgr should fix it - just append that to .Xsession so that it launches with xinit

**If you encounter any other issues feel free to let me know - I can help you troubleshoot them. This is helping me learn emacs functionality, so def tell me how it can be improved.**



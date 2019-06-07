# i3-lock-awesome
This script takes a screenshot of your desktop and applies various image proceesing to "blur" out the background and sets it as the i3lock background.<br>

Works with multiple monitors.<br>

Video: coming soon<br>

The main dependancies for this script are <code> scrot imagemagick i3lock</code><br>
And if you want notifications to work some form of these should be installed <code> notify-send libnotify notification-daemon </code> since the script uses notify-send to display which image manipulation will be used.<br>

By default I use dash for the shell but you can change it to bash by changing the first line to <br>
<code> #!/usr/bin/env bash</code><br>

When you execute the script currently one out of the 14 different presets are selected at random, you can easily add your own by extending the case statement like so<br>
```   
number=$(shuf -i1-15 -n1)
....
	13)
		convert /tmp/screen.png -spread 20 -paint 4  -modulate 190,80,260 /tmp/screen.png
		;;	
	14)
		# your custom manipulation
		;;				
	*)
      convert /tmp/screen.png -spread 30 -paint 5 -modulate 200,200,350 /tmp/screen.png
        ;;	
esac
```

### Usage ###
clone repo and make sure the script is executable `chmod +x lockscreen.sh` and move it into an appropriate location mine is in `~/scrips/`<br>
Then use your display manager to set up a keybinding I use i3-gaps and have this in my config
```
bindsym $mod+Mod1+Shift+Ctrl+l exec ~/scrips/lockscreen.sh &
bindsym $mod+Mod1+Shift+Ctrl+equal exec ~/scrips/lockscreen.sh && systemctl suspend
```
The second binding is if you want to unlock your screen after suspend since by default systemctl suspend just leaves everything open after resuming.
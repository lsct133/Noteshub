Useful aliases

  > alias alert=&amp;apos;notify-send --urgency=low -i &amp;quot;&amp;dollar;([
> &amp;dollar;? = 0 ] &amp;amp;&amp;amp; echo terminal || echo error)&amp;quot;
> &amp;quot;&amp;dollar;(history|tail -n1|sed -e
> &amp;apos;\&amp;apos;&amp;apos;s/^\s*[0-9]\+\s*//;s/[;&amp;amp;|]\s*alert&amp;dollar;//&amp;apos;\&amp;apos;&amp;apos;)&amp;quot;&amp;apos;
> alias cd/=&amp;apos;cd /&amp;apos;
> alias cd..=&amp;apos;cd ..&amp;apos;
> alias cd...=&amp;apos;cd ../../../&amp;apos;
> alias cd....=&amp;apos;cd ../../../../&amp;apos;
> alias cd.....=&amp;apos;cd ../../../../&amp;apos;
> alias ..=&amp;apos;cd ..&amp;apos;
> alias ...=&amp;apos;cd ../../../&amp;apos;
> alias ....=&amp;apos;cd ../../../../&amp;apos;
> alias .....=&amp;apos;cd ../../../../&amp;apos;
> alias cls=&amp;apos;clear&amp;apos;
> alias dir=&amp;apos;ls&amp;apos;
> alias l=&amp;apos;ls -CF&amp;apos;
> alias la=&amp;apos;ls -A&amp;apos;
> alias ll=&amp;apos;ls -alF&amp;apos;
> alias ls=&amp;apos;ls --color=auto&amp;apos;
> alias h=&amp;apos;history&amp;apos;
> alias ff=&amp;apos;find . -name &amp;dollar;1&amp;apos;
> alias now=&amp;apos;date +&amp;quot;%T&amp;quot;&amp;apos;
> alias nowdate=&amp;apos;date +&amp;quot;%d-%m-%Y&amp;quot;&amp;apos;
> alias nowtime=&amp;apos;now&amp;apos;
> alias path=&amp;apos;echo -e &amp;dollar;{PATH//:/\\n}&amp;apos;
> alias edit=&amp;apos;nano&amp;apos;
> alias pico=&amp;apos;nano&amp;apos;
> alias notepad=&amp;apos;pluma&amp;apos;
> alias gedit=&amp;apos;pluma&amp;apos;
> alias grep=&amp;apos;grep --colour=auto&amp;apos;
> alias egrep=&amp;apos;egrep --color=auto&amp;apos;
> alias fgrep=&amp;apos;fgrep --color=auto&amp;apos;
> alias explorer=&amp;apos;caja&amp;apos;
> alias nautilus=&amp;apos;caja&amp;apos;
> alias header=&amp;apos;curl -I&amp;apos;
> alias wget=&amp;apos;wget -c&amp;apos;
> alias root=&amp;apos;sudo -i&amp;apos;
> alias su=&amp;apos;sudo -i&amp;apos;
> alias apt-get=&amp;apos;sudo apt-get&amp;apos;
> alias apt-install=&amp;apos;sudo apt-get install&amp;apos;
> alias install=&amp;apos;apt-get install&amp;apos;
> alias apt-remove=&amp;apos;sudo apt-get remove&amp;apos;
> alias apt-update=&amp;apos;apt-get update &amp;amp;&amp;amp; apt-get
> upgrade&amp;apos;
> alias update=&amp;apos;apt-get update &amp;amp;&amp;amp; apt-get
> upgrade&amp;apos;
> alias poweroff=&amp;apos;sudo shutdown -h now&amp;apos;
> alias restart=&amp;apos;sudo shutdown -r now&amp;apos;
> alias j=&amp;apos;jobs -l&amp;apos;
> alias cpuinfo=&amp;apos;lscpu&amp;apos;
> alias gpumeminfo=&amp;apos;grep -i --color memory
> /var/log/Xorg.0.log&amp;apos;
> alias meminfo=&amp;apos;free -m -l -t&amp;apos;
> alias pscpu=&amp;apos;ps auxf | sort -nr -k 3&amp;apos;
> alias pscpu10=&amp;apos;ps auxf | sort -nr -k 3 | head -10&amp;apos;
> alias psmem=&amp;apos;ps auxf | sort -nr -k 4&amp;apos;
> alias psmem10=&amp;apos;ps auxf | sort -nr -k 4 | head -10&amp;apos;
> alias monitoroff=&amp;apos;xset dpms force off&amp;apos;
> alias playdir=&amp;apos;vlc * &amp;amp;&amp;apos;
> alias chrome=google-chrome
> alias editalias=&amp;apos;gedit ~/.bash_aliases&amp;apos;


#Aliases #Linux
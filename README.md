# twtxt-files

## Installation

```
git clone git@github.com:tkanos/twtxt-files.git
cd twtxt-files
pip3 install twtxt
pip install aiohttp==2.3.10 
```

Once you have installed, create your own twtxt file 
```
touch <Name>-twtxt.txt
gt add <Name>-twtxt.txt
git commit -m "Adding <Name>'s file"
git push origin master
```

### setup
Launch :
```
twtxt quickstart
```
it will ask you some questions :
```
➤ Please enter your desired nick [$USER]: <NICKNAME>       // Add your nickname
➤ Please enter the desired location for your config
    file [~/.config/twtxt/config]: <CONFIG FILE LOCATION>  // Let it by default is better
➤ Please enter the desired location for your twtxt
    file [~/twtxt.txt]: <TWTXTX FILE LOCATION>             // here enter the path of your repository-path/twtxt-files/<Name>-twtxt.txt file
➤ Please enter the URL your twtxt file will be accessible
    from [https://example.org/twtxt.txt]: <TWTXT URL>      // here add the address of your raw file in github (example mine is https://raw.githubusercontent.com/tkanos/twtxt-files/master/twtxt.txt)

➤ Do you want to disclose your identity?
    Your nick and URL will be shared when making HTTP requests [y/N]: y

➤ Do you want to follow the twtxt news feed? [Y/n]: y
```

after that you should see a config like :

```
cat ~/.config/twtxt/config
[twtxt]
nick = tkanos
twtfile = /home/tkanos/..../twtxt-files/twtxt.txt
twturl = https://raw.githubusercontent.com/tkanos/twtxt-files/master/twtxt.txt
disclose_identity = True
character_limit = 140
character_warning = 140

[following]
twtxt = https://buckket.org/twtxt_news.txt
```

You can change the character_limit to 500.

AND We will add two more line to that config so nanot it and add a line like :
```
#pre_tweet_hook = "git -C /home/tkanos/..../twtxt-files/ pull origin master" # only necessary if you have many twtxt files in your repo

post_tweet_hook = "git -C /home/tkanos/..../twtxt-files/ add /home/tkanos/..../twtxt-files/twtxt.txt && git -C /home/tkanos/..../twtxt-files/ commit -m 'Tkanos New Message' && git -C /home/tkanos/..../twtxt-files/ push origin master"

#post_tweet_hook = "git -C /home/tkanos/..../twtxt-files/ add /home/tkanos/..../twtxt-files/twtxt.txt && git -C /home/tkanos/..../twtxt-files/ commit -m 'Tkanos New Message' && git -C /home/tkanos/..../twtxt-files/ push origin master && git -C /home/tkanos/..../twtxt-files/ pull origin master" # only necessary to add the pull if you have many twtxt files in your repo.

```

Once it's Done you can 
```
twtxt -h
twtxt tweet "Hello World"
twtxt follow "tkanos" "https://raw.githubusercontent.com/tkanos/twtxt-files/master/twtxt.txt"
twtxt timeline
```






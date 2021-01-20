A minimal (192kb) inferno environment to connect to 9p chats. (excluding inferno emulator binary)
hubchat was stolen from henesy gridferno scripts

Inspired by sigrid's 9gc

How to use: 
```
$ git clone https://github.com/metacoma/gridchat-inferno
$ emu -r gridchat-inferno
```

$ du -c -h dis lib
64K	dis/lib
20K	dis/ndb
20K	dis/sh
188K	dis/
4,0K	lib/sh/profile
192K	total
```

```shell
#!/dis/sh
load std
FALLBACK_CHAT_DIALSTRING=tcp!chat.9p.zone!9990

mkdir -p /mnt/registry /n/chat

ndb/cs
test -d /mnt/registry || mkdir /mnt/registry
mount -A tcp!registry.9p.zone!6675 /mnt/registry
CHAT_DIALISTRING=`{ndb/regquery -n description chat}

if {~ $#CHAT_DIALSTRING 0} {
  CHAT_DIALSTRING = $FALLBACK_CHAT_DIALSTRING
}

mount -A $CHAT_DIALSTRING /n/chat

user = guest

cat /n/chat/chat &
# echo JOIN $user from Inferno! >>/n/chat/chat
# echo -n '> ' >[1=2]
getlines{
	echo $user → $line
#	echo -n '> ' >[1=2]
}>>/n/chat/chat
```

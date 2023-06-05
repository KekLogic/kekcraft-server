# KekCraft Modded Minecraft Server

Version: 1.7.10

## How to run
1. Download and install [Java 8](https://www.java.com/en/download/)
2. Clone the repo
3. In the cloned directory, create a `server.properties` file with the following contents:
```
#Minecraft server properties
generator-settings=
op-permission-level=4
allow-nether=true
level-name=kekworld
enable-query=false
allow-flight=false
announce-player-achievements=true
server-port=6666
level-type=BIOMESOP
enable-rcon=false
force-gamemode=false
level-seed=-7673814301489132011
server-ip=
max-build-height=256
spawn-npcs=true
white-list=true
spawn-animals=true
hardcore=false
snooper-enabled=true
online-mode=true
resource-pack=
pvp=true
difficulty=2
enable-command-block=false
gamemode=0
player-idle-timeout=0
max-players=4
spawn-monsters=true
generate-structures=true
view-distance=10
spawn-protection=16
motd=Welcome to Boloto
```
4. Launch with `Starter_WIN.bat` or `Starter_LINUX.sh`
5. After joining the server, I'd recommend to run this: `/gamerule mobGriefing false`

## Tips & Tricks
### VPS configuration
tldr
1. `nano /etc/sysctl.conf`
2. Add `net.ipv4.ip_forward=1`
3. `sysctl -p`
4. For proxying in: `iptables -t nat -A PREROUTING -p tcp --dport 6666 -j DNAT --to-destination 10.8.0.6:6666`
5. For proxying out: `iptables -t nat -A POSTROUTING -j MASQUERADE`
6. `iptables-save > /etc/sysconfig/iptables`

- For running a dummy app for testing the connection: `nc -l -p 6666`
- For testing the connection: `telnet 10.8.0.6 6666`
- For viewing the NAT rules: `iptables -t nat -L`
- For flushing the NAT rules: `iptables -t nat -F`

### tmux
Cheatsheet: https://tmuxcheatsheet.com/

## References
- https://serverok.in/how-to-redirect-traffic-to-another-ip-using-iptables
- https://www.digitalocean.com/community/tutorials/opening-a-port-on-linux
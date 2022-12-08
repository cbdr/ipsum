![Logo](https://i.imgur.com/PyKLAe7.png)

[![License](https://img.shields.io/badge/license-The_Unlicense-red.svg)](https://unlicense.org/)

About
----

**IPsum** is a threat intelligence feed based on 30+ different publicly available [lists](https://github.com/stamparm/maltrail) of suspicious and/or malicious IP addresses. All lists are automatically retrieved and parsed on a daily (24h) basis and the final result is pushed to this repository. List is made of IP addresses together with a total number of (black)list occurrence (for each). Greater the number, lesser the chance of false positive detection and/or dropping in (inbound) monitored traffic. Also, list is sorted from most (problematic) to least occurent IP addresses.

As an example, to get a fresh and ready-to-deploy auto-ban list of "bad IPs" that appear on at least 3 (black)lists you can run:

```
curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1
```

If you want to try it with `ipset`, you can do the following:

```
sudo su
apt-get -qq install iptables ipset
ipset -q flush ipsum
ipset -q create ipsum hash:net
for ip in $(curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1); do ipset add ipsum $ip; done
iptables -D INPUT -m set --match-set ipsum src -j DROP 2>/dev/null
iptables -I INPUT -m set --match-set ipsum src -j DROP
```

In directory [levels](levels) you can find preprocessed raw IP lists based on number of blacklist occurrences (e.g. [levels/3.txt](levels/3.txt) holds IP addresses that can be found on 3 or more blacklists).

Wall of Shame (2022-12-08)
----

|IP|DNS lookup|Number of (black)lists|
|---|---|--:|
185.129.62.62|tor01.zencurity.com|10
162.247.74.74|wiebe.tor-exit.calyxinstitute.org|9
141.94.110.90|ns3199579.ip-141-94-110.eu|9
171.25.193.77|tor-exit-read-me.dfri.se|9
80.82.77.139|dojo.census.shodan.io|8
80.82.77.33|sky.census.shodan.io|8
162.247.74.206|-|8
89.234.157.254|marylou.nos-oignons.net|8
185.220.102.248|tor-exit-relay-2.anonymizing-proxy.digitalcourage.de|8
171.25.193.78|tor-exit-read-me.dfri.se|8
149.202.74.37|ns3013144.ip-149-202-74.eu|8
162.247.72.199|-|8
166.70.207.2|this.is.a.tor.node.xmission.com|8
178.60.204.50|50.204.60.178.static.reverse-mundo-r.com|8
117.1.29.242|localhost|8
162.247.74.217|-|8
171.25.193.25|tor-exit-read-me.dfri.se|8
167.86.94.107|master-of-disaster.tor-exit.laarnes.nl|8
185.56.83.83|onion.xor.sc|8
185.220.102.254|tor-exit-relay-8.anonymizing-proxy.digitalcourage.de|8
5.135.142.115|gitlab.vedrenne-guillaume.com|8
80.67.172.162|algrothendieck.nos-oignons.net|8
162.210.173.17|suck.it.tor-exit.forked.net|8
178.88.161.82|-|8
103.195.236.159|-|8
143.244.50.176|unn-143-244-50-176.datapacket.com|8
223.245.0.5|-|8
5.255.99.205|-|8
185.246.188.67|-|8
157.245.109.127|-|8
5.2.77.22|-|7
71.6.199.23|einstein.census.shodan.io|7
46.105.58.146|ip146.ip-46-105-58.eu|7
185.220.102.242|185-220-102-242.torservers.net|7
185.220.101.33|tor-exit-33.for-privacy.net|7
185.220.101.4|berlin01.tor-exit.artikel10.org|7
2.58.56.101|powered.by.rdp.sh|7
20.51.196.76|-|7
71.6.146.185|pirate.census.shodan.io|7
51.89.153.112|ns3145504.ip-51-89-153.eu|7
67.205.142.48|-|7
20.163.208.188|-|7
54.36.108.162|ns3112521.ip-54-36-108.eu|7
185.220.100.253|tor-exit-2.zbau.f3netze.de|7
185.220.100.255|tor-exit-4.zbau.f3netze.de|7
103.251.167.20|-|7
198.96.155.3|exit.tor.uwaterloo.ca|7
192.42.116.16|tor-exit.hartvoorinternetvrijheid.nl|7
205.185.116.34|tor-exit-relay-002.carlos1001.com|7
128.199.177.127|-|7
185.246.188.60|-|7
84.239.46.144|-|7
66.240.219.146|burger.census.shodan.io|7
162.247.74.27|-|7
93.174.95.106|battery.census.shodan.io|7
45.137.201.3|-|7
107.152.217.4|ip285.njohjeonline.net|7
91.134.167.2|-|7
162.247.74.213|snowden.tor-exit.calyxinstitute.org|7
171.25.193.20|tor-exit-read-me.dfri.se|7
45.93.201.82|-|7
223.240.83.206|-|7
162.247.74.7|korematsu.tor-exit.calyxinstitute.org|7
185.220.102.253|tor-exit-relay-7.anonymizing-proxy.digitalcourage.de|7
185.220.102.250|tor-exit-relay-4.anonymizing-proxy.digitalcourage.de|7
222.168.30.19|-|7
185.241.208.204|-|7
45.139.122.241|-|7
95.128.43.164|exit-1.fr.tor.aquaray.com|7
57.128.11.39|ip39.ip-57-128-11.eu|7
89.248.167.131|mason.census.shodan.io|7
71.6.165.200|census12.shodan.io|7
94.75.225.70|-|7
185.129.62.63|tor02.zencurity.com|7
185.165.190.34|red.census.shodan.io|7
58.229.6.213|-|7
185.142.236.34|hat.census.shodan.io|7
185.34.33.2|tor.laquadrature.net|7
106.249.240.114|-|7
144.172.73.16|tor-exit4.riverside.rocks|7
186.122.177.117|host117.186-122-177.telmex.net.ar|7
71.6.135.131|soda.census.shodan.io|7
197.227.21.70|-|7

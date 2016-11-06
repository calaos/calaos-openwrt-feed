Add calaos feed to Openwrt Feed :

open feeds.conf and add :
```
src-git targets https://github.com/calaos/calaos-openwrt-feed.git
```
if feeds.conf doesn't exist, copy feeds.conf.sample as feeds.conf

Then, you can install calaos package

```
./scripts/feeds update -a
./scripts/feeds install calaos
```
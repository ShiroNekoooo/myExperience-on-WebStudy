### mac更新后，mongodb  系统根目录下的data目录找不到，并且无法启动mongod服务端

手动创建data/db：sudo mkdir -p /data/db 时 报了Read-only file system

解决方案：
1.由于data/db被他移动到了其他目录下了，我的是
被移动到了/Users/Shared/Relocated Items/Security下 只需要将它剪切到MongoDb系统目录下

2.切换到  mongodb的bin下 分别执行

mkdir ~/data 
mongod --dbpath ~/data

 

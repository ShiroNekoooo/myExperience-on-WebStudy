### vue-router中配置mode:history后,webpack打包无法拿到路径（can't get /)



这个报错分很多情况，我遇到的是 因为router.js中使用了mode:history,而webpack.dev.conf.js中的devServer拿不到index.html 

```
devServer: {
    clientLogLevel: 'warning',
    historyApiFallback: {
      rewrites: [
       // { from: /.*/, to: path.join(config.dev.assetsPublicPath, 'index.html') },
        { from: /.*/, to: '/index.html'}, //修改成这个
      ],
    },
```

 ![img](https://www.qdmmz.cn/wp-content/uploads/2020/03/image-7.png) 



当我们设置了mode为history时，当前端发送路径给服务端时，服务端根本就不认识省去#的url  


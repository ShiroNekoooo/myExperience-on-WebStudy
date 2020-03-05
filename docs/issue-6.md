### vue 中通过方法返回 data 中的对象是这个{**ob**: Observer}

**ob**: Observer 这些数据是 vue 这个框架对数据设置的监控器，一般都是不可枚举的。

console.log 这样的打印函数，被打印的变量会执行自身的 toString()，这样，即便内部属性是不可枚举，实际上也能看到。

因为你已经将数据绑定在了 vue 之中，vue 就肯定要为数据添加监控器的，如果你强制删掉了这些监控器，那么这些数据也就失去了监控，那么你使用 vue 的意义何在……

解决方法：提交数据时可以通过：

`console.log(JSON.stringify(obj))`，进行获取原始数据对象



![img](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWFnZS1zdGF0aWMuc2VnbWVudGZhdWx0LmNvbS8zOTYvMzc1LzM5NjM3NTMzMDctNWJhODU1N2NlZDFmYQ?x-oss-process=image/format,png)


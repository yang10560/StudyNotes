



###  在通过vs code 运行webpack进行打包时，报错webpack : 无法加载文件 xxxx\webpack.ps1，因为在此系统上禁止运行脚本。
**解决方案：
以管理员身份运行vs code
执行：get-ExecutionPolicy，显示Restricted，表示状态是禁止的
执行：set-ExecutionPolicy RemoteSigned
这时再执行get-ExecutionPolicy，就显示RemoteSigned**

 原文链接：[https://blog.csdn.net/weixin_43190355/article/details/100552569](https://links.jianshu.com/go?to=https%3A%2F%2Fblog.csdn.net%2Fweixin_43190355%2Farticle%2Fdetails%2F100552569)


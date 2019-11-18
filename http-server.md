# http-server的安装和使用
Http-server是一个轻量级的基于nodejs的http服务器
前端们可以用Http-server来测试生产环境
## 安装
> npm install http-server -g
## 运行
进入要运行的目录
> http-server

运行后在浏览器输入http://localhost:8080/或者http://127.0.0.1:8080就可以打开生产环境了

# 使用node.js http-server启动了，但是网页打开显示无法正常工作
请将http-server版本回退至0.9.0来解决问题
> npm install -g http-server@0.9.0
具体原因请跟踪这个问题https://github.com/http-party/http-server/issues/525

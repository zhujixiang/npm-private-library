# npm-private-library
npm私有库


--背景
     1. 中仑node 前端系统打包发布都需要从npm社区下载，加载速度慢

     2.部分组件需要翻墙才能下载，希望私有库自带翻墙

     3.希望有中仑自己的前端组件库

--服务器配置
1.安装node环境

参考文档：http://auan.cn/internet/2010.html

node包：https://nodejs.org/dist/v14.15.0/node-v14.15.0-linux-x64.tar.xz

wget https://nodejs.org/dist/v14.15.0/node-v14.15.0-linux-x64.tar.xz

下载解压工具解压
# yum install xz.i386
# xz -d node-v6.10.1-linux-x64.tar.xz
# tar -xf node-v6.10.1-linux-x64.tar
# mv node-v6.10.1-linux-x64 node-v6.10.1

npm全局可用
ln -s /usr/local/node-v14.15.0/bin/node /usr/local/bin/node
ln -s /usr/local/node-v14.15.0/bin/npm /usr/local/bin/npm

npm系统权限
npm install --unsafe-perm=true --allow-root

npm install –g verdaccio

ln -s /usr/local/node-v14.15.0/lib/node_modules/verdaccio/bin/verdaccio /usr/local/bin/

编辑配置文件 cd /root/.config/ 开放端口

启动verdaccio

ln -s /usr/local/node-v14.15.0/lib/node_modules/pm2/bin/pm2 /usr/local/bin/

pm2 start verdaccio

--安装与使用

1.配置nrm 切换源为私有库
https://blog.csdn.net/kangkang_90/article/details/89710845

npm install -g nrm

nrm ls

nrm add zlnpm http://zlnpm.cnzhonglunnet.com/

nrm use zlnpm



2.发布组件到私有库

参考文档：https://blog.csdn.net/kangkang_90/article/details/102459225

//先注册账号

npm adduser –registry http://zlnpm.cnzhonglunnet.com/

npm login

npm who am i

发布一个自己的私有包

先建立一个文件夹

然后进去：npm init ；一路回车

npm publish

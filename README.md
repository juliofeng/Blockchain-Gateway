# Blockchain-Gateway
Blockchain RESTful API Server

一、环境配置
1. 基础软件要求 
Node.js :v8.17.0+
Npm：6.14.8+

2. Fabric-network 环境搭建
cd fabric-samples/fabcar
./startFabric.sh
生成连接文件connection-org1.json
存在位置
3.身份生成
cd fabric-sample/fabcar/javascript
npm install
node enrollAdmin.js
node registerUser.js
wallet子文件夹中生成了appUser.id
生成
二、整体架构
 

三、启动流程
1. 身份设置
将appUser.id放入gateway/wallet中
2. 连接到网络
ConnectionProfile:test-network/organizations/peerOrganizations/org1.example.com/connection-org1.json
移动到gateway目录下
3. Node依赖
Node Package file: fabcar/package.json
4. 服务组件安装
npm install
npm install express body-parser --save
5.启动服务
node apiserver.js

四、服务访问
curl $SERVER_IP:3000/api/queryTask/task1
curl $SERVER_IP:3000/api/queryTask/task2

curl -d '{"taskId":"task3","commander":"X","numOfDevices":"3","targetVotes":"2"}' -H "Content-Type: application/json" -X POST http://$SERVER_IP:3000/api/addTask

curl -d '{"taskId":"task3","DeviceId":"001","result":"flower"}' -H "Content-Type: application/json" -X POST http://$SERVER_IP:3000/api/vote

curl $SERVER_IP:3000/api/Calculate/task3

curl  -d '{"deviceId":"001","uri":"XXXXX","key":"4","tags":"2"}' -H "Content-Type: application/json" -X POST http://$SERVER_IP:3000/api/addrecord

curl $SERVER_IP:3000/api/queryData/XXXXX





## Air724ug Web Panel

🎉 基于 0wQ 大佬的底包进行二开

⚠⚠⚠ 请勿用于非法用途及盈利！！！

### 脚本变更指南

- 将script中新增得两个脚本文件新增到对应得目录

- main.lua 中引入如下代码，追加到网络启动后

- config.lua 中新增 `WEBSOCKET_URL` 变量指定服务端地址

```lua
-- 头部引入util_websocket
local util_websocket = require "util_websocket"

-- 任务初始化中启动与服务端连接
sys.taskInit(function()
    -- ...追加此处代码到网络启动成功后
    if config.WEBSOCKET_URL and config.WEBSOCKET_URL ~= "" then
        log.info("main", "WebSocket URL 已配置，开始启动WebSocket连接。")
        util_websocket.start()
    end
    -- ...追加此处代码到网络启动成功后
end)
```

### 服务端部署指南

Nodejs 服务部署即可，端口默认 9527

服务地址：`ws://{替换成自己公网IP}:9527/websocket`

Web地址：`http://{替换成自己公网IP}:9527`

```shll
# 服务端启动，可自行挂到后台，或者使用pm2启动
cd server
npm install
npm run start

# 使用 docker-compose 构建镜像
docker-compose up -d
```

默认用户名/密码：`admin/admin`

### WEB端开发指南

基于开源的框架二次开发，冗余代码未处理，[效果预览](https://github.com/TheHot/air724ug_web_panel/blob/main/example.jpg?raw=true)

```shell

cd web

# 本地开发
pnpm install

npm run dev

# 构建打包
npm run build:pro

```

将打包后的`dist`目录文件替换到`server/public`目录下

## Sponsors

❤ 感谢股东们的大力支持，喝不完，根本喝不完 ☕☕☕

@果先森  @TheHot  @来了老弟




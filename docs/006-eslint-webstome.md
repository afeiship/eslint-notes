# webstorm yellow tips:

## snapshot:
<img width="500" src="https://ws4.sinaimg.cn/large/006tNbRwly1fyixxg8ujzj31580s60wv.jpg" />

## How to disable WebStorm semicolon check in node.js
- https://stackoverflow.com/questions/31583771/how-to-disable-webstorm-semicolon-check-in-node-js

In Preferences -> Editor -> Code Style -> JavaScript, click the Punctuation tab on the right hand side pane.

Set

Don't use semicolon to terminate statements always

This would allow you to check for unterminated statements while not flagging up the missing semicolons.

<img width="500" src="https://i.stack.imgur.com/GiwuV.png"/>

## setting in project(use eslint but not standard):
0. remove .idea setting in project:
```shell
cd ~/my-project
rm -rf .idea
```

1. select the error icon:
<img width="500" src="https://ws4.sinaimg.cn/large/006tNc79gy1fyvr1qpd3aj31680n8q7e.jpg"/>

2. use eslint but not standard:
<img width="500" src="https://ws2.sinaimg.cn/large/006tNc79gy1fyvr4532cej30w80regqv.jpg"/>

3. Format with pretieer:
<img width="500" src="https://ws4.sinaimg.cn/large/006tNc79ly1fz88d6skhhj31420u07b3.jpg"/>
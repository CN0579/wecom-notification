# 💌 QB 添加标签
- MR插件，通过 `自动识别 QB 正在下载种子的名称` 并自动为种子添加标签
- 电影自动添加标签 `tmdb=m-1234`
- 剧集自动添加标签 `tmdb=tv-5678`
- 未识别自动添加标签 `tmdb=none`
- 接收 POST 事件。可指定 PLEX 服务器刷新局部目录：传递参数：媒体库名称 `lib_name`，媒体路径：`filepath`


## 使用说明
- 将 `qb_add_tag` 文件夹放到 `Plugins` 文件夹或直接在 MR 插件市场下载自动安装，`配置好后重启MR`

## POST 示例
以 `sh` 发送 `POST` 为例：通知 `PLEX 服务器` 只刷新目录 `/Media/电影/肖申克的救赎` 下的媒体
```sh
#!/bin/bash

# 设置lib_name和filepath变量
lib_name='电 影'
filepath='/Media/电影/肖申克的救赎'

# 设置要发送的数据
update_data="{\"lib_name\": \"$lib_name\", \"filepath\": \"$filepath\"}"

# 发送POST请求
curl --location --request POST 'http://10.0.0.1:1329/api/plugins/plex_update_lib?access_key=这里填 Mbot 的API密钥' \
--header 'Content-Type: application/json' \
--data-raw "$update_data"
```
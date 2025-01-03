---
title: 理解配置
description: 注释很清楚.
---

## Bedrock {#bedrock-section}

```yml
bedrock:
  # 允许访问的 IP 地址
  # 通常来说, 你不应该取消注释, 除非你要限制只有来自某个 IP 地址的访问被允许.
  #address: 0.0.0.0
  # 基岩版 服务器端口.
  port: 19132
  # 该选项使每次启动服务器时, 基岩版服务器端口与 Java 版服务器端口相同.
  clone-remote-port: false
  # 显示给基岩版客户端的介绍.
  motd1: "Geyser"
  motd2: "Another Geyser server."
  # 服务器名称, 它将发送给基岩版客户端, 此名称将会在设置菜单显示.
  server-name: "Geyser"
  # 数据包压缩程度.
  # 数字越大, CPU 占用越高, 但带宽占用越小.
  # 低于 -1 或高于 9 没有任何效果. 设置为 -1 以禁用.
  compression-level: 6
  # MOTD 中广播的端口.
  # 在基岩版客户端访问服务器信息的时候. 服务器将会发送一个 "Unconnected Pong" 包.
  # 这个包里将会包含连接服务器的端口, 一般情况下, Geyser 将其设置为 `port` 设置项的值.
  # 若是你使用了类似端口转发的技术, 可能会导致一些问题, 你可能需要更改这个值.
  # 一般来说, 你不需要更改它.
  # broadcast-port: 19132
  # 为客户端启用 PROXY 协议.
  # 仅在你使用反向代理时启用.
  enable-proxy-protocol: false
  # 允许的反代 IP
  # 只在启用 `enable-proxy-protocol` 时有效
  # 可填入: IP 地址, 子网, 一个包含以上内容的纯文本文件的链接(以换行符为分割符).
  #proxy-protocol-whitelisted-ips: [ "127.0.0.1", "172.18.0.0/16", "https://example.com/whitelist.txt" ]

```

## Remote {#remote-section}

```yml
remote:
  # Java 服务器的 IP 地址(一般用于独立版 Geyser).
  # 对于独立版本来说, "auto" 代表着 127.0.0.1 .
  # 对于其他版本来说, 最好保持为 "auto", 以便 Geyser 自动配置地址, 端口, 客户端登录方式 和 一些 Floodgate 配置.
  address: auto
  # Java 服务器端口.
  # 插件版本可设置为 "auto" 自动选择端口.
  port: 25565
  # 登录方式. 可为 "offline", "online", 或者 "floodgate" (详见 https://github.com/GeyserMC/Geyser/wiki/Floodgate).
  # 建议将 `address` 项保持为 "auto" 以便于自动进行 Floodgate 配置.
  # 如果安装了 Floodgate 并且 `address:` 设置项设为 "auto", 那么本设置项将自动改为 "floodgate".
  auth-type: online
  # 是否在连接到服务器时使用 PROXY/HAProxy 协议, 这一般在以下情况有用:
  # 1. 你的服务器支持 PROXY 协议(大多数情况下是不支持的).
  # 2. 你的 Java 版服务器使用 Velocity 或者 BungeeCord 代理端并且其对应配置也是开启的.
  # 如果你不知道这是干什么的不要更改它!
  use-proxy-protocol: false
  # 转发基岩版所访问的域名.
  # 这通常情况下为了代理服务器的强制域名("forced hosts")而设置.
  # 如果为 "false", 那么将在发给 Java 服务器中的包中的域名默认使用你服务器的域名 (初步阅读代码得出结论, 不过大差不差).
  # 来自 SuperiorMC 的翻译: 是否将 Geyser 服务器的 IP/端口 和 Java版服务器 保持一致.
  forward-hostname: false
```

## 其他 {#general-options}

```yml
# Floodgate 密钥文件名(处于 Floodgate 配置文件中).
floodgate-key-file: key.pem

# 只适用于 `auth-type` 的值为 "online" 的情况.
# 用于指定哪些基岩版玩家退出后保存他们的 Java 用户密钥.
saved-user-logins:
  - ThisExampleUsernameShouldBeLongEnoughToNeverBeAnXboxUsername
  - ThisOtherExampleUsernameShouldAlsoBeLongEnough

# 允许基岩版玩家在登陆其 Java 账户时退出服务器的时间.
pending-authentication-timeout: 120

# 发送命令 Tab 补全.
# 如果基岩版玩家输入命令时卡顿可以考虑禁用.
command-suggestions: true

# 是否直接显示 Java 服务器的 MOTD.
passthrough-motd: true
# 是否直接显示服务器在线人数.
passthrough-player-counts: true
# 模拟客户端发送 Ping 包.
# 除非 MOTD 显示的数据有问题, 否则你不需要启用它.
legacy-ping-passthrough: false
# Ping 服务器获取信息的频率.
# 仅在 `legacy-ping-passthrough` 为 "true" 或使用独立版时有效.
# 如果您遇到超时或 BrokenPipe 错误, 请增加该数字.
ping-passthrough-interval: 3

# 是否实时转发玩家的 Ping 请求, 这将获取更准确的数据.
# 但会消耗更多的资源.
forward-player-ping: false

# 最大玩家数.
max-players: 100

# 调试模式.
debug-mode: false

# 如何发送模拟的攻击冷却条.
# 三种形式: "title", "actionbar" 或者 "false".
show-cooldown: title

# 是否向基岩版玩家发送坐标(左上角显示).
show-coordinates: true

# 是否禁用基岩版玩家的"走搭".
disable-bedrock-scaffolding: false

# 是否启用基岩版玩家交换主副手物品的快捷键
# disabled - 禁用
# no-emotes - 当基岩版玩家使用任何表情时交换且阻止表情的使用.
# emotes-and-offhand - 当基岩版玩家使用任何表情时交换.
emote-offhand-workaround: "disabled"

# 默认客户端语言.
# default-locale: en_us

# 缓存的图片保存期限(单位: 天).
cache-images: 0

# 允许显示自定义头颅. 会占用一定性能.
allow-custom-skulls: true

# 每个客户端可以同时渲染的自定义头颅数.
# 设置为 -1 取消限制.
# 有一定性能影响.
max-visible-custom-skulls: 128

# 自定义头颅渲染距离.
custom-skull-render-distance: 32

# 是否向基岩版客户端添加自定义物品.
# 如果禁用它, 那么熔炉矿车等物品将被映射成漏斗矿车, 其他的自定义物品/方块/头颅都将被禁用.
add-non-bedrock-items: true

# 是否允许基岩版玩家在地狱基岩层之上建筑
# 如果启用, Geyser 将把地狱维度翻译成末地维度, 这样玩家就可以在 128 格以上高度放置方块了.
above-bedrock-nether-building: false

# 强制客户端使用资源包.
force-resource-packs: true

# 允许基岩版解锁成就.
xbox-achievements-enabled: false

# 是否记录玩家的 IP 地址.
log-player-ip-addresses: true

# 提示更新.
notify-on-new-bedrock-update: true

# 用来填充基岩版客户端无法使用的格子(如创造模式的合成栏)的物品.
unusable-space-block: minecraft:barrier


# 是否禁用数据包压缩.
disable-compression: true

# 配置版本, 不要改变
config-version: 4
```

## bStats {#metrics}

```yml
# bStats 设置.
# https://bstats.org/plugin/server-implementation/GeyserMC .
metrics:
  # 是否启用.
  enabled: true
  # UUID, 请不要更改.
  uuid: generateduuid
```

## 高级设置 {#advanced-options}

```yml
# Geyser 会在每个记分板数据包之后更新记分板.
# 但是当 Geyser 试图每秒处理大量记分板数据包时会导致严重的延迟.
# 此选项允许您指定在每秒多少个计分板数据包之后, 计分板更新将被限制到每秒四次更新.
scoreboard-packet-threshold: 20

# 允许来自 ProxyPass 和 Waterdog 的连接.
# 详见 https://www.spigotmc.org/wiki/firewall-guide/ - 使用 UDP 替代 TCP.
enable-proxy-connections: false

# MTU 值, 自行查询何为 MTU .
mtu: 1400

# 是否直接连接到 Java 服务器而不建立 TCP 连接.
# 只有当某个插件的数据包或网络无法与 Geyser 正常工作时, 才应考虑关闭此功能.
# 如果在插件版本上启用, Geyser 配置下的 Java 服务器地址和端口部分将被忽略.
# 如果在插件版本上禁用, 将有可能导致性能会下降, 延迟会增加.
use-direct-connection: true
```


汉化文件: [config.yml](https://raw.githubusercontent.com/GeyserChinese/geyserchinese.github.io/refs/heads/main/config_translation/geyser-config.yml)

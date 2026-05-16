---
title: 我只能说帅爆了
date: 2026-02-24T08:36:25+08:00
lastmod: 2026-04-04T07:54:00+08:00
---

# 我只能说帅爆了

# UAC 助手

本插件可以通过检测权限让 ClassIsland 在启动时以管理员身份启动。

> [!NOTE] ✏️ 
> **温馨提示**：本插件出于安全考虑，第一次食用不默认启用**以管理员身份运行 ClassIsland** 的功能，因此请您到设置界面开启

## 使用方法

1. 在插件市场下载本插件；
2. 在插件设置界面中，启动插件功能
3. 放心(?食用

## 声明

本项目参考了：

- [StartUpAsAdmin](https://github.com/ClassIsland/StartUpAsAdmin)
- [CIUACHelper](https://github.com/liuziheng20091106/CIUACHelper)
- [SystemTools](https://github.com/Programmer-MrWang/SystemTools)

特别感谢 [@Programmer-MrWang](https://github.com/Programmer-MrWang) 对本插件的技术支持

## 许可证

本项目基于 [GNU General Public License v3.0](https://github.com/Ma-fangxiu/uaccomp/blob/master/LICENSE) 许可。

aaa你A。

```html
```

<iframe src="/widgets/Vue REPL/" data-subtype="widget" border="0" frameborder="no" framespacing="0" allowfullscreen="true" style="width: 926px;"></iframe>

<div>
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>数字时钟</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            font-family: 'Arial', sans-serif;
        }
        .clock-container {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 40px 60px;
            box-shadow: 0 8px 32px 0 rgba(31, 38, 135, 0.37);
            border: 1px solid rgba(255, 255, 255, 0.18);
        }
        .time {
            font-size: 72px;
            color: white;
            font-weight: bold;
            letter-spacing: 5px;
            text-shadow: 0 0 10px rgba(255, 255, 255, 0.5);
        }
        .date {
            font-size: 24px;
            color: rgba(255, 255, 255, 0.8);
            margin-top: 15px;
            text-align: center;
        }
        .seconds {
            font-size: 9px;
            );
        }
    </style>
</head>
<body>
    <div class="clock-container">
        <div class="time" id="clock">
            <span id="hours">00</span>:<span id="minutes">00</span>:<span id="seconds" class="seconds">00</span>
        </div>
        <div class="date" id="date">吃饭中...</div>
    </div>
    <script>
        function updateClock() {
            const now = new Date();
            // 获取时间
            const hours = String(now.getHours()).padStart(2, '0');
            const minutes = String(now.getMinutes()).padStart(2, '0');
            const seconds = String(now.getSeconds()).padStart(2, '0');
            // 更新显示
            document.getElementById('hours').textContent = hours;
            document.getElementById('minutes').textContent = minutes;
            document.getElementById('seconds').textContent = seconds;
            // 获取日期
            const year = now.getFullYear();
            const month = String(now.getMonth() + 1).padStart(2, '0');
            const day = String(now.getDate()).padStart(2, '0');
            const weekDays = ['星期日', '星期一', '星期二', '星期三', '星期四', '星期五', '星期六'];
            const weekDay = weekDays[now.getDay()];
            // 更新日期显示
            document.getElementById('date').textContent = `${year}年${month}月${day}日 ${weekDay}`;
        }
        // 初始化时钟
        updateClock();
        // 每秒更新一次
        setInterval(updateClock, 1000);
    </script>
</body>
</html>
</div>

‍

# 🎵 音乐播放器

一个功能丰富的在线音乐播放器，支持多平台音乐搜索、在线播放、歌词显示、音乐下载等功能。

## ✨ 功能特性

### 🎯 核心功能
- **多平台音乐搜索** - 支持网易云音乐、QQ音乐、酷我音乐、酷狗音乐、咪咕音乐等
- **在线播放** - 高品质音乐在线播放，支持多种音质选择
- **每日推荐** - 基于关键词的智能推荐系统，每次刷新都有新发现
- **歌词显示** - 实时滚动歌词，支持点击跳转
- **音乐下载** - 支持音乐文件和歌词文件下载

### 🎨 界面特色
- **现代化UI设计** - 毛玻璃效果、渐变背景、流畅动画
- **响应式布局** - 完美适配桌面端和移动端
- **暗色主题** - 护眼的深色界面设计
- **直观操作** - 简洁明了的用户交互

### 🎮 操作体验
- **键盘快捷键** - 空格键播放/暂停，左右箭头切换歌曲
- **智能推荐** - 40+关键词库，涵盖心情、场景、风格、年代等
- **无缝播放** - 支持播放列表自动切换
- **实时反馈** - 优雅的通知系统

## 🚀 快速开始

### 环境要求
- 现代浏览器（Chrome、Firefox、Safari、Edge）
- 网络连接

### 使用方法
1. 直接在浏览器中打开 `播放器.html` 文件
2. 等待推荐歌单加载完成
3. 点击歌曲开始播放，或使用搜索功能查找特定音乐

## 🔧 API配置与替换

### 当前API配置
播放器使用的音乐API地址配置在JavaScript代码的第902行：

```javascript
const API_BASE = 'https://music-api.gdstudio.xyz/api.php';
```

### 🔄 一键替换API教程

如果当前API不可用，可以按照以下步骤替换：

#### 步骤1：找到API配置
在 `播放器.html` 文件中找到第902行的API配置：
```javascript
// 🎵 音乐API配置 - 如需更换API请修改此处
const API_BASE = 'https://music-api.gdstudio.xyz/api.php';
```

#### 步骤2：替换API地址
将 `API_BASE` 的值替换为新的API地址：
```javascript
// 示例：替换为新的API
const API_BASE = 'https://your-new-api.com/api.php';
```

#### 步骤3：验证API兼容性
确保新API支持以下接口格式：

**搜索音乐：**
```
GET /api.php?types=search&source=netease&name=歌曲名&count=30
```

**获取播放链接：**
```
GET /api.php?types=url&source=netease&id=歌曲ID&br=320
```

**获取歌词：**
```
GET /api.php?types=lyric&source=netease&id=歌曲ID
```

**获取专辑图：**
```
GET /api.php?types=pic&source=netease&id=图片ID&size=300
```

### 🌐 推荐的替代API

以下是一些可用的音乐API服务：

1. **NeteaseCloudMusicApi**
   ```javascript
   const API_BASE = 'http://localhost:3000';
   // 需要本地部署：https://github.com/Binaryify/NeteaseCloudMusicApi
   ```

2. **自建API服务**
   ```javascript
   const API_BASE = 'https://your-domain.com/music-api';
   // 需要自己搭建兼容的API服务
   ```

### ⚠️ 注意事项

1. **CORS跨域问题**：播放器已内置跨域解决方案，使用代理服务器处理
2. **API格式兼容**：新API必须返回相同格式的JSON数据
3. **音乐源支持**：确保新API支持所需的音乐平台
4. **速率限制**：注意API的请求频率限制

## 📁 项目结构

```
音乐播放器/
├── 播放器.html          # 主程序文件（HTML + CSS + JavaScript）
└── README.md           # 项目文档
```

## 🎵 支持的音乐平台

- 🎧 网易云音乐 (netease)
- 🎶 QQ音乐 (tencent)
- 🎵 酷我音乐 (kuwo)
- 🎤 JOOX (joox)
- 🎸 酷狗音乐 (kugou)
- 📻 咪咕音乐 (migu)
- 🌍 Deezer (deezer)
- 🎯 Spotify (spotify)
- 🍎 Apple Music (apple)
- 📺 YouTube Music (ytmusic)
- 🌊 TIDAL (tidal)
- 🎼 Qobuz (qobuz)
- 📖 喜马拉雅 (ximalaya)

## ⌨️ 键盘快捷键

| 按键 | 功能 |
|------|------|
| `空格` | 播放/暂停 |
| `←` | 上一首 |
| `→` | 下一首 |
| `回车` | 搜索（搜索框内） |

## 🎨 自定义配置

### 修改推荐关键词
在代码中找到 `playlistKeywords` 数组（约第918行），可以添加或修改推荐关键词：

```javascript
// 🏷️ 推荐关键词配置 - 可自定义添加关键词
const playlistKeywords = [
    // 心情类
    '开心', '伤感', '治愈', '励志', '放松', '浪漫',
    // 添加你的自定义关键词
    '学习', '工作', '运动', '咖啡厅',
    // ...更多关键词
];
```

### 修改音乐源优先级
在代码中找到 `musicSources` 数组（约第930行），可以调整音乐源的优先级：

```javascript
// 🎼 音乐源配置 - 可调整优先级顺序
const musicSources = ['netease', 'tencent', 'kuwo', 'kugou', 'migu'];
```

### 调整自动播放设置
在 `loadRandomPlaylist` 函数中找到自动播放配置：

```javascript
// 🎯 自动播放配置 - 可修改是否自动播放
if (currentIndex === -1 && shuffledSongs.length > 0) {
    setTimeout(() => {
        currentPlaylist = recommendPlaylist;
        playSong(0);
    }, 1500); // 延迟时间可调整
}
```

## 🐛 常见问题

### Q: 为什么有些歌曲播放不了？
A: 可能是版权限制或API限制，尝试切换其他音乐源或更换API。

### Q: 如何解决跨域问题？
A: 播放器已内置跨域解决方案，使用 `https://api.allorigins.win/raw?url=` 作为代理。

### Q: 下载的音乐在哪里？
A: 下载的文件会保存在浏览器的默认下载文件夹中。

### Q: 可以离线使用吗？
A: 不可以，播放器需要网络连接来获取音乐数据。

## 🤝 贡献指南

欢迎提交Issue和Pull Request来改进这个项目！

### 开发建议
1. 保持代码注释的完整性
2. 遵循现有的代码风格
3. 测试新功能的兼容性
4. 更新相关文档

## 📄 许可证

本项目仅供学习和个人使用，请遵守相关音乐平台的服务条款。

## 🙏 致谢

- 感谢各大音乐平台提供的API接口
- 感谢开源社区的技术支持
- 感谢所有使用和反馈的用户

---

**⭐ 如果这个项目对你有帮助，请给个Star支持一下！**

## 📞 联系方式

如有问题或建议，欢迎通过以下方式联系：
- 提交GitHub Issue
- 发送邮件反馈

---

*最后更新时间：2024年12月* 

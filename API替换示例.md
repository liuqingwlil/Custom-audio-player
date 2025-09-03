# 🔧 音乐API替换详细教程

## 📍 当前API位置

在 `播放器.html` 文件的第902行找到API配置：

```javascript
// 🎵 音乐API配置 - 如需更换API请修改此处
const API_BASE = 'https://music-api.gdstudio.xyz/api.php';
```

## 🔄 替换步骤

### 方法一：直接替换API地址

1. **打开播放器文件**
   ```
   用文本编辑器打开 播放器.html
   ```

2. **找到API配置行**
   ```javascript
   // 搜索关键词: const API_BASE =
   // 或直接跳转到第902行
   ```

3. **替换API地址**
   ```javascript
   // 原配置
   const API_BASE = 'https://music-api.gdstudio.xyz/api.php';
   
   // 替换为新API（示例）
   const API_BASE = 'https://your-new-api.com/api.php';
   ```

4. **保存文件并测试**

### 方法二：使用本地API服务

如果要使用本地部署的API服务：

```javascript
// 本地API服务示例
const API_BASE = 'http://localhost:3000';
```

## 🌐 推荐的替代API服务

### 1. NeteaseCloudMusicApi (推荐)

**GitHub**: https://github.com/Binaryify/NeteaseCloudMusicApi

**部署方式**:
```bash
git clone https://github.com/Binaryify/NeteaseCloudMusicApi.git
cd NeteaseCloudMusicApi
npm install
npm start
```

**配置**:
```javascript
const API_BASE = 'http://localhost:3000';
```

**注意**: 需要修改API调用格式，因为接口参数可能不同

### 2. 其他音乐API服务

```javascript
// 示例API地址（需要自己搭建或找到可用的服务）
const API_BASE = 'https://api.example.com/music';
```

## ⚙️ API接口格式要求

新的API必须支持以下接口格式：

### 🔍 搜索音乐
```
GET {API_BASE}?types=search&source={platform}&name={keyword}&count={number}
```

**响应格式**:
```json
[
  {
    "id": "歌曲ID",
    "name": "歌曲名称",
    "artist": ["艺术家"],
    "album": "专辑名",
    "source": "平台名",
    "pic_id": "封面ID",
    "lyric_id": "歌词ID"
  }
]
```

### 🎵 获取播放链接
```
GET {API_BASE}?types=url&source={platform}&id={song_id}&br={quality}
```

**响应格式**:
```json
{
  "url": "播放链接",
  "br": "音质"
}
```

### 📝 获取歌词
```
GET {API_BASE}?types=lyric&source={platform}&id={lyric_id}
```

**响应格式**:
```json
{
  "lyric": "LRC格式歌词",
  "tlyric": "翻译歌词（可选）"
}
```

### 🖼️ 获取封面
```
GET {API_BASE}?types=pic&source={platform}&id={pic_id}&size={size}
```

**响应格式**:
```json
{
  "url": "图片链接"
}
```

## 🛠️ 自定义API适配

如果新API的接口格式不同，需要修改相应的函数：

### 修改搜索函数
```javascript
// 在 searchMusic() 函数中修改API调用
async function searchMusic() {
    // ... 其他代码 ...
    
    // 根据新API格式修改请求URL
    const apiUrl = `${API_BASE}/search?q=${encodeURIComponent(keyword)}&source=${source}&limit=30`;
    
    // ... 其他代码 ...
}
```

### 修改播放函数
```javascript
// 在 playSong() 函数中修改API调用
const apiUrl = `${API_BASE}/song/url?id=${song.id}&br=${quality}`;
```

## 🔧 常见API服务搭建

### 使用Docker快速部署

```dockerfile
# Dockerfile示例
FROM node:16
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 3000
CMD ["npm", "start"]
```

### 使用Vercel部署

```json
{
  "version": 2,
  "builds": [
    {
      "src": "app.js",
      "use": "@vercel/node"
    }
  ],
  "routes": [
    {
      "src": "/(.*)",
      "dest": "/app.js"
    }
  ]
}
```

## ⚠️ 注意事项

1. **CORS跨域**: 确保新API支持跨域请求或配置CORS
2. **API限制**: 注意新API的请求频率限制
3. **数据格式**: 确保返回的JSON格式与播放器兼容
4. **HTTPS**: 建议使用HTTPS协议的API服务
5. **稳定性**: 选择稳定可靠的API服务

## 🧪 测试新API

替换API后，按以下步骤测试：

1. **测试搜索功能**: 在搜索框输入关键词
2. **测试播放功能**: 点击歌曲播放
3. **测试歌词显示**: 检查歌词是否正常显示
4. **测试下载功能**: 尝试下载音乐和歌词
5. **测试推荐功能**: 刷新页面检查推荐歌单

## 🆘 故障排除

### 常见问题解决

1. **CORS错误**
   ```javascript
   // 播放器已内置CORS解决方案
   // 如果仍有问题，检查API是否支持CORS
   ```

2. **API格式不匹配**
   ```javascript
   // 需要修改相应的API调用函数
   // 根据新API的文档调整参数和响应处理
   ```

3. **网络连接问题**
   ```javascript
   // 检查API服务是否正常运行
   // 确认网络连接状态
   ```

## 📞 获取帮助

如果在替换API过程中遇到问题：

1. 检查浏览器开发者工具的控制台错误
2. 确认新API的接口文档
3. 测试API接口是否正常响应
4. 提交Issue到项目仓库

---

**💡 提示**: 建议在替换API前备份原文件，以便出现问题时快速恢复。 
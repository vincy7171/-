# 缓星 · HUANXING

按自己的轨道，慢慢发光。

「缓」是允许自己拥有不同的节奏；「星」是即使暂时看不见，也仍然存在的光。

一个无需安装依赖、无需 API 密钥、适合 GitHub Pages 的情绪日记与自我关怀网站。原生 HTML、CSS、JavaScript，适配手机和电脑。没有外部字体或图片请求。

## 已实现

- 多选情绪、强度、事件标签、文字日记；浏览器本地保存。
- 日记筛选、删除确认、JSON 数据导出。
- 最近七天概略心情图、情绪频次与事件共同出现统计。初始为空，无伪造记录。
- 呼吸、感官觉察、合成音景、肩部舒展、冥想、散步六种练习。
- 计时、暂停、继续、结束反馈；有帮助的练习自动汇总。
- 音景通过 Web Audio 在本地合成，支持音量调节，暂停或关闭时停止。
- 响应式布局、键盘焦点、原生模态对话框、减少动态效果偏好。

## 本地预览

在项目目录运行（需要 Python 3）：

```sh
python3 -m http.server 8080
```

打开 http://localhost:8080 。也可双击 index.html 预览，但浏览器对 file:// 的本地存储行为不同，建议使用 HTTP 服务。

## GitHub Pages 部署

最简单的方式，不需要命令行：

1. 新建 GitHub 仓库，将本项目目录内文件上传到仓库根目录，确保根目录有 index.html、style.css、app.js。
2. 进入仓库 Settings → Pages。
3. 在 Build and deployment 中选 Deploy from a branch，选择 main 和 / (root)，保存。
4. 等待 Pages 部署完成，在同一页面查看网站地址，通常为 https://你的用户名.github.io/仓库名/ 。

如果通过 Git 保留了 `.github/workflows/pages.yml`，也可以在 Settings → Pages 中将 Source 选择为 GitHub Actions。工作流会在 main 分支更新时自动发布，上传内容仅包含网站静态文件。

```sh
git init
git add .
git commit -m "Build Huanxing mood journal"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.git
git push -u origin main
```

请将示例远程地址替换为你自己的空仓库。也可部署到其他静态托管服务；无需构建命令，发布目录为项目根目录。

## 数据与功能边界

- 所有日记存储在 localStorage 的 `huanxing.v1` 中，仅在当前浏览器、当前网站源可见，不跨设备同步。更换部署域名或端口也会切换存储空间。
- 清除站点数据会丢失记录，建议定期导出。导出为可读 JSON，当前未提供导入恢复界面。
- 没有登录、服务端数据库或云端 AI。本地回顾按用户标签统计共同出现次数，不诊断、不推断因果。请勿将它宣传为专业心理测评或 AI 治疗服务。
- 图表将低落、焦虑、疲惫、平静、开心映射到 1–5 的概略位置，对每日所选标签取均值；“说不清”不参与计算。它不是心理健康分数，也不表示情绪强度。
- 默认没有提醒、打卡和排行榜，不向第三方发送日记。共享设备与未加密本地存储不适合保存高度敏感信息。
- 网站采用 hash 导航与相对资源路径，兼容 GitHub Pages 仓库子路径，无需配置路由回退。

## 文件

`index.html`：页面与模态框；`style.css`：视觉与响应式；`app.js`：数据、统计、练习与音频；`.github/workflows/pages.yml`：可选自动发布流程。

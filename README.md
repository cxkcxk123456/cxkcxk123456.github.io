# Academic Homepage

一个使用纯 HTML 和 CSS 编写的英文个人学术主页。无需构建工具、JavaScript、数据库、API Key 或付费服务，可直接预览，并通过 GitHub Pages 免费发布。

**当前仅为本地网站，尚未创建网站仓库、推送或验证公网部署。**

## 当前公开内容

以下信息已由本人提供，用于页面正文：

| 项目 | 内容 |
| --- | --- |
| 英文姓名 | Bin Wang |
| 机构 | Fudan University |
| 身份 | Master’s Student |
| 公开邮箱 | binwang25@m.fudan.edu.cn |

发布前，请核对上述姓名、机构和邮箱与 OpenReview 注册资料一致，并确认愿意公开该邮箱。研究方向与 GitHub 账号暂不展示；Publications、Projects、CV 也暂不展示，之后可按实际情况添加。

## 文件

| 文件 | 用途 |
| --- | --- |
| `index.html` | 页面内容、语义结构、SEO title 和 description |
| `style.css` | 排版、颜色、响应式布局和键盘焦点样式 |
| `.nojekyll` | 告诉 GitHub Pages 跳过 Jekyll 处理 |
| `.gitignore` | 排除常见本地临时文件和秘密配置 |
| `README.md` | 修改、预览和部署说明 |

## 修改和预览

用文本编辑器打开 `index.html`，修改对应正文；姓名或机构有变化时，同时更新 `<title>` 和 `<meta name="description">`。修改邮箱时，同时更新可见邮箱文字和 `mailto:` 链接。样式集中在 `style.css`。

直接双击 `index.html` 即可在浏览器查看。若已安装 Python，也可以在 PowerShell 运行：

```powershell
python -m http.server 8000 --bind 127.0.0.1 --directory "D:\Adaptive-TREAD\academic-homepage"
```

然后打开 `http://127.0.0.1:8000/`。该预览只在本机可用，不能作为 OpenReview 的 Homepage URL。完成后按 `Ctrl+C` 关闭服务。

发布前检查桌面和手机宽度下的布局、键盘 Tab 导航和邮箱链接，并逐项核对公开内容。

## 免费部署到 GitHub Pages

本机 Git 可用，GitHub CLI **2.102.0** 已安装在 `D:\Tools\GitHubCLI\bin\gh.exe`，并已加入当前用户 PATH。安装包已通过官方 SHA-256 校验。新打开的终端可以使用 `gh`；已有终端也可以直接使用完整路径。

首次连接使用 GitHub 官方网页登录授权，不需要向聊天或其他人提供密码或 Token：

```powershell
& "D:\Tools\GitHubCLI\bin\gh.exe" auth login --hostname github.com --git-protocol https --web
```

浏览器授权完成后，用以下只读命令核实状态和真实用户名：

```powershell
& "D:\Tools\GitHubCLI\bin\gh.exe" auth status --active --hostname github.com
& "D:\Tools\GitHubCLI\bin\gh.exe" api user --jq .login
```

CLI 成功登录后，可以自动完成仓库创建、网站提交与推送，以及 Pages 发布源配置。仍须先确认真实部署账号、页面公开内容和创建公开仓库；安装或登录成功本身不代表已发布。登录凭据不得放入网站目录或 Git 历史。下面保留完整的 GitHub 网页部署方法，供手动操作或网络排障时使用。

### 1. 确认账号与公共仓库

登录 GitHub，查看个人资料中的真实用户名。后续所有 `YOUR_GITHUB_USERNAME` 都必须替换成该用户名；它与页面姓名可以不同，网站正文也无需展示 GitHub 用户名。

目标仓库为 `YOUR_GITHUB_USERNAME.github.io`，目标主页地址为 `https://YOUR_GITHUB_USERNAME.github.io/`。仓库名中的用户名使用小写。如果该仓库已存在，先检查其中内容与现有网站，不要直接覆盖。

GitHub Free 可以在公共仓库免费使用 Pages。**创建前先确认同意创建公开仓库；页面内容也需经过本人确认后再上传。** 获得确认后，在 GitHub 选择 **New repository**，填写目标仓库名，选择 **Public**，创建仓库。可勾选 **Add README**，稍后用本项目的 README 替换它。

### 2. 只上传网站文件

在网站仓库选择 **Add file → Upload files**，只选择 `D:\Adaptive-TREAD\academic-homepage` 中以下五个文件：

```text
index.html
style.css
README.md
.nojekyll
.gitignore
```

将文件放在仓库根目录，提交到 `main`。若网页未显示或未接收点开头的文件，可以使用 **Add file → Create new file**：创建 `.nojekyll`，留空内容并提交；创建 `.gitignore` 时复制本地同名文件的内容。`.nojekyll` 用于关闭默认 Jekyll 处理；普通 HTML/CSS 即使暂未添加它通常也可工作，本项目仍包含它，以保持发布方式明确。

**不要上传整个 `D:\Adaptive-TREAD` 研究仓库，不要上传其 `.git` 目录或历史，也不要更改研究仓库的远端。** 不要上传密码、Token、私钥、私人电话、生日、`.env` 或尚未公开的研究文件。网页上传时同样需要按上述文件白名单逐项选择；`.gitignore` 不能替代人工确认。

### 3. 设置 Pages

进入网站仓库的 **Settings → Pages**，在 **Build and deployment** 中设置：

- **Source:** `Deploy from a branch`
- **Branch:** `main`
- **Folder:** `/(root)`

点击 **Save**。选择前应已向 `main` 提交网站文件；根目录必须含小写 `index.html`。

### 4. 等待并验证公网网站

GitHub 说明推送后网站更新可能需要最多约 10 分钟。可在 **Actions** 查看部署运行结果，然后通过 **Settings → Pages → Visit site** 打开网站。

确认以下各项后，才可将网站标为已上线：

- 在未登录 GitHub 的浏览器窗口中访问完整 HTTPS 地址，页面实际加载成功，而不是出现 404、登录页面或部署错误。
- 页面正文可见 `Bin Wang`、`Fudan University`、`Master’s Student` 和 `binwang25@m.fudan.edu.cn`；这些内容不能仅出现在网页元数据中。
- 样式正常，手机端没有横向溢出，邮箱链接指向正确地址，页面没有未替换的占位符。

可用 PowerShell 检查首页 HTTP 响应，仍需在浏览器核对正文和布局：

```powershell
(Invoke-WebRequest -UseBasicParsing -Uri "https://YOUR_GITHUB_USERNAME.github.io/").StatusCode
```

若出现 404，检查仓库名、Pages 发布源、`main` 根目录中的 `index.html` 和 Actions 部署结果。文件名区分大小写。推送或提交成功本身不代表部署成功；网络或权限不足时，应保留“尚未验证”状态。

实际用户名已确认且网站通过上述验证后，将 **`https://YOUR_GITHUB_USERNAME.github.io/`** 中的占位符替换成真实用户名，把所得完整 HTTPS URL 填入 OpenReview 的 **Homepage URL**。不要填本地预览地址或 GitHub 仓库地址。

## 未来扩展

需要添加内容时，在 `index.html` 的主内容区域加入带标题的语义化 `<section>`，并按需添加对应导航链接。可以使用以下稳定的 section ID：

| 模块 | 建议 ID | 何时添加 |
| --- | --- | --- |
| Research Interests | `research` | 本人确认希望公开的研究方向后 |
| Publications | `publications` | 有可公开列出的真实论文或预印本后；明确区分发表状态 |
| Projects | `projects` | 有真实、可公开介绍的项目后 |
| CV | `cv` | 有已检查隐私信息的公开 CV 后 |

GitHub 链接可在账号和是否公开得到确认后添加到 Contact。添加 CV PDF 或图片等新文件时，更新部署文件清单。不要将尚未发表或尚未公开的工作写成已发表成果，也不要填入未经确认的教育、导师或奖项信息。

## GitHub 官方文档

- [GitHub CLI 2.102.0 官方发布](https://github.com/cli/cli/releases/tag/v2.102.0)：本机安装版本及官方安装包。
- [GitHub CLI 网页登录](https://cli.github.com/manual/gh_auth_login)：浏览器授权与本地凭据保存。
- [创建 GitHub Pages 网站](https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site)：免费公共仓库、个人主页命名、入口文件、`.nojekyll` 和发布等待说明。
- [配置 GitHub Pages 发布源](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site)：分支与根目录设置。
- [排查 GitHub Pages 的 404 错误](https://docs.github.com/en/pages/getting-started-with-github-pages/troubleshooting-404-errors-for-github-pages-sites)：入口文件位置与大小写检查。

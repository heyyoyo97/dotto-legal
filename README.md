# 两点 Dotto — 法务静态站点

三个自包含 HTML 页面 + 品牌 logo，用于 App Store 上架所需的公开网址。HTML 内除引用同目录 `logo.png` 外无任何外部依赖（字体、CSS、JS 全部内联），可直接部署到任意静态托管。

| 文件 | 用途 | App Store Connect 对应字段 |
|------|------|---------------------------|
| `index.html` | 首页 / 支持页（含联系邮箱、删除入口说明） | **支持 URL（Support URL）** |
| `privacy.html` | 隐私政策 | **隐私政策 URL（Privacy Policy URL）** |
| `terms.html` | 用户协议 | 可放营销 URL，或在 App 内/隐私政策中引用 |
| `logo.png` | 两点品牌标识（页面引用，须一并上传） | — |

> 颜色与标识取自 app 设计系统：品牌紫 `#8278D9`（`src/design/theme.ts` 的 `accent`），logo 同 `assets/logo.png`。

源文本来自 `docs/privacy_policy.md` 与 `docs/user_agreement.md`，改文本后需同步更新这里的 HTML。

---

## 免费部署（任选其一，都不用买域名）

### 方案 A：Gitee Pages（码云，国内访问快，推荐）
1. 注册 gitee.com 账号并完成实名认证。
2. 新建一个**公开**仓库（如 `dotto-legal`），把 `legal-site/` 里的三个 HTML 和 logo.png 传上去（放在仓库根目录）。
3. 仓库页面 → 服务 → Gitee Pages → 选择分支 `master`、目录 `/` → 启动。
4. 得到网址形如 `https://<用户名>.gitee.io/dotto-legal/`。
   - 隐私政策 URL：`https://<用户名>.gitee.io/dotto-legal/privacy.html`
   - 支持 URL：`https://<用户名>.gitee.io/dotto-legal/`

### 方案 B：GitHub Pages（Apple 审核可达，国内偶发不稳）
1. 新建一个**公开** GitHub 仓库（如 `dotto-legal`），上传三个 HTML 和 logo.png 到根目录。
2. 仓库 Settings → Pages → Source 选 `main` 分支、`/ (root)` → Save。
3. 几分钟后得到 `https://<用户名>.github.io/dotto-legal/privacy.html` 等。

### 方案 C：腾讯云 COS 静态网站（已在用腾讯云）
1. 新建一个 COS 存储桶，权限设为「公有读私有写」。
2. 基础配置 → 静态网站 → 开启，索引文档填 `index.html`。
3. 上传三个 HTML 和 logo.png 到桶根目录。
4. 用「静态网站」给出的默认访问节点访问；绑定**自定义域名**才需备案，默认节点可先用于提交。

---

## 填入 App Store Connect
- **隐私政策 URL** → `.../privacy.html`（必填）
- **支持 URL** → `.../`（首页，必填）
- 部署后务必在手机浏览器实测能正常打开，再提交。

> 提示：以上为免费过审方案。若日后要品牌化 + 国内稳定访问 + 完整备案，可注册 dotto 域名指向同一份文件。

# Giscus 评论系统配置指南

## 解决 "giscus is not installed" 错误

### 第一步：安装 Giscus App
1. 访问 **GitHub Apps 安装页面**：https://github.com/apps/giscus
2. 点击 **Install** 按钮
3. 选择要安装的仓库：
   - 选择 **Only select repositories**
   - 勾选 `junjiangao/Notes` 仓库
4. 点击 **Install** 确认安装

### 第二步：启用 GitHub Discussions
1. 访问你的 GitHub 仓库：https://github.com/junjiangao/Notes
2. 点击 **Settings** 标签
3. 向下滚动找到 **Features** 部分
4. 勾选 **Discussions** 复选框

### 2. 获取仓库和分类 ID

访问以下页面配置 Giscus：
https://giscus.app/zh-CN

#### 配置步骤：
1. **仓库**: 输入 `junjiangao/Notes`
2. **页面 ↔️ discussion 映射关系**: 选择 `pathname`
3. **Discussion 分类**: 选择 `General` 或创建新分类
4. **特性**: 
   - ✅ 启用反应
   - ✅ 在主评论上方放置评论框

完成配置后，复制生成的 `data-repo-id` 和 `data-category-id` 值。

### 3. 更新 _config.yml

将获取到的 ID 填入配置文件：

```yaml
comments:
  active: giscus
  giscus:
    repo: junjiangao/Notes
    repo_id: "你的仓库ID"          # 从 giscus.app 获取
    category: General
    category_id: "你的分类ID"      # 从 giscus.app 获取
    mapping: pathname
    input_position: bottom
    lang: zh-CN
    reactions_enabled: 1
```

### 4. 测试评论功能

部署完成后，访问任意文章页面，应该能看到评论区域。

## 注意事项

1. **仓库必须是公开的**：Giscus 只支持公开仓库
2. **需要安装 Giscus App**：在仓库页面安装 [Giscus GitHub App](https://github.com/apps/giscus)
3. **Discussions 权限**：确保仓库启用了 Discussions 功能

如遇到问题，请查看 [Giscus 文档](https://github.com/giscus/giscus/blob/main/ADVANCED-USAGE.md)。
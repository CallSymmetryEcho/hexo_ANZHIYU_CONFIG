# Obsidian to Hexo 博客同步指南

> 记录如何从Obsidian笔记同步到Hexo博客的技术实现

## 背景

本项目用于管理和同步Obsidian仓库中的笔记到Hexo博客，采用**复制**而非移动的方式，确保原始笔记不受影响。

## 同步工具

### 工具位置
```
/Users/lianbin/workdir/_codes_/New_Project/website/hexo_ANZHIYU_CONFIG/tools/obsidian_sync/
```

### 脚本列表

| 脚本 | 功能 |
|------|------|
| `create_index.sh` | 创建Hexo和Obsidian的索引文件 |
| `find_new_files.sh` | 对比找出Obsidian新增的文件 |
| `sync_to_hexo.sh` | 将新增文件复制到Hexo |
| `convert_wikilinks.sh` | 转换Obsidian双链格式为Hexo兼容格式 |
| `full_sync.sh` | **一键同步脚本**（推荐） |

## 快速开始

### 第一次运行（初始化）

```bash
cd tools/obsidian_sync
./create_index.sh all
```

### 一键同步（推荐）

```bash
cd tools/obsidian_sync
./full_sync.sh
```

这会执行完整流程：
1. 创建/更新索引
2. 查找新增文件
3. 同步到Hexo
4. 生成静态网页
5. 推送到GitHub

### 手动同步流程

```bash
# 1. 更新索引
./create_index.sh all

# 2. 查看新增文件
./find_new_files.sh all

# 3. 同步到Hexo（会询问确认）
./sync_to_hexo.sh

# 4. 可选：转换双链格式
./convert_wikilinks.sh
```

### 常用选项

```bash
# 一键同步（会询问确认）
./full_sync.sh

# 强制同步，不询问确认
./full_sync.sh --force

# 模拟运行，不实际复制
./full_sync.sh --dry-run

# 单独脚本选项
./sync_to_hexo.sh --dry-run
./sync_to_hexo.sh --force
```

## 排除规则

同步时会自动排除以下文件夹：
- `废弃仓库/`
- `images/`
- `Article_reading_Auto_generated_by_zoteroif/`
- `.obsidian/`
- `外骨骼项目/`
- `template_folder/`
- `.trash/`

## 双链格式转换

### Obsidian格式
```markdown
[[文件名]]
[[文件名|显示文本]]
![[图片.png]]
```

### Hexo兼容格式
```markdown
[文件名](文件名)
[显示文本](文件名)
![](图片.png)
```

## 目录结构

```
tools/obsidian_sync/
├── indices/                  # 索引文件目录
│   ├── hexo_files.txt      # Hexo文件索引
│   └── obsidian_files.txt  # Obsidian文件索引
├── create_index.sh          # 创建索引脚本
├── find_new_files.sh       # 查找新增文件脚本
├── sync_to_hexo.sh         # 同步脚本
├── convert_wikilinks.sh    # 双链转换脚本
├── full_sync.sh            # 一键同步脚本（推荐）
└── new_files.txt           # 新增文件列表
```

## 环境变量

可通过环境变量自定义路径：

```bash
HEXO_PATH=/path/to/hexo/posts \
OBSIDIAN_PATH=/path/to/obsidian \
./create_index.sh all
```

## 注意事项

1. **复制而非移动**：所有操作都是复制，不会修改Obsidian原文件
2. **索引需要定期更新**：每次同步前建议更新索引
3. **手动审核**：新增文件需要人工确认后再同步
4. **双链处理**：复制后需要转换双链格式才能在Hexo中正常使用

## 相关资源

- [Obsidian CLI](https://obsidian.md)
- [Hexo文档](https://hexo.io/docs/)
- [Anzhiyu主题](https://anzhiyu.cn/)

---

*最后更新：2026-03-12*

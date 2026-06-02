# VectorPeakBlogs 协作指令

本仓库采用“渐进式披露”结构：根目录只放最短规则，详细说明放在 `agents_md_hub/`

## 必读顺序

1. 先读本文件
2. 通用协作框架见 `agents_md_hub/project_framework.md`
3. 项目具体规则见 `agents_md_hub/project_instruction.md`
4. 图标、图片和品牌资产记录见 `agents_md_hub/assets.md`

## 项目定位

- 本仓库是基于 Mintlify 搭建的 `VectorPeak` 文档与个人知识站点
- 站点主配置文件是 `docs.json`
- 内容主要使用 `MDX` 编写
- 文本文件默认使用 `UTF-8`，中文文件尤其要避免乱码

## 核心规则

- 保持个人知识站点定位，不要写成通用 SaaS 营销文档
- 修改导航、栏目或路径前，同时检查 `docs.json`、目标 `MDX` 文件和页面内链接
- 解释重要概念时采用自顶向下方式：先讲用途，再讲结构、机制、例子和边界
- 中文内容默认使用务实、清晰、解释型表达
- 文件路径、命令、配置键和代码标识符使用反引号标记
- 不要改写无关文件，也不要回退用户已有改动

## Mintlify 本地启动

Windows 下优先显式使用 `mint.cmd`，不要只写裸命令 `mint`

已验证环境：

- Node `22.22.3`
- npm `10.9.8`
- Mint CLI `4.2.588`
- Mint client `0.0.2997`

当前 Mint CLI 的 `mint.cmd dev --help` 未列出 `--port` 参数，本地预览优先使用默认端口启动

```powershell
cd /d E:\Github\VectorPeak\VectorPeakBlogs
mint.cmd dev --no-open
```

本地地址：

- `http://localhost:3000`

验证时优先使用 `localhost`：

```powershell
curl.exe -I --max-time 10 http://localhost:3000/
curl.exe -I --max-time 10 "http://localhost:3000/Agent/LangChain/Model%20Provider"
```

以返回 HTTP `200 OK` 为准

如果浏览器报 `ERR_CONNECTION_REFUSED`，通常不是 Node 损坏，而是 Mint dev 服务没有监听端口，或卡在 `preparing local preview...` 阶段。先清理卡住的 Mint 相关进程，再重新启动：

```powershell
$procs = Get-CimInstance Win32_Process | Where-Object {
  ($_.CommandLine -match 'mint\.cmd dev|@mintlify\\cli|mintlify') -and $_.ProcessId -ne $PID
}
$procs | Select-Object ProcessId,Name,CommandLine
foreach ($p in $procs) {
  Stop-Process -Id $p.ProcessId -Force -ErrorAction SilentlyContinue
}
mint.cmd dev --no-open
```

如果需要后台启动并保留日志：

```powershell
$project = 'E:\Github\VectorPeak\VectorPeakBlogs'
$log = Join-Path $project '.mint-dev.combined.log'
$cmd = '/c cd /d "' + $project + '" && mint.cmd dev --no-open > "' + $log + '" 2>&1'
$p = Start-Process -FilePath 'cmd.exe' -ArgumentList $cmd -WindowStyle Hidden -PassThru
Set-Content -Path (Join-Path $project '.mint-dev.pid') -Value $p.Id -Encoding ascii
```

看到日志里出现 `preview ready` 后，再访问 `http://localhost:3000`

## 详细规则

- `agents_md_hub/project_framework.md`
- `agents_md_hub/project_instruction.md`
- `agents_md_hub/assets.md`

# DigitalPick 数码指南

不买最贵的，只买最适合的。

**正式网站：[打开 DigitalPick](https://max0220-22.github.io/digitalpick/)**

已部署 GitHub Pages + Cloudflare Worker。详细上线记录与维护命令见源码包内 `docs/GITHUB-LIVE.md`。

中文数码购买决策网站，保留流动星河、3D小派、产品库、规则问答、验机清单与安全DeepSeek代理。

完整源码保存在 [digitalpick-source.zip](digitalpick-source.zip)，共234个项目文件，包含目录结构、测试和部署说明，不含密钥、环境文件、数据库、依赖或构建缓存。仓库通过GitHub网页上传，GitHub Actions自动解压源码后构建和发布。

## 本地运行

~~~bash
unzip digitalpick-source.zip -d source
cd source
npm ci
npm run dev
~~~

推荐Node.js 24 LTS。运行测试：npm test。源码内 README.md 和 docs/FREE-DEPLOYMENT.md 有完整维护说明。

## 免费托管

- 前端：GitHub Pages，仓库Settings → Pages选择GitHub Actions。
- AI：Cloudflare Pages入口经内部绑定连接Worker与SQLite Durable Object；Key只放Worker Secret。
- 仓库Actions Variable AI_PROXY_URL仅填写已部署的Pages网关公开HTTPS地址。
- 免费托管额度不包含DeepSeek模型调用费。所有数字示例价格仍是演示数据。
- 不要把任何API Key添加到NEXT_PUBLIC变量或提交到仓库。

更新网站：修改本地完整源码，运行测试后重新生成并上传digitalpick-source.zip，Actions会重新发布。不要把本地localhost预览产物直接上传到公网。

桌面/手机连接异常时打开 [连接与3D自检](https://max0220-22.github.io/digitalpick/diagnostics/)，仅检查免费会话和本地3D状态，不调用模型。

## 正式产品库与清单核验

[打开平板产品库](https://max0220-22.github.io/digitalpick/products/?category=tablet) · [清单逐项核验](https://max0220-22.github.io/digitalpick/products/coverage/)

产品库492条型号/地区版本：手机339、平板90、笔记本63。用户清单520项逐项核验：446确认、18纠正、56暂未确认；不把未确认名称编成已发布产品。部分记录只核对型号，未整理参数保持为空，不宣称所有字段完整。

支持品牌、代际、中文型号搜索和分页。缺报价不隐藏设备，新记录没有虚构价格、图片或评分。103项测试、前端/Worker类型检查及静态构建通过；来源与维护说明见源码内docs/CATALOG-EXPANSION.md。

## Detailed specifications — 2026-10-18

237 product records updated; 1,936 specification fields added and 176 refined. Identity-only records reduced from 169 to 18. Regional variants, Pro+ models and configuration bindings remain distinct. Official source links are included in product details and the AI context. No new prices, images or benchmarks.

Validation: 103 tests, frontend/Worker TypeScript, 516 static HTML pages and 20,286 local references; mobile layout checked at 390px. Reports and remaining gaps: docs/SPEC-ENRICHMENT.md and docs/spec-enrichment-report.json inside the source archive.

# DigitalPick 数码指南

不买最贵的，只买最适合的。

**正式网站：[打开 DigitalPick](https://max0220-22.github.io/digitalpick/)**

已部署 GitHub Pages + Cloudflare Worker。详细上线记录与维护命令见源码包内 `docs/GITHUB-LIVE.md`。

中文数码购买决策网站，保留流动星河、3D小派、产品库、规则问答、验机清单与安全DeepSeek代理。

完整源码保存在 [digitalpick-source.zip](digitalpick-source.zip)，共277个项目文件，包含目录结构、测试和部署说明，不含密钥、环境文件、数据库、依赖或构建缓存。仓库通过GitHub网页上传，GitHub Actions自动解压源码后构建和发布。

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
- 免费托管额度不包含DeepSeek模型调用费。价格按官网参考、历史发售和二手模型估算分别标注。
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

## 官方产品图片 — 2026-10-19

新增402条设备的官方主图，共覆盖426/492条型号及地区版本：手机307、平板75、笔记本44。产品卡片、详情页与参数素材库均展示图片及原始出处。剔除促销横幅、过小导航图、线框图和型号不符图片；其余66条保留明确占位。图片通过品牌官方CDN远程引用，品牌保留版权，不在源码包内再分发。

验证：105项测试、前端与Worker类型检查、516个静态HTML与21609条本地引用全部通过；390px手机布局及图片加载检查通过。来源、图片尺寸和完整缺口见源码内docs/MEDIA-EXPANSION.md、docs/official-media-report.json。本轮未调用付费模型。

## 价格来源与二手估算 — 2026-10-19

266/492条型号与地区记录至少有一种已核对价格信息：74条官网参考、152条发售参考、65条官方建议零售价，部分重叠。另有135条低置信度折旧模型情景估算，没有平台成交样本；不代表市场报价。226条没有足够依据填入数字，保持为空，未宣称全部价格已补齐。

在售状态、地区、基础配置、来源和核对日期分别展示；当前官网起价不自动当作同配置可购买报价，历史价、建议价和估算不用于硬预算推荐或真实差价。公开产品已移除早期演示数字，合成报价只存在测试夹具。

[查看价格方法与覆盖](https://max0220-22.github.io/digitalpick/pricing/) · [官网价格与发售价示例](https://max0220-22.github.io/digitalpick/products/ipad-air-11-m4/) · [旧款与二手估算示例](https://max0220-22.github.io/digitalpick/products/iphone-13/)

验证：112项测试、前端/Worker类型检查、517个静态HTML、23321条本地引用，390px手机排版检查通过。来源、计算方法和逐项缺口见源码内docs/PRICE-RESEARCH.md与docs/price-research-report.json。本轮未调用付费模型。

## 编码、图片过渡与小派参考推荐 — 2026-10-19

保留已确认的缺图占位文案。“暂未估算”采用完整Unicode常量，增加REDMI Book 16 2026（125H/1860g）卡片回归；源码和静态输出严格检查UTF-8、BOM与意外替换字符。修改前在Safari未复现该卡片乱码，没有把猜测写成已确认根因。

图片保留懒加载与原失败处理，新增骨架与模糊渐显；首页机型、分类、详情视图、素材库标签及下一页支持意图预加载，每次最多3图、总计32个地址去重，省流量及2G关闭预加载。

小派先给有来源的“核价备选”，明确非实时价格、购买前核实，再追问用途或全新/二手。参考池不等于通过当前购买报价审核，预算资格仍为false，不保证库存或预算内可买。虚构金额、未知ID与库存承诺仍被拦截，不改动硬预算规则推荐器。

验证：120项离线测试、前端/Worker类型检查、517个静态HTML、23321条本地引用及2637份导出文本编码检查。手机390px验证图片先骨架后就绪，lazy属性保留。细节见源码内docs/UX-IMPROVEMENTS.md。

预算复述与校验：允许在句首或句中复述带明确“预算”标签、金额与用户条件一致的预算，继续拒绝商品售价或不同金额。降级返回固定原因码，不记录或透传模型原文。首轮真实AI推荐通过；第二轮校验后本地接续，未视为两轮纯AI均通过。2次已授权验收已用完，后续补丁只做离线回归。

## FAQ、新人路径、收藏与清单分享 — 2026-10-19

首页新增12条FAQ和新人入口；[/start/](https://max0220-22.github.io/digitalpick/start/) 提供五步路径与22个可搜索术语。[/wishlist/](https://max0220-22.github.io/digitalpick/wishlist/) 在本机保存心愿设备，支持移除、对比和同源标签页同步；无需登录，不新增后端。产品列表、参数素材库与详情页均可收藏。

问卷结果和小派的机型推荐可复制纯文本清单，包含核价状态、来源日期与“基于演示数据，购买前请核实”。无合格结果时只分享需求与缺口；没有编造价格或候选。复制成功显示toast，受限时提供手动复制窗口。新增[开箱之后指南](https://max0220-22.github.io/digitalpick/guides/after-unboxing/)，覆盖激活检查、数据迁移和退货注意事项。

沿用现有静态导出发布，无新依赖或构建工具。128项离线测试、前端/Worker类型检查、520个静态HTML、24462条本地引用及2652份导出文本编码检查通过。390px深浅色、收藏刷新/跨标签页同步、搜索过滤与实际剪贴板复制已验收；未调用付费AI。设计参考与维护说明：源码内 `docs/STATIC-FEATURES.md`。

## 智能选购问卷分级预算修复 — 2026-10-20

问卷已接入独立价格资料：有效报价优先，缺报价时用来源明确的参考价/估算作规划，卡片标注“基于估算价”并显示配置、地区、来源和日期。先按原预算，无结果增加20%，仍无匹配时显示最近最多3款超预算备选及明确差额；系统、存储与用途条件保留。未入选列表逐台显示具体原因，空结果仍可复制需求和缺口。

138项测试、前端/Worker类型检查、520个静态HTML、24462条本地引用与2652份导出文本编码检查通过。已实际走完手机10000、手机3000、平板10000学习笔记、手机500四组问卷，验证估算标签、超预算差额、未入选原因和复制；390px深浅色无横向溢出。只有7款已有用途评级，其他型号不补造分数；无来源或配置无法确认仍可能为空。未调用付费AI或修改代理。详细说明见源码内 `docs/QUESTIONNAIRE-PRICE-FIX.md`。


## 下单确认区文案修复 — 2026-10-20

预算、实测范围及续航说明改为清晰完整的静态句子，每句一个文本节点，增大字号并使用实色阅读底板。142项测试及静态构建通过；500元场景三次刷新、动画后和深浅色切换后的DOM逐字一致，390px无横向溢出。修改前DOM未复现字序扰动，排查证据和验证边界保留于源码内 `docs/QUESTIONNAIRE-PRICE-FIX.md`。


## 同景日出主题 — 2026-10-20

首页在同一星河与小派模型上增加晨光天空和暖阳打光。导航日夜按钮、3D射线命中的小派与2D形象共用1.5秒过渡，保留聊天按钮、光标跟随和拖动；支持主题持久化、系统默认主题、首次提示及减少动态降级。主题切换不重建模型，文字区减星、铺阅读罩，日间使用浅色玻璃与深色文字。

151项测试、类型检查和静态构建通过。真实浏览器核对双向入口、连点锁、空白与拖动拒绝、Canvas实例稳定、一次性提示及390px布局。设计、存储键、降级策略与验收边界见源码内 `docs/DAY-NIGHT.md`。本轮未调用付费AI。


## 电影分镜日出升级 — 2026-10-21

同一条 1.6 秒时间轴编排屏息、天空溶解、方向光和界面配色；统一曝光衔接消除提前入夜的割裂感。日间增加太阳圆盘、轻光柱、两层高云、40 粒微尘、远山和 26 秒轨道光点；移动端微尘减半、保留一层云。夜间保留星河，并以 120px 渐隐处理 Hero 底部。

155 项测试、类型检查、520 页静态导出及 2654 份导出文本编码检查通过。浏览器验证四轮往返、模型不重建、390px 布局、2D 反馈、主题刷新保存和路由返回。所有持续氛围动画使用 rAF；不可见/减少动态时暂停。本机性能观察不代表所有设备的帧率保证。实现与验证边界见 `docs/DAY-NIGHT.md`。

# DigitalPick 数码指南

不买最贵的，只买最适合的。

中文数码购买决策网站，保留流动星河、3D小派、产品库、规则问答、验机清单与安全DeepSeek代理。

完整源码保存在 [digitalpick-source.zip](digitalpick-source.zip)，共187个项目文件，包含目录结构、测试和部署说明，不含密钥、环境文件、数据库、依赖或构建缓存。仓库通过GitHub网页上传，GitHub Actions自动解压源码后构建和发布。

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
- AI：独立Cloudflare Worker与SQLite Durable Object；Key只放Worker Secret。
- 仓库Actions Variable AI_PROXY_URL仅填写Worker公开HTTPS地址。
- 免费托管额度不包含DeepSeek模型调用费。所有数字示例价格仍是演示数据。
- 不要把任何API Key添加到NEXT_PUBLIC变量或提交到仓库。

更新网站：修改本地完整源码，运行测试后重新生成并上传digitalpick-source.zip，Actions会重新发布。不要把本地localhost预览产物直接上传到公网。

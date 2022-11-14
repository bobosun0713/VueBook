# 注意
1. Vite 已引入檔案必須加上副檔名

# 取得靜態資源
1. 不在public資料夾內的靜態資源，打包時會為檔名加上 hash，避免瀏覽器快取
2. public 不會加上 hash 只是把檔案複製到 build完成的 dist 資料夾內
> 使用方法
```
# 靜態資源放在 src/assets 時
new URL('/src/assets/xxx.png',import.meta.url).href

# 靜態資源放在 public 時
直接使用就行如 /xxx.png
```

# 環境變量
在 Vite 中取的環境變量方始:
1. 改用 import.meta.env （原本的 process.env 以不支持）
2. 取得 .env 文件變量前，前面開頭需要添加 VITE_ 來當作前綴字，否則會找不到
3. 可透過 vite.config.js 設置 envPrefix 來自定義前綴字
# 環境變數/模式/切換


## 內建的環境變數
1. import.meta.env.MODE (判斷目前模式，預設 development)
   > 如有設置 --mode 時，會顯示 --mode 所設定的參數
2. import.meta.env.BASE_URL (靜態資源的URL - 為 vite.config base 配置項)
3. import.meta.env.PROD (判斷是否為 prod 模式 - 執行指令: vite preview 為 prod 模式)
   > 執行指令為 package.json 裡的 script
4. import.meta.env.DEV  (判斷是否為 prod 模式 - 執行指令: vite 為 dev 模式)

## 環境變數取得方式
1. 改用 import.meta.env （原本的 process.env 以不支持）
2. 取得 .env 文件變量前，前面開頭需要添加 VITE_ 來當作前綴字，否則會找不到

<!--sec data-title="取得方式" data-id="section1" data-show=true ces-->
```js
import.meta.env.VITE_XXX

// 如果還是使用 webpack 為啟動專案，還是一樣使用 process
process.env.XXX
```
<!--endsec-->

3. 如要更改前綴字，可透過 vite.config.js 設置 envPrefix 來自定義前綴字開圖

<!--sec data-title="更改環境變數(前綴字)" data-id="section2" data-show=true ces-->
```js
// vite.config.ts
export default defineConfig({
  plugins: [vue()],
  envPrefix:"APP_", // 自定義開頭
})

// 取得方式(開頭需寫自定義前綴字)
import.meta.env.APP_XXX
```
<!--endsec-->


## 模式切換取得不同.evn檔
1. 可使用 --mode 來取得不同 .env檔
2. 當使用 --mode 來build專案時，如使用內建環境變量MODE時，會依照 build 的時候，如有設置 --mode 的參數時，就依照 --mode 參數顯示，如都未設置 --mode，預設顯示為 development 或  production

<!--sec data-title="使用 --mode 來取得不同 .env檔" data-id="section3" data-show=true ces-->
```json
// package.json 
"scripts": {
   "dev": "vite --mode dev",    //未指定默认取.env中的配置
 },

// 新建一個 .env.dev檔
VITE_DEV=test

// 取得方式(開頭需寫自定義前綴字)
import.meta.env.APP_XXX
```
<!--endsec-->
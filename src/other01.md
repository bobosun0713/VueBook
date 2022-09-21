# Vue Config環境設定

- Vue.config.silent （日誌與警告） true:關閉 false: 開啟

- Vue.config.devtools （ devtools檢查代碼） true:開 false:關

- Vue.config.productionTip （防止vue 在prod模式產生提示) true:開 false:關

- Vue.config.debug （錯誤警告） true:開 false: 關

> 生產環境下時，看個別需求是否要關閉以下功能！
   ```Javascript=
   if (process.env.NODE_ENV === "production") {
        Vue.config.devtools = false;
        Vue.config.debug = false;
        Vue.config.silent = true;
        Vue.config.productionTip = false;
    }
   ```


# Vite  專案部署到 Github Pages
1. 先定義一個 shell 腳本
   ```shell
   #!/usr/bin/env sh

   # abort on errors
   set -e

   # 這邊是執行 build 的動作，套件管理看個人習慣，這邊範例使用 pnpm 來做，預設 vite 打包完預設資料夾為 dist
   pnpm built

   # 切換 dist 資料夾底下
   cd dist

   # 執行 Git 基本操作
   git init
   git add -A
   git commit -m 'deploy'

   # 這邊網址要改為自己所建立的專案，也可以使用 SSH 看個人喜好 
   git push -f https://github.com/bobosun0713/SideProject-Spin_the_Wheel.git master:gh-pages

   # 返回上一次的做目錄
   cd -
   ```
2. 以上 shell 腳本建立好之後，需要去 vite.config.js 配置 base 選項，否則推到 Github Pages 上，會遇到資源檔抓不到的問題
   ```js
   import { defineConfig } from 'vite';
   import vue from '@vitejs/plugin-vue';

   export default defineConfig({
      // 注意！ 這邊是填寫要推的 Github branch 名稱
      base: '/SideProject-Spin_the_Wheel/', 
   });
   ```
3. 在 package.json 裡添加 script 指令
   ```json
   "deploy": "sh ./deploy.sh"
   ``` 

4. 執行 pnpm run deploy ，以上流程都沒出錯的話就大功告成！
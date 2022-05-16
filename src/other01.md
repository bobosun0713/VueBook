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
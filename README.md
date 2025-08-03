# 3D Parallax Mountain Website

這是一個使用 Vue 3 Composition API 和 Vite 構建的 3D 視差山脈網站。

## 功能特色

- 🏔️ 多層次山脈視差效果
- 🌫️ 霧氣層動態效果
- 🎯 滑鼠互動視差
- 📱 響應式設計
- ⚡ Vue 3 Composition API
- 🚀 Vite 快速開發

## 專案結構

```
3D-Parallax-Website-in-JavaScript/
├── index.html              # 主HTML檔案
├── package.json            # 專案依賴
├── vite.config.js          # Vite配置
├── home.vue               # 主頁面組件
├── src/
│   ├── main.js            # Vue應用入口
│   ├── App.vue            # 根組件
│   ├── config/
│   │   └── parallax-config.json  # 視差配置
│   └── section/
│       └── Mountain.vue   # 山脈視差組件
└── img/                   # 圖片資源
    ├── background.png
    ├── mountain_*.png
    └── fog_*.png
```

## 安裝與運行

### 1. 安裝依賴

```bash
npm install
```

### 2. 開發模式

```bash
npm run dev
```

這將在 `http://localhost:3000` 啟動開發伺服器。

### 3. 建置生產版本

```bash
npm run build
```

### 4. 預覽生產版本

```bash
npm run preview
```

## 技術架構

### Vue 3 Composition API
- 使用 `<script setup>` 語法
- 響應式資料管理
- 生命週期鉤子

### 視差效果實現
- 滑鼠位置追蹤
- 多層次視差計算
- 動態樣式綁定

### 配置管理
- JSON 配置檔案管理視差參數
- 分層視差效果
- 可調整的移動速度

## 視差層級

1. **背景層** (backgroundLayer) - 最慢移動
2. **低層山脈** (mountainLow) - 較慢移動
3. **中層山脈** (mountainMid) - 中等速度
4. **高層山脈** (mountainHigh) - 最快移動

## 自定義配置

可以在 `src/config/parallax-config.json` 中調整：
- 各層的移動速度
- 原始位置座標
- 層級倍數

## 瀏覽器支援

- Chrome 88+
- Firefox 85+
- Safari 14+
- Edge 88+

## 授權

MIT License
# F1 Race's Impact on City Sales: An Extended Analysis Project
# F1 賽事對城市旅遊銷售額影響分析：延伸專案

## 專案架構
```
f1-race-sales-analysis-project/
├── README.md                 <-- 專案報告，用 Markdown 格式撰寫
│
├── data/                     <-- 存放原始數據的資料夾
│   └── raw/
│       ├── f1_weekly_sales_by_city拷貝.csv
│       ├── google_trends_long_format.csv
│       ├── f1_event_products_template拷貝.csv
│       └── f1_dts_by_country_filled.csv
│
├── notebooks/                <-- 存放 Jupyter Notebook 檔案
│   └── f1_sales_analysis.ipynb  <-- 包含所有資料清理、分析與模型建立的程式碼
│
└── output/                   <-- 存放分析結果與視覺化圖表的資料夾
    ├── charts/
    │   ├── sales_comparison_by_week.png      <-- 賽事週與非賽事週銷售額比較圖
    │   └── trend_vs_sales_scatter.png        <-- 趨勢分數與銷售額的散佈圖
    └── model_results/
        └── regression_summary.csv            <-- 迴歸模型的詳細結果 (係數、p值等)
```
## 專案介紹
本專案是「F1 賽事對城市旅遊銷售額影響分析」的延伸。
本專案將證明 F1 賽事能顯著提升舉辦城市的銷售額，更進一步整合了多方數據（包括 Google 趨勢和消費者互動指標），建立預測模型。

## 專案目標
提供一套可行的商業策略，協助企業優化行銷決策，從而最大化賽事帶來的商業效益。

## 主要發現
- **舉辦賽事可帶來顯著的銷售增長**：賽事週的銷售額平均比非賽事週高出約 US$423，顯示 F1 賽事對當地經濟有直接的刺激作用。
- **在地化熱度是銷售關鍵**：模型的分析結果顯示，城市級別的 F1 搜尋趨勢與銷售額呈顯著正相關。這代表銷售增長主要受當地、即時的賽事熱度所驅動。
- **顧客參與度與銷售額密切相關**：產品評論數是另一個重要的銷售驅動力，反映了活躍的消費者群體能有效帶動銷售。
- **專案的最終預測模型**：我們成功建立了一個迴歸模型，可解釋 17.4% 的銷售額變動，並提供量化的洞察以指導策略制定。

## 數據來源
> **[點此查看各城市每週的銷售額數據及是否為比賽週的標示檔案](https://github.com/Debbylihii/F1-Race-Impact-on-City-Sales/blob/fce0230643b1716389ef13b585ca0b1d5318ad78/data/raw/f1_weekly_sales_by_city.csv)**<br>
> **[點此查看線上旅遊平台的產品數量和評論數](https://github.com/Debbylihii/F1-Race-Impact-on-City-Sales/blob/fce0230643b1716389ef13b585ca0b1d5318ad78/data/raw/f1_event_products_template.csv)**<br>
> **[點此查看包含國家層級的 F1 與 Drive to Survive 趨勢分數、GDP 等數據](https://github.com/Debbylihii/F1-Race-Impact-on-City-Sales/blob/fce0230643b1716389ef13b585ca0b1d5318ad78/data/raw/f1_dts_by_country_filled.csv)**<br>
> **[點此查看 F1 或相關資訊（如知名賽車手）在 2020-2024 年間的 Google 搜尋趨勢分數](https://github.com/Debbylihii/F1-Race-Impact-on-City-Sales/blob/fce0230643b1716389ef13b585ca0b1d5318ad78/data/raw/google_trends_long_format.csv)**<br>

## 資料處理與分析方法
  - **資料清理與整合**：將 f1_event_products_template 中的 race_location 欄位清理為標準化的城市名稱，以便與其他數據集合併。透過日期和城市欄位，將所有相關數據整合至一個主數據集中。
  - **描述性統計**：使用 t-檢定比較賽事週與非賽事週的平均銷售額，以驗證差異的統計顯著性。
  - **模型建立**：採用多元線性迴歸模型來預測銷售額。最初納入了「是否比賽週」、「城市 F1 趨勢分數」、「產品數量」、「評論數」、「國家 F1 趨勢分數」和「DTS 趨勢分數」等變數。
  - **經過模型驗證**：發現國家層級的趨勢分數在控制其他變數後並不具備統計顯著性，因此將其排除，以建立更精簡、更具解釋力的最終模型。

## 預測模型成果
  **最終模型方程式為**：> **[點此查看預測模型成果](model_results/regression_summary.csv)**<br>

## 商業建議
  **基於模型的洞察，提出以下優化行銷與營運的策略**：<br> 
   - **即時行銷策略**：在 F1 賽事舉辦前夕和賽事週期間，應將行銷資源集中在舉辦城市，並透過即時監控 Google 趨勢來優化廣告投放。<br>
   - **重視使用者體驗與口碑**：透過提供優質產品與服務，積極鼓勵消費者留下評論。產品評論數不僅是顧客滿意度的指標，也是驅動銷售的有效工具。<br>
   - **數據驅動的決策**：利用本模型作為基礎，可以對未來賽事舉辦地的潛在銷售額進行預測，為預算編列和產品上架提供數據支持。

## 未來展望
  **未來可進一步拓展本專案**：<br>
   - **擴充數據**：納入更多外部數據，如社群媒體聲量、機票預訂量或飯店入住率，以提升模型的準確性。<br>
   - **時間序列分析**：利用更複雜的模型來預測銷售趨勢，並考量賽事舉辦前的熱度爬升週期。<br>
   - **分群分析**：將不同特性的城市（如新興市場與成熟市場）進行分群，並針對性地建立模型，以提供更精準的行銷建議。

## 程式碼與工具
程式語言：Python
函式庫：pandas (數據處理), scikit-learn (機器學習), matplotlib / seaborn (資料視覺化)。
報告形式：專案程式碼與分析流程皆收錄於 Jupyter Notebook (.ipynb) 檔案中。

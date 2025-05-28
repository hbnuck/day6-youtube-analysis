# 📺 Day 6 - YouTube 資料分析與 SQL 整合

本針對 YouTube 影片資料進行探索性分析與視覺化，並結合 SQLite 進行資料查詢，強化資料庫操作能力。

## 🔍 資料來源
包含欄位有：
- Title（影片標題）
- Views（觀看數）
- Likes（喜歡數）
- Comments（留言數）
- Published At（上架時間）
- Keyword（關鍵字）

## 📊 主要分析項目
1. **觀看數前十影片**  
   - 使用 seaborn 畫出 barplot，觀察熱門影片分布  
   - 比較傳統 `plt.bar()` 和 `sns.barplot()` 差異

2. **觀看數與喜歡數的關聯性**  
   - 使用散佈圖搭配 `sns.regplot()`  
   - 計算相關係數 (約 0.7)，代表觀看數與按讚數呈現中度正相關

3. **各年份影片總觀看數變化**  
   - 把上架時間轉為年份，畫出時間折線圖，觀察趨勢

4. **留言與觀看數相關分析**  
   - 透過相關係數與散佈圖視覺化觀察

5. **影片關鍵字熱門程度分析**  
   - 將 `Keyword` 欄位以「|」分割
   - 計算各關鍵字對應的總觀看數，加總後取前15名畫長條圖

## 🗃️ SQLite 資料查詢
- 使用 `pandas.to_sql()` 將 DataFrame 寫入本地 `youtube.db`
- 查詢觀看數前十名影片：  
  ```sql
  SELECT Title, Views
  FROM video
  ORDER BY Views DESC
  LIMIT 10
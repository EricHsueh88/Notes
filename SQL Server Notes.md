# SQL Server 筆記

## Tips & Concepts
* 在`DELETE` data的時候，要將`WHERE` 寫在`FROM` 同一行 執行時會比較保險，或是在中間穿插一行`--SELECT *`在刪資料前做Double Check。
* 盡量用中括號來包中文或保留字作為欄位名稱時。
* 在做列出排名前3筆資料時，在第3筆和第4筆資料是相同時，可以用`SELECT TOP 3 WITH TIES [ColumnName]...`做到並列名次顯示。
* 一項作業就必須更新三個資料表，其中缺一不可，或是在交易連線時，需要 Transation Statements。
* 在欄位為`CHAR`，但內容又不足`CHAR`固定欄位時，會多出來的空白，使用`TRIM` 把空白拿掉。
* 在`CONVERT(VARCHAR,….)`時，`VARCHAR`預設是30，但最好先設定長度，EX：日期預設是10，2020/08/01。

## 快捷鍵
* 註解：`Ctrl  K`+ `Ctrl C`
* 取代：`Ctrl H`
* 關閉查詢結果：`Ctrl R`
* 查詢table欄位、型態：`ALT + F1`




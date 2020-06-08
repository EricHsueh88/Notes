# GIT 常用指令及觀念

### 開始專案協作流程：
>1. 將專案來源 **Fork** 一份至自己 **GITHUB** 上。
>2. (從自己的GITHUB ) **Clone** 至本地 **Local** 端。
>3. 將要協作的部份另外開 **Branch**。

### 拉取上游資料流程：
>將 **Branch** 切換至上傳分支，再做`git pull upstream <欲拉取之分支>`。

### 推送進度流程：
>將 **Branch** 切換至上傳分支，再做`git push origin <欲推送之分支>`。

### 檢查本地(Origin)鏈結與上游(Upstream)鏈結：
>`git remote -v` ，**-v**為非必要輸入，但加入後能完整看見網址加以確認。
>

### 製作Commit
>1.在版本提交後又更改的檔案尚未被GIT追蹤，列入**Untracked Area**。  
>2.`git add` 後列入**Staging Area**(等待commit區)。  
>3.`git commit -m "description"`，將更改**Commit**至儲存區**(Repo**)。  
>4. 可使用`git commit -a -m "description"` 來同時**add** 和 **commit**。
### Branch 分支：
- 檢查分支：`git branch`
- 切換分支：`git checkout <branch>`
- 新增分支：`git branch <branch>`，在當下的分支去延伸。
- 刪除分支：`git branch -d <branch>`


### 檢視提交的歷史紀錄：
使用 `git log`以反向時間來檢視提交紀錄，可搭配指令有 
- `-p`：用來顯示每筆提交所做的修改內容。
- `-n`：指定輸出最後n筆紀錄。
- `--oneline`：將輸出結果以一筆一行呈現。
- `--graph`：會有分支顏色提示。
- `--grep=""`：可以從Commit訊息裡搜尋符合字樣內容。
- `--committer`：列出提交者名字符合指定字串的提交。

## Commit Part

### 追加檔案至最近的Commit
1.先將位於**Working Directory**的檔案`add`至**Staging Area**。  
2.`git commit --amend --no-edit`即可。

### 修改Commit紀錄：
- `git commit --amend -m "description"`：修改最後一筆Commit紀錄的訊息。但所做的更改Git會生成新的Commit物件。

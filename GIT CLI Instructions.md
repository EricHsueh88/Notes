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

### Branch 分支：
- 檢查分支：`git branch`
- 切換分支：`git checkout <branch>`
- 刪除分支：`git branch -d <branch>`
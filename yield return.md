# C# yield 用法

### 用於回傳IEnumerable<T>

相較於Foreach Iterator(迭代器)，會歷遍所有元素並存入內存才回傳；若用yield return 回傳，執行到yield return 時，會處理以下三件事情：
- Iterator block 暫停
- current 更新為 yield return 的 value
- foreach 的MoveNext() 回傳true

而foreach在執行完embedded_statement後再次觸發MoveNext()時會從原本暫停的地方再執行下去直到Iterator Block中的程式:

- 再次觸發yield return
- 執行結束
- yield break

---
參考資訊：

https://blog.51cto.com/u_14316983/2806430
https://ithelp.ithome.com.tw/articles/10193586
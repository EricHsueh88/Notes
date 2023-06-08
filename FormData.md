## FormData 特性


#### 作為API的資料傳遞方式之一的資料型態，有類似於Dictionary中KeyValuePairs屬性，以下為[應用方式](#應用方式)及[注意事項](#注意事項)

---

### 應用方式
 以下列舉 **一般物件** 及**Class物件**用法

  * **一般物件**
    ex. 刪除組織中的某些單位所有人員
    >Server
    [HttpDelete]
    ``` cpp
    public List<string> Employees([FromForm] string org, [FromForm] List<string> units){...} 
    ```
    >Client
    ``` cpp 
    let form = new FormData();
    form.append('org','team_a');
    units.forEach((unit,idx)=>{
       form.append('units',unit); 
    });
    
    fetch(url,{
        body:form,
        method:'Delete'
    });
    ```
* **Class物件** 

    ex. 新增單筆員工資料
    >Server
    ``` cpp
    [HttpPost]
    public List<string> Employee([FromForm] Employee emp, [FromForm] IFormfile empAvatar){...} 

    // 員工
    public class Employee {
        public int id {get;set;}
        public string gender {get;set;}
        public string name {get;set;}
        public string ext {get;set;}
    }
    ```
    >Client
    ``` cpp 
    let form = new FormData();
    form.append('emp[gender]','F');
    form.append('emp[name]','Martin')
    form.append('empAvatar', file);
    
    fetch(url,{
        body:form,
        method:'POST'
    });
    ```
    ex. 更新多筆員工分機
    >Server
    ``` cpp
    [HttpPut]
    public List<string> Employees([FromForm] List<Employee> emps, [FromForm] List<IFormfile> empAvatars){...} 
    ```
    >Client
    ``` cpp 
    let form = new FormData();
    listData.forEach((item,idx)=>{
        form.append('id',`emps[Employee[${i}][item.id]]);
        form.append('ext'`emps[Employee[${i}][item.ext]]);
    });
    
    fetch(url,{
        body:form,
        method:'PUT'
    });
    ```
---
### 注意事項
- 若Client端傳```null```值，則Server端使用```string```或```string?```接，會接到```"null"```而非```null```




# **JMeter 壓測工具**
### **Installed**
* Java 8+ 
  <https://www.oracle.com/java/technologies/javase/jdk19-archive-downloads.html>
* JMeter 
<https://jmeter.apache.org/download_jmeter.cgi>
---
## **Setup**
### **Create Thread Group**
::: success 
Test Plan >Add > Treads(Users)> TreadsGroup
:::

::: spoiler view pic
![](https://i.imgur.com/pqmsJVC.png)
:::

### **Step2.** Pressure Settings

#### **Thread Properties**
::: info 
* Number of Threads(users):Number of users usage in the same time.
* Ramp-up period(seconds):Test Period
:::

::: spoiler view pic
![](https://i.imgur.com/EsgqJ3b.png)
:::
### **Add View Result**
::: success
Thread Group > Add > Listeners > View Result Tree 

==tips:==<font color="red"> There're different type of Result Presentation, tree is one of clearest of them, you can also add multiple result types as well </font>
:::

::: spoiler view pic 
![](https://i.imgur.com/5wknlgo.png)

:::

### **Create & Settings HTTPS(S) Test Script Recorder**

* **Create** 
  ::: info
  Test Plan > Add > Non-Test Elements > Test Script Recorder
  :::
  

  
  ![](https://i.imgur.com/slwXbKS.png)



* **Configuration**
  ::: info 
  HTTPS Domains：Domain Name Which you test
  Target Controller: Toggle target controller by     dropDown
  :::

  ![](https://i.imgur.com/aOOcgqi.png)
  
*  **SSL Settings (==OPTIONAL==)**
  ::: info 
  If your target website set HSTS, the CA is necessary in this scenario.\
 And Here's the demostrate for generate self-certificate through command line below.
  :::
  **1. generate Keypair from RSA into proxyserver.jks file**
 
 > cmd script : \
 > keytool -genkeypair -alias `<root.ca>` -dname `
 "CN=_JMeter Root CA for recording (INSTALL ONLY IF IT'S YOURS), OU=Username: yuan_lin, C=TW"` -keyalg `<RSA>` -keystore `<proxyserver.jks>` -storepass `<password>` -keypass `<password>`-validity `<7>`\
 
 * **Param Description**
   * keytool : Java 提供的密鑰和證書管理工具。
   * -genkeypair : 生成一個密鑰對（包括公鑰和私鑰）
   * -keyalg `RSA` : 指定使用的加密演算法
   * -storepass `password` : 用於保護密鑰庫的密碼
   * -keypass `password`:保護私鑰的密碼
   * -validity `7`: 簽章時效(天)

 **2.try another way like export crt from website than set into jmeter ssl manager**
 


###  **Recording Controller**
::: success
Thread Group > Add > logic Controller > Recording Controller
:::

![](https://i.imgur.com/EfQ6URz.png)

\
==tips:若有需要登入Authorization資料(ex:token..)可利用Extractor來將登入成功回傳token，寫入變數中==

* **Extractor Config(提取器設定)**
  ::: success 
  Recording Controller - HTTP Request > Add > Post Processors >     Regular Expression Extractor
  :::
  ::: info 
  **Regular Expression Extractor Config**\
  Field to Check(資料來源)\
  Name of created variable(變數名稱)\
  Regular Expression(正規表達式)\
  Template(位置):`$1$`
  
  :::

    ![](https://i.imgur.com/7cGpWsC.png)
    create 
    
    ![](https://i.imgur.com/xWrOlNt.png)
    Authorization settings
  
* **Request Header Config(請求標頭設定)**
  ::: success 
  Recording Controller - HTTP Request(doule click) > HTTP Header Manager > parameterize header value (refer extractor param) 
  :::
 

  ![image](https://hackmd.io/_uploads/SkAj-O-NC.png)


---
## **Usage**

1. **Setting HTTP Proxy Server**
2. **Record Test Activity**
3. **Run Test**
4. **Export Result**

### **Step1.** Setting HTTP Proxy Server
:::info
**Option A** (Setting on Browsers . <font color="red">FireFox Limit</font>)
1. Settings > Search "Proxy" in keyword
2. Open ConnectionSettings 
3. select "Manual proxy configuration", enter "localhost" for HTTP Proxy, and "8888" for Port.

**Option B (Settings PC Proxy)** 
1. Windows Settings  > Network & internet > Proxy
2. Use setup script
3. Proxy Address : http://localhost, Port：8888
:::

::: spoiler view pic 
![](https://i.imgur.com/QXdpeVI.png)
FireFox Proxy Settings
![](https://i.imgur.com/bfGvL7Q.png)
Proxy Settings From PC
:::


### **Step2.** Record Test Activity
:::info
1. Click `HTTP(S) Test Script Recorder`
2. Set HTTPS Domains : <your test domain>, Port:8888
3. Toggle Target Controller to the `<Your recording controller>`
4. Click start button to start recording 
5. Start using your website
6. Click stop to end recording
:::


![](https://i.imgur.com/FzXKQ6N.png)
Test Script Recorder

    
### **Step3.** Run Test
:::info
1. Click Start in Toolbar
2. Check test result in View Results Tree
:::


![](https://i.imgur.com/uIoVNUM.png)
Test Run & View Result
    
### **Step4.** Export Result
:::info
1. Run Script to Export \
jmeter -n -t `<source jmx filepath(include source.jmx)>` -l `~\<result name>.jtl` -e -o `<result dest path>`
    
**Example**    
> jmeter -n -t C:\Users\eric_hsueh\Desktop\buzuJMeter\NewPortal.jmx -l C:\Users\eric_hsueh\Desktop\buzuJMeter\NewPortalResult.jtl -e -o C:\Users\eric_hsueh\Desktop\buzuJMeter\NewPortalResult
:::

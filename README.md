# 發行自己的虛擬貨幣(ERC20 Token)
### 智能合約 Smart Contract：
簡單地來說，智能合約（smart contract）是區塊鏈中一種制訂合約時所使用的特殊協議，主要用於提供驗證及執行智能合約內所訂定的條件。智能合約中內含了程式碼函式，亦能	與其他合約進行互動、做決策、儲存資料及傳送以太幣等功能。：

### 測試網路 Test Network
區塊鏈的一個特性是上鏈的資料與程式碼都不可更改，所以我們需要一個測試環境，對我們寫好的智能合約進行各種測試，盡量減少出錯的狀況。

### 區塊鏈錢包 Blockchain Wallet：
任何人要在區塊鏈上互動，例如：提交轉帳需求、查看資產狀況、部署智能合約等，會需要一個溝通工具，就是區塊鏈錢包。




## 為什麼Token需要ERC20?
### Token是甚麼?

Token 只是以太坊智能合約的一種應用，可以想像這種代幣只是存在於某個智能合約中的紀錄，這個合約上記載著每個以太坊地址擁有的 Token 數量多寡，


### Token 為何需要ERC20?
而每次的轉移都是呼叫原本創建 Token 合約裡面的 Function 去做改動，在創建 Token 時，可以自由訂定規則，像是我可以制定一種完全無法轉移的 Token(就像是宣告一個參數而不使用)，但這樣的設計， Token 就變得沒有價值傳遞的意義存在，因此為了要讓Token能擁有合理的貨幣機制，才會有 ERC20 被設立。往後我們只要知道，若是一個 Token 符合 ERC20，即代表他是一種具有完整貨幣交易功能的代幣。

####與ERC-721的差別
ERC-721 標準規定了符合它這種標準的每個 Token 都有唯一的 Token ID。在 ERC-721 標準裡，每個 Token 都是獨一無二的



### 前置作業
1. 有自己的以太坊區塊鏈錢包。

2. 需要有Ropsten測試鏈的 Ether(Matamask有教)

3. 發行代幣的程式碼(等等會教)

4. 智能合約部署平台。

### 1.從測試鏈水龍頭(水管)取得 Ropsten測試鏈的乙太幣
在區塊鏈上，除了查詢資料之外的互動，例如：轉帳、部署智能合約，啟動智能合約內的功能等，基本上都是需要花費原生加密貨幣，所以在發行代幣之前，我們需要先取得Ropsten測試鏈的乙太幣，接下來我以MetaMask錢包來示範，如何取得：

![image](https://user-images.githubusercontent.com/62298086/157822943-7b9f3654-7856-45a3-8512-5bd3563432ed.png)


什麼是水龍頭(水管)？簡單說就是給你領取免費加密貨幣的管道。

有些水龍頭網站會放置廣告，以免費送加密貨幣為號召，吸引廣大用戶進入水龍頭網站瀏覽廣告，因而有廣告收入。對於測試鏈而言，主要是為了提供無成本的測試環境給開發者，於是透過測試鏈水龍頭，提供免費的測試鏈加密貨幣，讓開發者可以使用。

(補充)如果你身上有過多的乙太幣 測試鍊不會發給你歐
![image](https://user-images.githubusercontent.com/62298086/157823041-9272d5ff-458b-4dd8-bf4b-609dee89e960.png)


### 2.設定你的代幣程式碼
至https://remix.ethereum.org/ 部屬及測試合約
1.輸入自己想要的合約名稱
![image](https://user-images.githubusercontent.com/62298086/157823190-b6581315-58e2-4480-9dbd-6e5c59ac1df0.png)

### 複製token程式碼，我已放在這個庫中

### 3.修改程式碼
程式代碼有一段
![image](https://user-images.githubusercontent.com/62298086/157823355-acc6b03f-fd9d-4c8e-871c-52a68026fb49.png)
symbol: 幣的代號
name: 幣的名稱(可以用中文)
decimals: 小數點位數
_totalSupply: 總發行量
0x你的錢包：請務必改成你自己的錢包位置(ps錢包位置可從metamask查看)



### 4.進行compile，注意版本最好相近，成功會出現綠勾勾

![image](https://user-images.githubusercontent.com/62298086/157823596-bbb3f266-c859-4f4f-90ec-ca130a5562cc.png)

### 5.發佈合約，Deplay如果成功會跑出metamask要你付錢

記得修改成 inject web 3，因為我們要用metamask
![image](https://user-images.githubusercontent.com/62298086/157823743-58bf314f-b315-4bb4-ab09-70296cf2bc38.png)

Web3
它是一個函式庫，他把以太坊的 JSON-RPC API  (你代幣的程式碼) 重新封裝過，並添加一下實用的函式庫，常用於 Dapp (去中心化的app)網站的前端部分。


![image](https://user-images.githubusercontent.com/62298086/157823867-0d10afc7-fa2a-4085-8ee6-904345b0112a.png)
什麼是燃料價格？(GWEI)
就每單位 Gas 願意付出多少 ETH，一般使用 Gwei 作為單位 Gwei=0.000000001Eth(也就是一個ether可以=10億個GWEI)
如果你想在交易上更快被礦工驗證打包的話，Gas Price(Gwei) 就需要調整越高越好，但如果想要花費較少，您可以通過降低您支付每單位 Gas 的金額來實現。所以您為每個單位支付的價格會增加或減少交易的開採速度(也就是你的資料上鍊時間會變慢)。

什麼是燃料限制？(Gas Limit):
Gas Limit 被稱為 Limit，因為它是你願意花費在交易上的最大數量的 Gas 單位。這樣可以避免合約中出現錯誤的情況。然而，如果你不想在 Gas 上花費太多，降低 Gas Limit 並不會有多大幫助。您必須包含足夠的 Gas 來涵蓋您使用的計算資源，否則您的交易將因 Out of Gas 而失敗。




![image](https://user-images.githubusercontent.com/62298086/157824004-43d1557d-54e1-4249-bd5e-c710fa84ce90.png)
你已經成功將你自創的代幣上以太坊Ropsten測試鏈了

然後，初次發行的代幣會先轉給發行者(你)
！於是我們要利用MetaMask錢包去掛載你發行的虛擬貨幣並，順便試用轉帳功能


![image](https://user-images.githubusercontent.com/62298086/157824057-3716ebbe-26ea-4789-8362-46984c23e2ec.png)

![image](https://user-images.githubusercontent.com/62298086/157824078-d17e4f6d-a4e7-4498-bddc-a5621b35fa2e.png)

![image](https://user-images.githubusercontent.com/62298086/157824106-a6f2835d-5c7a-449b-90bd-b99c478bbe2f.png)

![image](https://user-images.githubusercontent.com/62298086/157824130-7f4663c6-dc0e-46ce-b845-9db2839cacc5.png)

![image](https://user-images.githubusercontent.com/62298086/157824161-ffece938-6ec2-43a4-ae85-a7084f7870bc.png)

![image](https://user-images.githubusercontent.com/62298086/157824192-ff376135-5c16-4bea-bc82-24180a9be9d6.png)

### 補充:程式碼解釋
![image](https://user-images.githubusercontent.com/62298086/157824236-d4553d6a-b7ce-4785-9e69-a0baba8ba76a.png)
1.首先會先看到Solidity的版本

2.Safemath主要是在協助簡單的四則運算避免出錯，你可以發現Safemath主要是為了處理數學運算規範，帶有安全檢查，以避免整數運算後溢位的情形。


再來是ERC20的通用標準，裡面內容包含
totalSupply（） –用於獲取ERC-20token的token總供應量。

balanceOf（） –跟踪每個以太坊錢包中的代幣餘額。

transfer（） –創建token後，此函數可以將所有token發送到一個錢包或將其分發給ICO投資者。

transferFrom（） –使token持有者能夠在初始分配之後彼此交換token。

approve（） –用於“批准”其他帳戶以從調用該函數的帳戶中提取一定數量的token。

allowance（） –使用approve（）之後，allowance（）用於查看允許批准的帳戶從原始帳戶中提取的代幣數量。

![image](https://user-images.githubusercontent.com/62298086/157824345-580efbe3-a0d2-414a-97ca-d9d331bd8ab3.png)
MINIMEtoken是一個可複製的，ERC 20token。它的目的在於使任何開發人員都可以在不影響原始token的情況下為token持有者提供額外的功能。

Owend 
用於指定合約的擁有者


![image](https://user-images.githubusercontent.com/62298086/157824411-675d27e0-dd06-4ee6-a20e-4a392ab5e20b.png)
開始創建自己的ERC20 TOKEN，並規範其帶有符號，名稱和小數以及最大總供給量


在此編輯自己的ERC 20 TOKEN，下列之後的所有程式碼皆在描述此ERC20之標準




![image](https://user-images.githubusercontent.com/62298086/157824460-96288d0e-82ac-46c4-828a-5c04a02d9e66.png)
實作前面ERC20Interface的程式碼


totalSupply（） :用於獲取ERC-20 token的token總供應量

balanceOf（） :每個以太坊錢包中的代幣餘額

transfer（） :創建token後，定義如何將token發送到錢包

approve（） :用於”批准”其他帳戶以從調用該函數的帳戶中，提取token (存取控制)

transferFrom（） 
讓contract有權力讓其他使用者使用


實作前面ERC20Interface的程式碼



![image](https://user-images.githubusercontent.com/62298086/157824518-5928c65b-dad7-40c1-8e1d-d1131ae1c064.png)
![image](https://user-images.githubusercontent.com/62298086/157824558-99186c3d-d88e-48f6-98cd-710efe99e41e.png)


參考資訊
https://blog.toright.com/posts/6347/%E4%BB%A5%E5%A4%AA%E5%9D%8A%E6%89%8B%E6%8A%8A%E6%89%8B%E7%99%BC%E5%B9%A3%E6%95%99%E5%AD%B8-%E5%89%B2%E9%9F%AD%E8%8F%9C%E8%B5%B7%E6%89%8B%E5%BC%8F.html






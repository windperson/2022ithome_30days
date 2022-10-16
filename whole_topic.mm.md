# Orleans 基本概念與功能介紹
## *基本概念*
### Virtual Actor Model平行運算模型
### Grain
### Silo
### Cluster
### Client
## *開發(dev)功能*
### Grain宣告方法
#### 傳統繼承Grain母類別方式宣告
#### POCO Grain (.NET 7+)
### RPC呼叫
#### 單元測試
#### 使用.NET Interactive Jupyter Notebook測試
#### .NET Core依賴注入(DI)
#### Exception Handling
### 資料儲存
#### Grain狀態儲存機制
#### 官方支援Storage Provider
##### In-Memory
##### Azure Blob/Table Storage (No-SQL)
##### ADO.NET Storage Provider (SQL-based DB)
### 自動觸發執行
#### Timer
#### Reminder
### 事件/資料流非同步驅動
#### Observer
#### Streaming
##### 官方支援Stream Provider
* Azure Queue
* Azure Event Hub

nuget: [Microsoft.Orleans.OrleansServiceBus](https://www.nuget.org/packages/Microsoft.Orleans.OrleansServiceBus)

### 跨多Grain實體之交易機制(ACID Transaction)
https://thenewstack.io/microsoft-orleans-brings-distributed-transactions-to-cloud/

### Grain其他進階功能/設定
#### One-Way request
https://docs.microsoft.com/en-us/dotnet/orleans/grains/oneway
#### Grain Call filter/Interceptor
https://docs.microsoft.com/en-us/dotnet/orleans/grains/interceptors
Usage:  
    * Authentication
    * As a logging mechanism:
      https://github.com/Expecho/Orleans.Telemetry.ApplicationInsights
#### Reentrancy
https://docs.microsoft.com/en-us/dotnet/orleans/grains/reentrancy
Purpose:   
    * Prevent Deadlock
    * Improve RPC invocation Performance
#### Grain RPC Interface Versioning

#### GrainService
https://docs.microsoft.com/en-us/dotnet/orleans/grains/grainservices
Special system daemon service that act like stateless worker, not recommended to use for business logic

#### Stateless Worker
https://docs.microsoft.com/en-us/dotnet/orleans/grains/stateless-worker-grains
#### Grain Directory (Cluster Membership) hosting
https://docs.microsoft.com/en-us/dotnet/orleans/host/grain-directory
##### Azure Table
##### Redis
##### Consul (v4.0+)
https://www.nuget.org/packages/Microsoft.Orleans.Clustering.Consul/4.0.0-preview2

## *運營(ops)功能*
### Hosting Environment
#### TestCluster
#### ASP.NET Core Co-Hosting
#### .NET Generic Hosting
### Azure Blob Storage/Table/Queue Provider configuration
### ADO.NET provider configuration
### Server GC configuration
### DI(Dependency Injection) registration
### Logging & Telemetry
### HealthCheck
#### 與ASP.NET Core HealthCheck機制整合
### StartupTask
## *主機架設套件＆第三方開源元件*
### Providers
#### [Orleans Redis Providers](https://github.com/OrleansContrib/Orleans.Redis)
##### [Orleans.Persistence.Redis](https://www.nuget.org/packages/Orleans.Persistence.Redis)
##### [Orleans.Clustering.Redis](https://www.nuget.org/packages/Orleans.Clustering.Redis)
##### [Orleans.Reminders.Redis](https://www.nuget.org/packages/Orleans.Reminders.Redis)
#### [Orleans.Providers.MongoDB](https://github.com/OrleansContrib/Orleans.Providers.MongoDB)
#### [Orleans.Stream.Kafka](https://github.com/jonathansant/Orleans.Streams.Kafka)
### [OrleansDashboard](https://github.com/OrleansContrib/OrleansDashboard)
### [SignalR.Orleans](https://github.com/OrleansContrib/SignalR.Orleans)
### [OrgnalR](https://github.com/LiamMorrow/OrgnalR)

# Orleans 整合應用及部署上雲

## *整合[Polly](https://dotnetfoundation.org/projects/polly)智慧重試RPC呼叫*

## *常見系統架構模式*
### Smart Cache Pattern

https://github.com/OrleansContrib/DesignPatterns/blob/master/Smart%20Cache.md
Example: Url Shortener

### Dispatch Pattern

https://github.com/OrleansContrib/DesignPatterns/blob/master/Dispatcher.md
Example: Online polling system

### Observer Pattern

https://github.com/OrleansContrib/DesignPatterns/blob/master/Observer.md
Example: Chatting system backend

### Cadence Pattern

https://github.com/OrleansContrib/DesignPatterns/blob/master/Cadence.md
Example: IoT sensor data processing

### Registry Pattern

https://social.technet.microsoft.com/wiki/contents/articles/51018.registry-pattern-using-microsoft-orleans.aspx
Example: Shopping cart

### Reduce Pattern

https://github.com/OrleansContrib/DesignPatterns/blob/master/Reduce.md
Example: Leader board System
## *Azure上雲部署*
### Azure Web App(PaaS)
#### Single Silo Hosting
#### Multiple Silo Instance(s) Hosting
### AKS(Kubernetes)
### Azure Container Apps
#### KEDA autoscaling

---
title: "代替パイプをリッスンするサーバーの構成 (SQL Server 構成マネージャー) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "名前付きパイプ [SQL Server], 構成"
  - "リッスン [SQL Server], パイプ"
  - "パイプ [SQL Server], 代替"
  - "代替パイプ [SQL Server]"
ms.assetid: 914f7491-e2be-4b0d-b3aa-fe5409cdbafa
caps.latest.revision: 29
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 29
---
# 代替パイプをリッスンするサーバーの構成 (SQL Server 構成マネージャー)
  このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で SQL Server 構成マネージャーを使用して、代替パイプをリッスンするようにサーバーを構成する方法について説明します。 既定では、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] の既定のインスタンスは、名前付きパイプ \\\\.\pipe\sql\query をリッスンします。 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]および [!INCLUDE[ssEW](../../includes/ssew-md.md)] の名前付きインスタンスは、他のパイプをリッスンします。  
  
 クライアント アプリケーションを使用して特定の名前付きパイプに接続するには、次の 3 つの方法があります。  
  
-   サーバーで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスを実行します。  
  
-   クライアントで、名前付きパイプを指定して別名を作成します。  
  
-   クライアントで、カスタム接続文字列を使用して接続するように指定します。  
  
##  <a name="SSMSProcedure"></a> SQL Server 構成マネージャーの使用  
  
#### SQL Server データベース エンジンによって使用される名前付きパイプを構成するには  
  
1.  SQL Server 構成マネージャーのコンソール ペインで、**[SQL Server ネットワークの構成]** を展開し、*\<instance name>* **のプロトコル**を展開します。  
  
2.  詳細ペインで **[名前付きパイプ]** を右クリックし、**[プロパティ]** をクリックします。  
  
3.  **[プロトコル]** タブで、 **[パイプ名]** ボックスに [!INCLUDE[ssDE](../../includes/ssde-md.md)] によってリッスンされるパイプを入力し、 **[OK]**をクリックします。  
  
4.  コンソール ペインで、 **[SQL Server のサービス]**をクリックします。  
  
5.  詳細ペインで **[SQL Server (**\<instance name>**)]** を右クリックします。次に、**[再起動]** をクリックして [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を停止し、再起動します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が代替パイプをリッスンしている場合、クライアント アプリケーションを使用して特定の名前付きパイプに接続するには次の 3 つの方法があります。  
  
-   サーバーで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスを実行します。  
  
-   クライアントで、名前付きパイプを指定して別名を作成します。  
  
-   クライアントで、カスタム接続文字列を使用して接続するように指定します。  
  
## 参照  
 [クライアントが使用するサーバーの別名の作成または削除 &#40;SQL Server 構成マネージャー&#41;](../../database-engine/configure-windows/create or delete a server alias for use by a client.md)   
 [サーバー ネットワークの構成](../../database-engine/configure-windows/server-network-configuration.md)  
  
  
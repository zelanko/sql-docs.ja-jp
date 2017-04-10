---
title: "ステージング ストアド プロシージャ (マスター データ サービス) | Microsoft Docs"
ms.custom: ""
ms.date: "04/01/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6a613106-9f87-4caf-a23a-a726fc6561c5
caps.latest.revision: 15
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 15
---
# ステージング ストアド プロシージャ (マスター データ サービス)
  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] からステージング処理を開始する場合、次の 3 つのストアド プロシージャのいずれかを使用します。  
  
-   stg.udp_\<名前>_Leaf  
  
-   stg.udp_\<名前>_Consolidated  
  
-   stg.udp_\<名前>_Relationship  
  
 name は、エンティティの作成時に指定されたステージング テーブルの名前です。  
  
## ステージング処理ストアド プロシージャのパラメーター  
 次の表では、これらのストアド プロシージャのパラメーターの一覧を示します。  
  
|パラメーター|Description|  
|---------------|-----------------|  
|**VersionName**<br /><br /> 必須|バージョンの名前。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] コレクションの設定に応じて、このパラメーターは大文字と小文字が区別される場合とされない場合があります。|  
|**LogFlag**<br /><br /> 必須|ステージング処理中にトランザクションをログに記録するかどうかを決定します。 有効な値は次のとおりです。<br /><br /> **0**: トランザクションをログに記録しない。<br /><br /> **1**: トランザクションをログに記録する。<br /><br /> <br /><br /> 詳細については、「[トランザクション (マスター データ サービス)](../master-data-services/transactions-master-data-services.md)」を参照してください。|  
|**BatchTag**<br /><br /> Web サービス以外は必須|ステージング テーブルに指定した **BatchTag** の値。|  
|**Batch_ID**<br /><br /> Web サービスでのみ必須|ステージング テーブルに指定した **Batch_ID** の値。|  
|**[ユーザー名]**|省略可能なパラメーター|  
|**[ユーザー ID]**|省略可能なパラメーター|  
  
### ステージング処理ストアド プロシージャの例  
 次の例は、ステージング ストアド プロシージャを使用してステージング処理を開始する方法を示します。  
  
```  
USE [DATABASE_NAME]  
GO  
  
EXEC[stg].[udp_name_Leaf]  
      @VersionName = N'VERSION_1',  
@LogFlag = 1,  
@BatchTag = N'batch1'  
      @UserName=N’domain\user’  
  
GO  
  
```  
  
## 参照  
 [検証ストアド プロシージャ (マスター データ サービス)](../master-data-services/validation-stored-procedure-master-data-services.md)   
 [ステージング中に発生したエラーの表示 (マスター データ サービス)](../master-data-services/view-errors-that-occur-during-staging-master-data-services.md)  
  
  
---
title: "[Master ストアド プロシージャ転送タスク エディター] ([ストアド プロシージャ] ページ) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.transferstoredprocedurestask.storedprocedures.f1"
helpviewer_keywords: 
  - "ストアド プロシージャ転送タスク エディター"
ms.assetid: 5fcf171e-cc0b-4c24-8eb5-3a4b4775e64a
caps.latest.revision: 20
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 20
---
# [Master ストアド プロシージャ転送タスク エディター] ([ストアド プロシージャ] ページ)
  **[Master ストアド プロシージャ転送タスク エディター]** ダイアログ ボックスの **[ストアド プロシージャ]** ページを使用すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の 1 つのインスタンスの **master** データベースから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の別のインスタンスの **master** データベースに、1 つ以上のユーザー定義ストアド プロシージャをコピーする場合のプロパティを指定できます。 このタスクの詳細については、「 [Transfer Master Stored Procedures Task](../../integration-services/control-flow/transfer-master-stored-procedures-task.md)」を参照してください。  
  
> [!NOTE]  
>  このタスクは、コピー元のサーバーの **master** データベースからコピー先のサーバーの **master** データベースに、**dbo** が所有しているユーザー定義のストアド プロシージャのみを転送します。 コピー先のサーバーでストアド プロシージャを作成するには、そのサーバーの **master** データベースの CREATE PROCEDURE 権限を取得するか、そのサーバーの **sysadmin** 固定サーバー ロールのメンバーである必要があります。  
  
## オプション  
 **SourceConnection**  
 SMO 接続マネージャーを一覧から選択するか、**[\<新しい接続>]** をクリックしてコピー元のサーバーへの新しい接続を作成します。  
  
 **DestinationConnection**  
 SMO 接続マネージャーを一覧から選択するか、**[\<新しい接続>]** をクリックしてコピー先のサーバーへの新しい接続を作成します。  
  
 **[IfObjectExists]**  
 コピー先のサーバーの **master** データベースに存在する名前と同じ名前を持つ、ユーザー定義ストアド プロシージャの処理方法を選択します。  
  
 このプロパティには、次の表に示すオプションがあります。  
  
|値|Description|  
|-----------|-----------------|  
|**[FailTask]**|ストアド プロシージャがコピー先のサーバーの **master** データベースに既に存在する名前と同じ名前を持つ場合、タスクは失敗します。|  
|**Overwrite**|コピー先のサーバーの **master** データベースにある同じ名前のストアド プロシージャを上書きします。|  
|**Skip**|コピー先のサーバーの **master** データベースにある同じ名前のストアド プロシージャをスキップします。|  
  
 **[TransferAllStoredProcedures]**  
 コピー元のサーバーの **master** データベースのすべてのユーザー定義ストアド プロシージャをコピー先のサーバーにコピーするかどうかを選択します。  
  
|値|Description|  
|-----------|-----------------|  
|**True**|**master** データベースのユーザー定義ストアド プロシージャをすべてコピーします。|  
|**False**|指定したストアド プロシージャのみをコピーします。|  
  
 **[StoredProceduresList]**  
 コピー先の **master** データベースにコピーする、コピー元サーバーの **master** データベースのユーザー定義ストアド プロシージャを選択します。 このオプションは、 **[TransferAllStoredProcedures]** を **[False]**に設定した場合のみ使用できます。  
  
## 参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../integration-services/integration-services-error-and-message-reference.md)   
 [Integration Services タスク](../../integration-services/control-flow/integration-services-tasks.md)   
 [[Master ストアド プロシージャ転送タスク エディター] ([全般] ページ)](../Topic/Transfer%20Master%20Stored%20Procedures%20Task%20Editor%20\(General%20Page\).md)   
 [[式] ページ](../Topic/Expressions%20Page.md)   
 [SMO 接続マネージャー](../../integration-services/connection-manager/smo-connection-manager.md)  
  
  
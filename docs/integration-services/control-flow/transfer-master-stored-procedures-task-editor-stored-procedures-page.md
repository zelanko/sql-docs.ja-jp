---
title: "Master ストアド プロシージャ転送タスク エディター ([ストアド プロシージャ] ページ) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.transferstoredprocedurestask.storedprocedures.f1
helpviewer_keywords:
- Transfer Stored Procedures Task Editor
ms.assetid: 5fcf171e-cc0b-4c24-8eb5-3a4b4775e64a
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 454835b1fe51015f9fd7668dcb4c639f3287edd6
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="transfer-master-stored-procedures-task-editor-stored-procedures-page"></a>[Master ストアド プロシージャ転送タスク エディター] ([ストアド プロシージャ] ページ)
  **[Master ストアド プロシージャ転送タスク エディター]** ダイアログ ボックスの **[ストアド プロシージャ]** ページを使用すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の 1 つのインスタンスの **master** データベースから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の別のインスタンスの **master** データベースに、1 つ以上のユーザー定義ストアド プロシージャをコピーする場合のプロパティを指定できます。 このタスクの詳細については、「 [Transfer Master Stored Procedures Task](../../integration-services/control-flow/transfer-master-stored-procedures-task.md)」を参照してください。  
  
> [!NOTE]  
>  このタスクは、コピー元のサーバーの **master** データベースからコピー先のサーバーの **master** データベースに、 **dbo** が所有しているユーザー定義のストアド プロシージャのみを転送します。 コピー先のサーバーでストアド プロシージャを作成するには、そのサーバーの **master** データベースの CREATE PROCEDURE 権限を取得するか、そのサーバーの **sysadmin** 固定サーバー ロールのメンバーである必要があります。  
  
## <a name="options"></a>オプション  
 **SourceConnection**  
 一覧で、SMO 接続マネージャーを選択するかクリックして**\<新しい接続 >**移行元サーバーに新しい接続を作成します。  
  
 **DestinationConnection**  
 一覧で、SMO 接続マネージャーを選択するかクリックして**\<新しい接続 >**移行先サーバーに新しい接続を作成します。  
  
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
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../integration-services/integration-services-error-and-message-reference.md)   
 [Integration Services タスク](../../integration-services/control-flow/integration-services-tasks.md)   
 [Master ストアド プロシージャ タスク エディター &#40; を転送します。[全般] ページ &#41;](../../integration-services/control-flow/transfer-master-stored-procedures-task-editor-general-page.md)   
 [「 式」 ページ](../../integration-services/expressions/expressions-page.md)   
 [SMO 接続マネージャー](../../integration-services/connection-manager/smo-connection-manager.md)  
  
  

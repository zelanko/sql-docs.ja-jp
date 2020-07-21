---
title: '[Master ストアドプロシージャ転送タスクエディター] ([ストアドプロシージャ] ページ)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferstoredprocedurestask.storedprocedures.f1
helpviewer_keywords:
- Transfer Stored Procedures Task Editor
ms.assetid: 5fcf171e-cc0b-4c24-8eb5-3a4b4775e64a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0cd0b269c0ced445017d573cfad08a767d5f2008
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85439989"
---
# <a name="transfer-master-stored-procedures-task-editor-stored-procedures-page"></a>[Master ストアド プロシージャ転送タスク エディター] ([ストアド プロシージャ] ページ)
  **[Master ストアド プロシージャ転送タスク エディター]** ダイアログ ボックスの **[ストアド プロシージャ]** ページを使用すると、 **の 1 つのインスタンスの** master [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] データベースから **の別のインスタンスの** master [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]データベースに、1 つ以上のユーザー定義ストアド プロシージャをコピーする場合のプロパティを指定できます。 このタスクの詳細については、「 [Transfer Master Stored Procedures Task](control-flow/transfer-master-stored-procedures-task.md)」を参照してください。  
  
> [!NOTE]  
>  このタスクは、コピー元のサーバーの **master** データベースからコピー先のサーバーの **master** データベースに、 **dbo** が所有しているユーザー定義のストアド プロシージャのみを転送します。 コピー先のサーバーでストアド プロシージャを作成するには、そのサーバーの **master** データベースの CREATE PROCEDURE 権限を取得するか、そのサーバーの **sysadmin** 固定サーバー ロールのメンバーである必要があります。  
  
## <a name="options"></a>オプション  
 **[Sourceconnection]**  
 SMO 接続マネージャーを一覧から選択するか、をクリックし **\<New connection...>** て、移行元サーバーへの新しい接続を作成します。  
  
 **DestinationConnection**  
 SMO 接続マネージャーを一覧から選択するか、をクリックし **\<New connection...>** て、移行先サーバーへの新しい接続を作成します。  
  
 **[IfObjectExists]**  
 コピー先のサーバーの **master** データベースに存在する名前と同じ名前を持つ、ユーザー定義ストアド プロシージャの処理方法を選択します。  
  
 このプロパティには、次の表に示すオプションがあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|**[FailTask]**|ストアド プロシージャがコピー先のサーバーの **master** データベースに既に存在する名前と同じ名前を持つ場合、タスクは失敗します。|  
|**Overwrite**|コピー先のサーバーの **master** データベースにある同じ名前のストアド プロシージャを上書きします。|  
|**Skip**|コピー先のサーバーの **master** データベースにある同じ名前のストアド プロシージャをスキップします。|  
  
 **[TransferAllStoredProcedures]**  
 コピー元のサーバーの **master** データベースのすべてのユーザー定義ストアド プロシージャをコピー先のサーバーにコピーするかどうかを選択します。  
  
|[値]|説明|  
|-----------|-----------------|  
|**True**|**master** データベースのユーザー定義ストアド プロシージャをすべてコピーします。|  
|**False**|指定したストアド プロシージャのみをコピーします。|  
  
 **[StoredProceduresList]**  
 コピー先の **master** データベースにコピーする、コピー元サーバーの **master** データベースのユーザー定義ストアド プロシージャを選択します。 このオプションは、 **[TransferAllStoredProcedures]** を **[False]** に設定した場合のみ使用できます。  
  
## <a name="see-also"></a>関連項目  
 [Integration Services のエラーとメッセージの参照](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Integration Services タスク](control-flow/integration-services-tasks.md)   
 [Master ストアドプロシージャ転送タスクエディター &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md)   
 [[式] ページ](expressions/expressions-page.md)   
 [SMO 接続マネージャー](connection-manager/smo-connection-manager.md)  
  
  

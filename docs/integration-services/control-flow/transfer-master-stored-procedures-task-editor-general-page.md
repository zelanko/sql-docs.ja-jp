---
title: "Master ストアド プロシージャ転送タスク エディター (全般 ページ) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.transferstoredprocedurestask.general.f1
helpviewer_keywords:
- Transfer Stored Procedures Task Editor
ms.assetid: fa1abd4c-e2be-427f-be53-860e49c97227
caps.latest.revision: 25
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 59bb5b42a9c832df8af539f2490eec9e7edb81c8
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="transfer-master-stored-procedures-task-editor-general-page"></a>[Master ストアド プロシージャ転送タスク エディター] ([全般] ページ)
  **[Master ストアド プロシージャ転送タスク エディター]** ダイアログ ボックスの **[全般]** ページを使用すると、Master ストアド プロシージャ転送タスクの名前と説明を入力できます。 このタスクの詳細については、「 [Transfer Master Stored Procedures Task](../../integration-services/control-flow/transfer-master-stored-procedures-task.md)」を参照してください。  
  
> [!NOTE]  
>  このタスクは、コピー元のサーバーの **master** データベースからコピー先のサーバーの **master** データベースに、 **dbo** が所有しているユーザー定義のストアド プロシージャのみを転送します。 コピー先のサーバーでストアド プロシージャを作成するには、そのサーバーの **master** データベースの CREATE PROCEDURE 権限を取得するか、そのサーバーの **sysadmin** 固定サーバー ロールのメンバーである必要があります。  
  
## <a name="options"></a>オプション  
 **名**  
 Master ストアド プロシージャ転送タスクの一意な名前を入力します。 この名前は、タスク アイコンのラベルとして使用されます。  
  
> [!NOTE]  
>  タスク名はパッケージ内で一意である必要があります。  
  
 **Description**  
 Master ストアド プロシージャ転送タスクの説明を入力します。  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../integration-services/integration-services-error-and-message-reference.md)   
 [Integration Services タスク](../../integration-services/control-flow/integration-services-tasks.md)   
 [[Master ストアド プロシージャ転送タスク エディター] &#40;[ストアド プロシージャ] ページ&#41;](../../integration-services/control-flow/transfer-master-stored-procedures-task-editor-stored-procedures-page.md)   
 [[式] ページ](../../integration-services/expressions/expressions-page.md)  
  
  

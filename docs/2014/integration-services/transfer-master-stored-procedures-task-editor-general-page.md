---
title: Master ストアド プロシージャ転送タスク エディター ([全般] ページ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferstoredprocedurestask.general.f1
helpviewer_keywords:
- Transfer Stored Procedures Task Editor
ms.assetid: fa1abd4c-e2be-427f-be53-860e49c97227
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: d2eff925b3aa3278c5b662e5848d979f017936ce
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62766185"
---
# <a name="transfer-master-stored-procedures-task-editor-general-page"></a>[Master ストアド プロシージャ転送タスク エディター] ([全般] ページ)
  **[Master ストアド プロシージャ転送タスク エディター]** ダイアログ ボックスの **[全般]** ページを使用すると、Master ストアド プロシージャ転送タスクの名前と説明を入力できます。 このタスクの詳細については、「 [Transfer Master Stored Procedures Task](control-flow/transfer-master-stored-procedures-task.md)」を参照してください。  
  
> [!NOTE]  
>  このタスクは、コピー元のサーバーの **master** データベースからコピー先のサーバーの **master** データベースに、 **dbo** が所有しているユーザー定義のストアド プロシージャのみを転送します。 コピー先のサーバーでストアド プロシージャを作成するには、そのサーバーの **master** データベースの CREATE PROCEDURE 権限を取得するか、そのサーバーの **sysadmin** 固定サーバー ロールのメンバーである必要があります。  
  
## <a name="options"></a>および  
 **名前**  
 Master ストアド プロシージャ転送タスクの一意な名前を入力します。 この名前は、タスク アイコンのラベルとして使用されます。  
  
> [!NOTE]  
>  タスク名はパッケージ内で一意である必要があります。  
  
 **[説明]**  
 Master ストアド プロシージャ転送タスクの説明を入力します。  
  
## <a name="see-also"></a>関連項目  
 [Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Integration Services タスク](control-flow/integration-services-tasks.md)   
 [[Master ストアド プロシージャ転送タスク エディター] &#40;[ストアド プロシージャ] ページ&#41;](../../2014/integration-services/transfer-master-stored-procedures-task-editor-stored-procedures-page.md)   
 [[式] ページ](expressions/expressions-page.md)  
  
  

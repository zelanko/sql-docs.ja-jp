---
title: Master ストアド プロシージャ転送タスク エディター ([全般] ページ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferstoredprocedurestask.general.f1
helpviewer_keywords:
- Transfer Stored Procedures Task Editor
ms.assetid: fa1abd4c-e2be-427f-be53-860e49c97227
caps.latest.revision: 24
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f89c6e35e69b8982b379b61e5341e80d6f768cd9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37205792"
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
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Integration Services タスク](control-flow/integration-services-tasks.md)   
 [[Master ストアド プロシージャ転送タスク エディター] &#40;[ストアド プロシージャ] ページ&#41;](../../2014/integration-services/transfer-master-stored-procedures-task-editor-stored-procedures-page.md)   
 [[式] ページ](expressions/expressions-page.md)  
  
  

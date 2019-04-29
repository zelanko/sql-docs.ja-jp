---
title: SQL 実行タスク エディター (結果セット ページ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executesqltask.resultset.f1
helpviewer_keywords:
- Execute SQL Task Editor
ms.assetid: d27000c8-8d91-4e1c-b45e-bca9a3c12f6d
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: da5cfd11c00876a4d7f3d8c784715e79bd1c73ba
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62898425"
---
# <a name="execute-sql-task-editor-result-set-page"></a>[SQL 実行タスク エディター] ([結果セット] ページ)
  **[SQL 実行タスク エディター]** ダイアログ ボックスの **[結果セット]** ページを使用すると、SQL ステートメントの結果を新しい変数または既存の変数にマップできます。 このダイアログ ボックスのオプションは、[全般] ページの **[ResultSet]** が **[なし]** に設定されている場合は無効です。  
  
 このタスクの詳細については、「 [SQL 実行タスク](control-flow/execute-sql-task.md) 」と「 [SQL 実行タスクにおける結果セット](../../2014/integration-services/result-sets-in-the-execute-sql-task.md)」を参照してください。  
  
## <a name="options"></a>および  
 **[結果名]**  
 **[追加]** をクリックして結果セットのマッピング設定を追加した後、結果に名前を付けます。 結果セットの種類によっては、特定の結果名を使用する必要があります。  
  
 結果セットの種類が " **単一行**" の場合、クエリによって返される列の名前か、クエリによって返される列の列リスト内で列の位置を示す数値を使用できます。  
  
 結果セットの種類が " **完全な結果セット** " または " **XML**" の場合、結果セット名には 0 を使用する必要があります。  
  
 **関連トピック:** [SQL 実行タスクにおける結果セット](../../2014/integration-services/result-sets-in-the-execute-sql-task.md)  
  
 **[変数名]**  
 変数を選択して変数に結果セットをマップするか、[\<**新しい変数...**>] をクリックして **[変数の追加]** ダイアログ ボックスで新しい変数を追加します。  
  
 **[追加]**  
 結果セットのマッピングを追加します。  
  
 **[削除]**  
 一覧で結果セットのマッピングを選択して、 **[削除]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [SQL 実行タスク エディター &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md)   
 [SQL 実行タスク エディター&#40;パラメーター マッピング ページ&#41;](../../2014/integration-services/execute-sql-task-editor-parameter-mapping-page.md)   
 [TRANSACT-SQL リファレンス &#40;データベース エンジン&#41;](/sql/t-sql/language-reference)  
  
  

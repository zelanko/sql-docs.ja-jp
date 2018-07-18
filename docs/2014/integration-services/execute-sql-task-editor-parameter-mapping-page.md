---
title: SQL 実行タスク エディター ([パラメーター マッピング] ページ) |Microsoft Docs
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
- sql12.dts.designer.executesqltask.parametermapping.f1
helpviewer_keywords:
- Execute SQL Task Editor
ms.assetid: 8ebe020a-7921-46b2-8823-398748f379b2
caps.latest.revision: 42
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4baffae0ada8cddc911561f63ca32f9b4b578283
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37152783"
---
# <a name="execute-sql-task-editor-parameter-mapping-page"></a>[SQL 実行タスク エディター] ([パラメーター マッピング] ページ)
  **[SQL 実行タスク エディター]** ダイアログ ボックスの **[パラメーター マッピング]** ページを使用すると、SQL ステートメント内のパラメーターに変数をマップできます。  
  
 この手順の詳細については、「 [SQL 実行タスク](control-flow/execute-sql-task.md) 」と「 [SQL 実行タスクのパラメーターとリターン コード](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md)」を参照してください。  
  
## <a name="options"></a>および  
 **[変数名]**  
 **[追加]** をクリックしてパラメーター マッピングを追加した後で、システム変数またはユーザー定義変数を一覧から選択するか、[\<**新しい変数...**>] をクリックして **[変数の追加]** ダイアログ ボックスで新しい変数を追加します。  
  
 **関連トピック:** [Integration Services &#40;SSIS&#41; の変数](integration-services-ssis-variables.md)  
  
 **[方向]**  
 パラメーターの方向を選択します。 各変数を入力パラメーター、出力パラメーター、またはリターン コードにマップします。  
  
 **[データ型]**  
 パラメーターのデータ型を選択します。 使用できるデータ型の一覧は、タスクによって使用される接続マネージャーで選択したプロバイダーに固有のものです。  
  
 **[パラメーター名]**  
 パラメーター名を指定します。  
  
 タスクで使用される接続マネージャーの種類によって、数字またはパラメーター名を使用する必要があります。 接続マネージャーの種類によっては、パラメーター名の先頭文字を @ 記号にすること、@Param1 などの特定の名前を使用すること、またはパラメーター名として列名を使用することが求められます。  
  
 **関連トピック:** [SQL 実行タスクのパラメーターとリターン コード](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md)  
  
 **[パラメーター サイズ]**  
 文字列やバイナリ フィールドなどの可変長パラメーターのサイズを指定します。  
  
 この設定により、プロバイダーは可変長パラメーター値に十分な領域を割り当てることができるようになります。  
  
 **[追加]**  
 クリックすると、パラメーター マッピングが追加されます。  
  
 **[削除]**  
 一覧からパラメーター マッピングを選択してから **[削除]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [SQL 実行タスク エディター &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md)   
 [SQL 実行タスク エディター&#40;結果セット ページ&#41;](../../2014/integration-services/execute-sql-task-editor-result-set-page.md)   
 [TRANSACT-SQL リファレンス &#40;データベース エンジン&#41;](/sql/t-sql/language-reference)  
  
  

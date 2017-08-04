---
title: "一括挿入タスク エディター (オプション ページ) |Microsoft ドキュメント"
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
- sql13.dts.designer.bulkinserttask.options.f1
helpviewer_keywords:
- Bulk Insert Task Editor
ms.assetid: b3702811-3eb8-4b28-9190-5ae7a1a7bb6f
caps.latest.revision: 31
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 1a714027caa6581a56d9f22da84c48d469e80cb1
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="bulk-insert-task-editor-options-page"></a>[一括挿入タスク エディター] ([オプション] ページ)
  **[一括挿入タスク エディター]** ダイアログ ボックスの **[オプション]** ページを使用すると、一括挿入操作のプロパティを設定できます。 一括挿入タスクにより、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のテーブルまたはビューに大量のデータがコピーされます。  
  
 一括挿入タスクについては、「[一括挿入タスク](../../integration-services/control-flow/bulk-insert-task.md)」および「[「BULK INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/bulk-insert-transact-sql.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **CodePage**  
 データ ファイル内のデータのコード ページを指定します。  
  
 **[DataFileType]**  
 読み込み操作で使用するデータ型の値を指定します。  
  
 **BatchSize**  
 バッチ内の行数を指定します。 既定では、データ ファイル全体です。 **[BatchSize]** を 0 に設定すると、データは単一のバッチに読み込まれます。  
  
 **[LastRow]**  
 コピーする最後の行を指定します。  
  
 **[FirstRow]**  
 コピーを開始する最初の行を指定します。  
  
 **[一括挿入タスク エディター]**  
 |項目|定義|  
|----------|----------------|  
|**CHECK 制約**|テーブルおよび列に対する制約をチェックします。|  
|**[NULL を保持する]**|空の列に任意の既定値を挿入する代わりに、一括挿入操作中に NULL 値を保持します。|  
|**[ID 挿入を許可する]**|ID 列に既存の値を挿入します。|  
|**[テーブル ロック]**|一括挿入中にテーブルをロックします。|  
|**[トリガーを起動する]**|テーブル上のすべての挿入トリガー、更新トリガー、および削除トリガーを起動します。|  
  
 **SortedData**  
 一括挿入ステートメントに ORDER BY 句を指定します。 指定する列名は、挿入先テーブル内の有効な列でなければなりません。 既定値は **false**です。 これは、データが ORDER BY 句によって並べ替えられないことを意味します。  
  
 **[MaxErrors]**  
 一括挿入操作が取り消されるまでに発生が許可される最大エラー数を指定します。 0 の値は、許可されるエラー数が無制限であることを示します。  
  
> [!NOTE]  
>  一括読み込み操作でインポートできない行は、1 つのエラーとしてカウントされます。  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../integration-services/integration-services-error-and-message-reference.md)   
 [一括挿入タスク エディターと &#40; です。「 全般」 ページと &#41; です。](../../integration-services/control-flow/bulk-insert-task-editor-general-page.md)   
 [一括挿入タスク エディター & #40 です。[接続] ページ &#41;](../../integration-services/control-flow/bulk-insert-task-editor-connection-page.md)   
 [「式」 ページ](../../integration-services/expressions/expressions-page.md)   
 [制御フロー](../../integration-services/control-flow/control-flow.md)  
  
  

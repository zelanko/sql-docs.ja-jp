---
title: "一括挿入タスク エディター (接続 ページ) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.bulkinserttask.connection.f1
helpviewer_keywords:
- Bulk Insert Task Editor
ms.assetid: 51252c20-8865-4ede-a3fd-bd73a968f47d
caps.latest.revision: 30
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c837ff29b8f5158620629811352c398a39d30c2c
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="bulk-insert-task-editor-connection-page"></a>[一括挿入タスク エディター] ([接続] ページ)
  **[一括挿入タスク エディター]** ダイアログ ボックスの **[接続]** ページを使用すると、一括挿入操作の挿入元と挿入先、および使用するフォーマットを指定できます。  
  
 一括挿入操作の詳細については、「[Bulk Insert Task](../../integration-services/control-flow/bulk-insert-task.md)」(一括挿入タスク) と「[データのインポートまたはエクスポート用のフォーマット ファイル (SQL Server)](../../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **接続**  
 一覧で、OLE DB 接続マネージャーを選択するかクリックして\<**新しい接続をしています.**> 新しい接続を作成します。  
  
 **関連トピック:** [OLE DB 接続マネージャー](../../integration-services/connection-manager/ole-db-connection-manager.md)、[OLE DB 接続マネージャーの構成](../../integration-services/connection-manager/configure-ole-db-connection-manager.md)  
  
 **[DestinationTable]**  
 挿入先のテーブルまたはビューの名前を入力するか、テーブルまたはビューを一覧から選択します。  
  
 **Format**  
 一括挿入のフォーマットの挿入元を選択します。 このプロパティのオプションを次の表に示します。  
  
|値|Description|  
|-----------|-----------------|  
|**[ファイルを使用]**|フォーマット指定が格納されているファイルを選択します。 このオプションを選択すると、動的オプションの **[FormatFile]**が表示されます。|  
|**[指定]**|フォーマットを指定します。 このオプションを選択すると、動的オプションの **[RowDelimiter]** および **[ColumnDelimiter]**が表示されます。|  
  
 **ファイル**  
 一覧で、ファイルまたはフラット ファイル接続マネージャーを選択するかクリックして\<**新しい接続をしています.**> 新しい接続を作成します。  
  
 このファイルの場所は、このタスクの接続マネージャーに指定されている SQL Server データベース エンジンを基準とする相対パスです。 SQL Server データベース エンジンは、サーバーのローカル ハード ドライブ、共有、または SQL Server にマップされたドライブでこのテキスト ファイルにアクセスできる必要があります。 SSIS ランタイムはこのファイルにアクセスしません。  
  
 フラット ファイル接続マネージャーを使用してソース ファイルにアクセスした場合、フラット ファイル接続マネージャーに指定されたフォーマットは一括挿入タスクで使用されません。 その代わり、フォーマット ファイルに指定されたフォーマットか、またはタスクの RowDelimiter プロパティおよび ColumnDelimiter プロパティの値が一括挿入タスクで使用されます。  
  
 **関連トピック:** 「[ファイル接続マネージャー](../../integration-services/connection-manager/file-connection-manager.md)」、「[ファイル接続マネージャー エディター](../../integration-services/connection-manager/file-connection-manager-editor.md)」、「[フラット ファイル接続マネージャー](../../integration-services/connection-manager/flat-file-connection-manager.md)」、「[フラット ファイル接続マネージャー エディター ([全般] ページ)](../../integration-services/connection-manager/flat-file-connection-manager-editor-general-page.md)」、「[フラット ファイル接続マネージャー エディター ([列] ページ)](../../integration-services/connection-manager/flat-file-connection-manager-editor-columns-page.md)」、「[フラット ファイル接続マネージャー エディター ([詳細設定] ページ)](../../integration-services/connection-manager/flat-file-connection-manager-editor-advanced-page.md)」  
  
 **[テーブルの更新]**  
 データベースおよびビューの一覧を更新します。  
  
## <a name="format-dynamic-options"></a>[Format] の動的オプション  
  
### <a name="format--use-file"></a>[Format] = [ファイルを使用]  
 **[FormatFile]**  
 フォーマット ファイルのパスを入力します。または、参照ボタン ( **[...]** ) をクリックし、フォーマット ファイルを指定します。  
  
### <a name="format--specify"></a>[Format] = [指定]  
 **[RowDelimiter]**  
 ソース ファイルの行区切り記号を指定します。 既定値は **{CR}{LF}**です。  
  
 **[ColumnDelimiter]**  
 ソース ファイルの列区切り記号を指定します。 既定値は **[タブ]**です。  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../integration-services/integration-services-error-and-message-reference.md)   
 [一括挿入タスク エディターと &#40; です。「 全般」 ページと &#41; です。](../../integration-services/control-flow/bulk-insert-task-editor-general-page.md)   
 [一括挿入タスク エディター &#40;のオプション ページ&#41; です。](../../integration-services/control-flow/bulk-insert-task-editor-options-page.md)   
 [「 式」 ページ](../../integration-services/expressions/expressions-page.md)   
 [一括挿入 &#40; です。Transact SQL と &#41; です。](../../t-sql/statements/bulk-insert-transact-sql.md)   
 [制御フロー](../../integration-services/control-flow/control-flow.md)  
  
  

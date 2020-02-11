---
title: '[一括挿入タスクエディター] ([接続] ページ)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.bulkinserttask.connection.f1
helpviewer_keywords:
- Bulk Insert Task Editor
ms.assetid: 51252c20-8865-4ede-a3fd-bd73a968f47d
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: b6834a2a4cd75e70de253419cc42ec5904ce0793
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66061220"
---
# <a name="bulk-insert-task-editor-connection-page"></a>[一括挿入タスク エディター] ([接続] ページ)
  
  **[一括挿入タスク エディター]** ダイアログ ボックスの **[接続]** ページを使用すると、一括挿入操作の挿入元と挿入先、および使用するフォーマットを指定できます。  
  
 一括挿入操作の詳細については、「[Bulk Insert Task](control-flow/bulk-insert-task.md)」(一括挿入タスク) と「[データのインポートまたはエクスポート用のフォーマット ファイル (SQL Server)](../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **接続**  
 OLE DB 接続マネージャーを一覧から選択するか、[\<**新しい接続...**>] をクリックして新しい接続を作成します。  
  
 **関連トピック:** [OLE DB 接続マネージャー](connection-manager/ole-db-connection-manager.md)、 [OLE DB 接続マネージャーの構成](../../2014/integration-services/configure-ole-db-connection-manager.md)  
  
 **DestinationTable**  
 挿入先のテーブルまたはビューの名前を入力するか、テーブルまたはビューを一覧から選択します。  
  
 **形式**  
 一括挿入のフォーマットの挿入元を選択します。 このプロパティのオプションを次の表に示します。  
  
|値|[説明]|  
|-----------|-----------------|  
|**ファイルの使用**|フォーマット指定が格納されているファイルを選択します。 このオプションを選択すると、動的オプションの **[FormatFile]** が表示されます。|  
|**指定**|フォーマットを指定します。 このオプションを`RowDelimiter`選択すると、動的オプション`ColumnDelimiter`とが表示されます。|  
  
 **拡張子**  
 ファイル接続マネージャーまたはフラット ファイル接続マネージャーを一覧から選択するか、[\<**新しい接続...**>] をクリックして新しい接続を作成します。  
  
 このファイルの場所は、このタスクの接続マネージャーに指定されている SQL Server データベース エンジンを基準とする相対パスです。 SQL Server データベース エンジンは、サーバーのローカル ハード ドライブ、共有、または SQL Server にマップされたドライブでこのテキスト ファイルにアクセスできる必要があります。 SSIS ランタイムはこのファイルにアクセスしません。  
  
 フラット ファイル接続マネージャーを使用してソース ファイルにアクセスした場合、フラット ファイル接続マネージャーに指定されたフォーマットは一括挿入タスクで使用されません。 その代わり、フォーマット ファイルに指定されたフォーマットか、またはタスクの RowDelimiter プロパティおよび ColumnDelimiter プロパティの値が一括挿入タスクで使用されます。  
  
 **関連トピック:** [ファイル接続マネージャー](connection-manager/file-connection-manager.md)、[ファイル接続マネージャーエディター](../../2014/integration-services/file-connection-manager-editor.md)、[フラットファイル接続マネージャー](connection-manager/flat-file-connection-manager.md)、フラットファイル接続マネージャーエディター [&#40;全般ページ&#41;](general-page-of-integration-services-designers-options.md)、フラットファイル接続マネージャー[エディター &#40;列ページ&#41;](../../2014/integration-services/flat-file-connection-manager-editor-columns-page.md)、[フラットファイル接続マネージャーエディター &#40;詳細設定ページ&#41;](../../2014/integration-services/flat-file-connection-manager-editor-advanced-page.md)  
  
 **テーブルの更新**  
 データベースおよびビューの一覧を更新します。  
  
## <a name="format-dynamic-options"></a>[Format] の動的オプション  
  
### <a name="format--use-file"></a>[Format] = [ファイルを使用]  
 **FormatFile**  
 フォーマット ファイルのパスを入力します。または、参照ボタン **[...]** をクリックし、フォーマット ファイルを指定します。  
  
### <a name="format--specify"></a>[Format] = [指定]  
 `RowDelimiter`  
 ソース ファイルの行区切り記号を指定します。 既定値は **{CR} {LF}** です。  
  
 `ColumnDelimiter`  
 ソース ファイルの列区切り記号を指定します。 既定値は **[タブ]** です。  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーとメッセージの参照](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [一括挿入タスクエディター &#40;[全般] ページ&#41;](../../2014/integration-services/bulk-insert-task-editor-general-page.md)   
 [一括挿入タスクエディター &#40;オプションページ&#41;](../../2014/integration-services/bulk-insert-task-editor-options-page.md)   
 [[式] ページ](expressions/expressions-page.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [制御フロー](control-flow/control-flow.md)  
  
  

---
title: "[一括挿入タスク エディター] ([接続] ページ) | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.bulkinserttask.connection.f1"
helpviewer_keywords: 
  - "一括挿入タスク エディター"
ms.assetid: 51252c20-8865-4ede-a3fd-bd73a968f47d
caps.latest.revision: 30
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 30
---
# [一括挿入タスク エディター] ([接続] ページ)
  **[一括挿入タスク エディター]** ダイアログ ボックスの **[接続]** ページを使用すると、一括挿入操作の挿入元と挿入先、および使用するフォーマットを指定できます。  
  
 一括挿入操作の詳細については、「[Bulk Insert Task](../../integration-services/control-flow/bulk-insert-task.md)」(一括挿入タスク) と「[データのインポートまたはエクスポート用のフォーマット ファイル (SQL Server)](../../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md)」を参照してください。  
  
## オプション  
 **接続**  
 OLE DB 接続マネージャーを一覧から選択するか、**[\<新しい接続>]** をクリックして新しい接続を作成します。  
  
 **関連トピック:**「[OLE DB 接続マネージャー](../../integration-services/connection-manager/ole-db-connection-manager.md)」、「[OLE DB 接続マネージャーの構成](../../integration-services/connection-manager/configure-ole-db-connection-manager.md)」  
  
 **[DestinationTable]**  
 挿入先のテーブルまたはビューの名前を入力するか、テーブルまたはビューを一覧から選択します。  
  
 **Format**  
 一括挿入のフォーマットの挿入元を選択します。 このプロパティのオプションを次の表に示します。  
  
|値|Description|  
|-----------|-----------------|  
|**[ファイルを使用]**|フォーマット指定が格納されているファイルを選択します。 このオプションを選択すると、動的オプションの **[FormatFile]** が表示されます。|  
|**[指定]**|フォーマットを指定します。 このオプションを選択すると、動的オプションの **[RowDelimiter]** および **[ColumnDelimiter]** が表示されます。|  
  
 **ファイル**  
 ファイル接続マネージャーまたはフラット ファイル接続マネージャーを一覧から選択するか、**[\<新しい接続>]** をクリックして新しい接続を作成します。  
  
 このファイルの場所は、このタスクの接続マネージャーに指定されている SQL Server データベース エンジンを基準とする相対パスです。 SQL Server データベース エンジンは、サーバーのローカル ハード ドライブ、共有、または SQL Server にマップされたドライブでこのテキスト ファイルにアクセスできる必要があります。 SSIS ランタイムはこのファイルにアクセスしません。  
  
 フラット ファイル接続マネージャーを使用してソース ファイルにアクセスした場合、フラット ファイル接続マネージャーに指定されたフォーマットは一括挿入タスクで使用されません。 その代わり、フォーマット ファイルに指定されたフォーマットか、またはタスクの RowDelimiter プロパティおよび ColumnDelimiter プロパティの値が一括挿入タスクで使用されます。  
  
 **関連トピック:** 「[ファイル接続マネージャー](../../integration-services/connection-manager/file-connection-manager.md)」、「[ファイル接続マネージャー エディター](../../integration-services/connection-manager/file-connection-manager-editor.md)」、「[フラット ファイル接続マネージャー](../../integration-services/connection-manager/flat-file-connection-manager.md)」、「[フラット ファイル接続マネージャー エディター ([全般] ページ)](../Topic/Flat%20File%20Connection%20Manager%20Editor%20\(General%20Page\).md)」、「[フラット ファイル接続マネージャー エディター ([列] ページ)](../Topic/Flat%20File%20Connection%20Manager%20Editor%20\(Columns%20Page\).md)」、「[フラット ファイル接続マネージャー エディター ([詳細設定] ページ)](../Topic/Flat%20File%20Connection%20Manager%20Editor%20\(Advanced%20Page\).md)」  
  
 **[テーブルの更新]**  
 データベースおよびビューの一覧を更新します。  
  
## [Format] の動的オプション  
  
### [Format] = [ファイルを使用]  
 **FormatFile**  
 フォーマット ファイルのパスを入力します。または、参照ボタン (**[...]**) をクリックし、フォーマット ファイルを指定します。  
  
### [Format] = [指定]  
 **[RowDelimiter]**  
 ソース ファイルの行区切り記号を指定します。 既定値は **{CR}{LF}** です。  
  
 **[列区切り記号]**  
 ソース ファイルの列区切り記号を指定します。 既定値は **[タブ]** です。  
  
## 参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../integration-services/integration-services-error-and-message-reference.md)   
 [[一括挿入タスク エディター] ([全般] ページ)](../Topic/Bulk%20Insert%20Task%20Editor%20\(General%20Page\).md)   
 [[一括挿入タスク エディター] ([オプション] ページ)](../Topic/Bulk%20Insert%20Task%20Editor%20\(Options%20Page\).md)   
 [[式] ページ](../Topic/Expressions%20Page.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/bulk-insert-transact-sql.md)   
 [制御フロー](../../integration-services/control-flow/control-flow.md)  
  
  
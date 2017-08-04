---
title: "WMI データ リーダー タスク エディター ([WMI オプション] ページ) |Microsoft ドキュメント"
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
- sql13.dts.designer.wmidatareadertask.wmiquery.f1
helpviewer_keywords:
- WMI Data Reader Task Editor
ms.assetid: 4b8d4716-882d-41b0-b77e-e0e2741a2cd5
caps.latest.revision: 40
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 2d87bb0cfa2ca6a0ad103ac803e6fac662a9d385
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="wmi-data-reader-task-editor-wmi-options-page"></a>[WMI データ リーダー タスク エディター] ([WMI オプション] ページ)
  **[WMI データ リーダー タスク エディター]** ダイアログ ボックスの **[WMI オプション]** ページを使用すると、WQL (Windows Management Instrumentation Query Language) クエリのソースおよびクエリ結果の出力先を指定できます。  
  
 このタスクの詳細については、「 [WMI Data Reader Task](../../integration-services/control-flow/wmi-data-reader-task.md)」を参照してください。 WQL (WMI Query Language) の詳細については、MSDN ライブラリにある Windows Management Instrumentation のトピック「 [WQL を使用したクエリ](http://go.microsoft.com/fwlink/?LinkId=79045)」を参照してください。  
  
## <a name="static-options"></a>静的オプション  
 **[WMIConnectionName]**  
 一覧で、WMI 接続マネージャーを選択するかクリックして\<**新しい WMI 接続しています.**> 新しい接続マネージャーを作成します。  
  
 **関連トピック:** [WMI 接続マネージャー](../../integration-services/connection-manager/wmi-connection-manager.md)、[WMI 接続マネージャー エディター](../../integration-services/connection-manager/wmi-connection-manager-editor.md)  
  
 **[WQLQuerySourceType]**  
 タスクで実行する WQL クエリのソースの種類を選択します。 このプロパティのオプションを次の表に示します。  
  
|値|Description|  
|-----------|-----------------|  
|**[直接入力]**|ソースを WQL クエリに設定します。 この値を選択すると、動的オプションの **[WQLQuerySourceType]**が表示されます。|  
|**[ファイル接続]**|WQL クエリを含むファイルを選択します。 この値を選択すると、動的オプションの **[WQLQuerySourceType]**が表示されます。|  
|**変数**|WQL クエリを定義する変数に、ソースを設定します。 この値を選択すると、動的オプションの **[WQLQuerySourceType]**が表示されます。|  
  
 **[OutputType]**  
 データ テーブル、プロパティ値、またはプロパティ名と値のいずれを出力に含めるかを指定します。  
  
 **[OverwriteDestination]**  
 出力先のファイルまたは変数内の元のデータを変更しないか、上書きするか、データを追加するかを指定します。  
  
 **[DestinationType]**  
 タスクで実行する WQL クエリの出力先の種類を選択します。 このプロパティのオプションを次の表に示します。  
  
|値|Description|  
|-----------|-----------------|  
|**[ファイル接続]**|WQL クエリの結果を保存するファイルを選択します。 この値を選択すると、動的オプションの **[DestinationType]**が表示されます。|  
|**変数**|WQL クエリの結果を保存する変数を設定します。 この値を選択すると、動的オプションの **[DestinationType]**が表示されます。|  
  
## <a name="wqlquerysourcetype-dynamic-options"></a>[WQLQuerySourceType] 動的オプション  
  
### <a name="wqlquerysourcetype--direct-input"></a>[WQLQuerySourceType] = [直接入力]  
 **[WQLQuerySource]**  
 クエリを指定します。または、参照 ([...]) をクリックし、 **[WQL クエリ]** ダイアログ ボックスを使用してクエリを入力します。  
  
### <a name="wqlquerysourcetype--file-connection"></a>[WQLQuerySourceType] = [ファイル接続]  
 **[WQLQuerySource]**  
 一覧で、ファイル接続マネージャーを選択するかクリックして\<**新しい接続をしています.**> 新しい接続マネージャーを作成します。  
  
 **関連トピック:** [ファイル接続マネージャー](../../integration-services/connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
### <a name="wqlquerysourcetype--variable"></a>[WQLQuerySourceType] = [変数]  
 **[WQLQuerySource]**  
 一覧で、変数を選択するかクリックして\<**新しい変数しています.**> 新しい変数を作成します。  
  
 **関連トピック:** [Integration Services (SSIS) 変数](../../integration-services/integration-services-ssis-variables.md)、[変数の追加](http://msdn.microsoft.com/library/d09b5d31-433f-4f7c-8c68-9df3a97785d5)  
  
## <a name="destinationtype-dynamic-options"></a>[DestinationType] 動的オプション  
  
### <a name="destinationtype--file-connection"></a>[DestinationType] = [ファイル接続]  
 **変換先**  
 一覧で、ファイル接続マネージャーを選択するかクリックして\<**新しい接続をしています.**> 新しい接続マネージャーを作成します。  
  
 **関連トピック:** [ファイル接続マネージャー](../../integration-services/connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
### <a name="destinationtype--variable"></a>[DestinationType] = [変数]  
 **変換先**  
 一覧で、変数を選択するかクリックして\<**新しい変数しています.**> 新しい変数を作成します。  
  
 **関連トピック:** [Integration Services (SSIS) 変数](../../integration-services/integration-services-ssis-variables.md)、[変数の追加](http://msdn.microsoft.com/library/d09b5d31-433f-4f7c-8c68-9df3a97785d5)  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../integration-services/integration-services-error-and-message-reference.md)   
 [WMI データ リーダー タスク エディター & #40 です。[全般] ページ &#41;](../../integration-services/control-flow/wmi-data-reader-task-editor-general-page.md)   
 [「式」 ページ](../../integration-services/expressions/expressions-page.md)   
 [WMI イベント監視タスク](../../integration-services/control-flow/wmi-event-watcher-task.md)  
  
  

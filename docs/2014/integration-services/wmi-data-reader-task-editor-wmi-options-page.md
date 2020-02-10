---
title: '[WMI データリーダータスクエディター] ([WMI オプション] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.wmidatareadertask.wmiquery.f1
helpviewer_keywords:
- WMI Data Reader Task Editor
ms.assetid: 4b8d4716-882d-41b0-b77e-e0e2741a2cd5
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 8367f0ae57df5333808e4dfde25c5676a3bcf1d4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66054358"
---
# <a name="wmi-data-reader-task-editor-wmi-options-page"></a>[WMI データ リーダー タスク エディター] ([WMI オプション] ページ)
  
  **[WMI データ リーダー タスク エディター]** ダイアログ ボックスの **[WMI オプション]** ページを使用すると、WQL (Windows Management Instrumentation Query Language) クエリのソースおよびクエリ結果の出力先を指定できます。  
  
 このタスクの詳細については、「 [WMI Data Reader Task](control-flow/wmi-data-reader-task.md)」を参照してください。 WQL (WMI Query Language) の詳細については、MSDN ライブラリにある Windows Management Instrumentation のトピック「 [WQL を使用したクエリ](https://go.microsoft.com/fwlink/?LinkId=79045)」を参照してください。  
  
## <a name="static-options"></a>静的オプション  
 **WMIConnectionName**  
 Wmi 接続マネージャーを一覧から選択するか、[ \<**新しい wmi 接続...**>] をクリックして新しい接続マネージャーを作成します。  
  
 **関連トピック:** [wmi 接続マネージャー](connection-manager/wmi-connection-manager.md)、 [wmi 接続マネージャーエディター](../../2014/integration-services/wmi-connection-manager-editor.md)  
  
 **[Wqlquerysourcetype]**  
 タスクで実行する WQL クエリのソースの種類を選択します。 このプロパティのオプションを次の表に示します。  
  
|値|[説明]|  
|-----------|-----------------|  
|**直接入力**|ソースを WQL クエリに設定します。 この値を選択すると、動的オプションの **[WQLQuerySourceType]** が表示されます。|  
|**ファイル接続**|WQL クエリを含むファイルを選択します。 この値を選択すると、動的オプションの **[WQLQuerySourceType]** が表示されます。|  
|**変数**|WQL クエリを定義する変数に、ソースを設定します。 この値を選択すると、動的オプションの **[WQLQuerySourceType]** が表示されます。|  
  
 **OutputType**  
 データ テーブル、プロパティ値、またはプロパティ名と値のいずれを出力に含めるかを指定します。  
  
 **OverwriteDestination**  
 出力先のファイルまたは変数内の元のデータを変更しないか、上書きするか、データを追加するかを指定します。  
  
 **Destinationtype]**  
 タスクで実行する WQL クエリの出力先の種類を選択します。 このプロパティのオプションを次の表に示します。  
  
|値|[説明]|  
|-----------|-----------------|  
|**ファイル接続**|WQL クエリの結果を保存するファイルを選択します。 この値を選択すると、動的オプションの **[DestinationType]** が表示されます。|  
|**変数**|WQL クエリの結果を保存する変数を設定します。 この値を選択すると、動的オプションの **[DestinationType]** が表示されます。|  
  
## <a name="wqlquerysourcetype-dynamic-options"></a>[WQLQuerySourceType] 動的オプション  
  
### <a name="wqlquerysourcetype--direct-input"></a>[WQLQuerySourceType] = [直接入力]  
 **[Wqlquerysource]**  
 クエリを指定します。または、参照 ( [...] ) をクリックし、**[WQL クエリ]** ダイアログ ボックスを使用してクエリを入力します。  
  
### <a name="wqlquerysourcetype--file-connection"></a>[WQLQuerySourceType] = [ファイル接続]  
 **[Wqlquerysource]**  
 ファイル接続マネージャーを一覧から選択するか、\<**[新しい接続...]** をクリックして新しい接続マネージャーを作成します。  
  
 **関連トピック:** [ファイル接続マネージャー](connection-manager/file-connection-manager.md)、[ファイル接続マネージャーエディター](../../2014/integration-services/file-connection-manager-editor.md)  
  
### <a name="wqlquerysourcetype--variable"></a>[WQLQuerySourceType] = [変数]  
 **[Wqlquerysource]**  
 変数を一覧から選択するか、[ \<**新しい変数...** ] をクリックして新しい変数を作成> ます。  
  
 **関連トピック:** [SSIS&#41; 変数の Integration Services &#40;](integration-services-ssis-variables.md)[変数の追加](../../2014/integration-services/add-variable.md)  
  
## <a name="destinationtype-dynamic-options"></a>[DestinationType] 動的オプション  
  
### <a name="destinationtype--file-connection"></a>[DestinationType] = [ファイル接続]  
 **宛先**  
 ファイル接続マネージャーを一覧から選択するか、\<**[新しい接続...]** をクリックして新しい接続マネージャーを作成します。  
  
 **関連トピック:** [ファイル接続マネージャー](connection-manager/file-connection-manager.md)、[ファイル接続マネージャーエディター](../../2014/integration-services/file-connection-manager-editor.md)  
  
### <a name="destinationtype--variable"></a>[DestinationType] = [変数]  
 **宛先**  
 変数を一覧から選択するか、[ \<**新しい変数...** ] をクリックして新しい変数を作成> ます。  
  
 **関連トピック:** [SSIS&#41; 変数の Integration Services &#40;](integration-services-ssis-variables.md)[変数の追加](../../2014/integration-services/add-variable.md)  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーとメッセージの参照](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [[WMI データリーダータスクエディター] &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md)   
 [[式] ページ](expressions/expressions-page.md)   
 [WMI イベント監視タスク](control-flow/wmi-event-watcher-task.md)  
  
  

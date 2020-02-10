---
title: '[WMI イベント監視タスクエディター] ([WMI オプション] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.wmieventwatcher.wmiquery.f1
helpviewer_keywords:
- WMI Event Watcher Task Editor
ms.assetid: 525f3de7-a021-4e52-9939-3a83c88f131a
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 52ca90b38975c8db762ec0937b265a91b03c5cb2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66054379"
---
# <a name="wmi-event-watcher-task-editor-wmi-options-page"></a>[WMI イベント監視タスク エディター] ([WMI オプション] ページ)
  
  **[WMI イベント監視タスク エディター]** ダイアログ ボックスの **[WMI オプション]** ページを使用すると、WQL (Windows Management Instrumentation Query Language) クエリのソースや、WMI イベント監視タスクがどのように WMI (Microsoft Windows Instrumentation) イベントに応答するかを指定できます。  
  
 このタスクの詳細については、「 [WMI Event Watcher Task](control-flow/wmi-event-watcher-task.md)」を参照してください。 WQL (WMI Query Language) の詳細については、MSDN ライブラリにある Windows Management Instrumentation のトピック「 [WQL を使用したクエリ](https://go.microsoft.com/fwlink/?LinkId=79045)」を参照してください。  
  
## <a name="static-options"></a>静的オプション  
 **WMIConnectionName**  
 Wmi 接続マネージャーを一覧から選択するか、[ \<**新しい wmi 接続...**>] をクリックして新しい接続マネージャーを作成します。  
  
 **関連トピック:** [wmi 接続マネージャー](connection-manager/wmi-connection-manager.md)、 [wmi 接続マネージャーエディター](../../2014/integration-services/wmi-connection-manager-editor.md)  
  
 **[Wqlquerysourcetype]**  
 タスクで実行する WQL クエリのソースの種類を選択します。 このプロパティのオプションを次の表に示します。  
  
|値|[説明]|  
|-----------|-----------------|  
|**直接入力**|ソースを WQL クエリに設定します。 この値を選択すると、動的オプションの **[WQLQuerySource]** が表示されます。|  
|**ファイル接続**|WQL クエリを含むファイルを選択します。 この値を選択すると、動的オプションの **[WQLQuerySource]** が表示されます。|  
|**変数**|ソースを、WQL クエリを定義する変数に設定します。 この値を選択すると、動的オプションの **[WQLQuerySource]** が表示されます。|  
  
 **ActionAtEvent**  
 WMI イベントをログに記録すると共に [!INCLUDE[ssIS](../includes/ssis-md.md)] アクションを実行するか、単にイベントをログに記録するだけにするかを指定します。  
  
 **AfterEvent**  
 WMI イベントを受け取った後にタスクを成功または失敗させるか、イベントの発生をタスクで引き続き監視するかを指定します。  
  
 **ActionAtTimeout**  
 WMI クエリのタイムアウトをログに記録すると共に [!INCLUDE[ssIS](../includes/ssis-md.md)] イベントを発生させるか、単にタイムアウトをログに記録するだけにするかを指定します。  
  
 **AfterTimeout**  
 タイムアウトに対してタスクを成功または失敗させるか、別のタイムアウトの発生をタスクで引き続き監視するかを指定します。  
  
 **NumberOfEvents**  
 監視するイベントの数を指定します。  
  
 **タイムアウト**  
 イベントが発生するのを待機する秒数を指定します。 値 0 は、タイムアウトを設定しないことを意味します。  
  
## <a name="wqlquerysource-dynamic-options"></a>[WQLQuerySource] の動的オプション  
  
### <a name="wqlquerysource--direct-input"></a>[WQLQuerySource] = [直接入力]  
 **[Wqlquerysource]**  
 クエリを指定します。または、参照ボタン ( [...] ) をクリックし、**[WQL クエリ]** ダイアログ ボックスを使用してクエリを入力します。  
  
### <a name="wqlquerysource--file-connection"></a>[WQLQuerySource] = [ファイル接続]  
 **[Wqlquerysource]**  
 ファイル接続マネージャーを一覧から選択するか、\<**[新しい接続...]** をクリックして新しい接続マネージャーを作成します。  
  
 **関連トピック:** [ファイル接続マネージャー](connection-manager/file-connection-manager.md)、[ファイル接続マネージャーエディター](../../2014/integration-services/file-connection-manager-editor.md)  
  
### <a name="wqlquerysource--variable"></a>[WQLQuerySource] = [変数]  
 **[Wqlquerysource]**  
 変数を一覧から選択するか、[ \<**新しい変数...** ] をクリックして新しい変数を作成> ます。  
  
 **関連トピック:** [SSIS&#41; 変数の Integration Services &#40;](integration-services-ssis-variables.md)[変数の追加](../../2014/integration-services/add-variable.md)  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーとメッセージの参照](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [[WMI イベント監視タスクエディター] &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md)   
 [[式] ページ](expressions/expressions-page.md)   
 [WMI データ リーダー タスク](control-flow/wmi-data-reader-task.md)  
  
  

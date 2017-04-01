---
title: "[WMI データ リーダー タスク エディター] ([WMI オプション] ページ) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.wmidatareadertask.wmiquery.f1"
helpviewer_keywords: 
  - "WMI データ リーダー タスク エディター"
ms.assetid: 4b8d4716-882d-41b0-b77e-e0e2741a2cd5
caps.latest.revision: 40
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 40
---
# [WMI データ リーダー タスク エディター] ([WMI オプション] ページ)
  **[WMI データ リーダー タスク エディター]** ダイアログ ボックスの **[WMI オプション]** ページを使用すると、WQL (Windows Management Instrumentation Query Language) クエリのソースおよびクエリ結果の出力先を指定できます。  
  
 このタスクの詳細については、「 [WMI Data Reader Task](../../integration-services/control-flow/wmi-data-reader-task.md)」を参照してください。 WQL (WMI Query Language) の詳細については、MSDN ライブラリにある Windows Management Instrumentation のトピック「[WQL を使用したクエリ](http://go.microsoft.com/fwlink/?LinkId=79045)」を参照してください。  
  
## 静的オプション  
 **[WMIConnectionName]**  
 WMI 接続マネージャーを一覧から選択するか、**[\<新しい WMI 接続>]** をクリックして新しい接続マネージャーを作成します。  
  
 **関連トピック:** [WMI 接続マネージャー](../../integration-services/connection-manager/wmi-connection-manager.md)、[WMI 接続マネージャー エディター](../../integration-services/connection-manager/wmi-connection-manager-editor.md)  
  
 **[WQLQuerySourceType]**  
 タスクで実行する WQL クエリのソースの種類を選択します。 このプロパティのオプションを次の表に示します。  
  
|値|Description|  
|-----------|-----------------|  
|**[直接入力]**|ソースを WQL クエリに設定します。 この値を選択すると、動的オプションの **[WQLQuerySourceType]** が表示されます。|  
|**[ファイル接続]**|WQL クエリを含むファイルを選択します。 この値を選択すると、動的オプションの **[WQLQuerySourceType]** が表示されます。|  
|**変数**|WQL クエリを定義する変数に、ソースを設定します。 この値を選択すると、動的オプションの **[WQLQuerySourceType]** が表示されます。|  
  
 **[OutputType]**  
 データ テーブル、プロパティ値、またはプロパティ名と値のいずれを出力に含めるかを指定します。  
  
 **[OverwriteDestination]**  
 出力先のファイルまたは変数内の元のデータを変更しないか、上書きするか、データを追加するかを指定します。  
  
 **[DestinationType]**  
 タスクで実行する WQL クエリの出力先の種類を選択します。 このプロパティのオプションを次の表に示します。  
  
|値|Description|  
|-----------|-----------------|  
|**[ファイル接続]**|WQL クエリの結果を保存するファイルを選択します。 この値を選択すると、動的オプションの **[DestinationType]** が表示されます。|  
|**変数**|WQL クエリの結果を保存する変数を設定します。 この値を選択すると、動的オプションの **[DestinationType]** が表示されます。|  
  
## [WQLQuerySourceType] 動的オプション  
  
### [WQLQuerySourceType] = [直接入力]  
 **[WQLQuerySource]**  
 クエリを指定します。または、参照 ([...]) をクリックし、**[WQL クエリ]** ダイアログ ボックスを使用してクエリを入力します。  
  
### [WQLQuerySourceType] = [ファイル接続]  
 **[WQLQuerySource]**  
 ファイル接続マネージャーを一覧から選択するか、**[\<新しい接続>]** をクリックして新しい接続マネージャーを作成します。  
  
 **関連トピック:** [ファイル接続マネージャー](../../integration-services/connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
### [WQLQuerySourceType] = [変数]  
 **[WQLQuerySource]**  
 変数を一覧から選択するか、**[\<新しい変数>]** をクリックして新しい変数を作成します。  
  
 **関連トピック:** [Integration Services (SSIS) 変数](../../integration-services/integration-services-ssis-variables.md)、[変数の追加](../Topic/Add%20Variable.md)  
  
## [DestinationType] 動的オプション  
  
### [DestinationType] = [ファイル接続]  
 **転送先**  
 ファイル接続マネージャーを一覧から選択するか、**[\<新しい接続>]** をクリックして新しい接続マネージャーを作成します。  
  
 **関連トピック:** [ファイル接続マネージャー](../../integration-services/connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
### [DestinationType] = [変数]  
 **転送先**  
 変数を一覧から選択するか、**[\<新しい変数>]** をクリックして新しい変数を作成します。  
  
 **関連トピック:** [Integration Services (SSIS) 変数](../../integration-services/integration-services-ssis-variables.md)、[変数の追加](../Topic/Add%20Variable.md)  
  
## 参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../integration-services/integration-services-error-and-message-reference.md)   
 [WMI データ リーダー タスク エディター ([全般] ページ)](../Topic/WMI%20Data%20Reader%20Task%20Editor%20\(General%20Page\).md)   
 [[式] ページ](../Topic/Expressions%20Page.md)   
 [WMI イベント監視タスク](../../integration-services/control-flow/wmi-event-watcher-task.md)  
  
  
---
title: "WMI イベント監視タスク |Microsoft ドキュメント"
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
- sql13.dts.designer.wmieventwatchertask.f1
helpviewer_keywords:
- WQL [Integration Services]
- WMI Event Watcher task [Integration Services]
ms.assetid: b5bb52e9-a77e-41e1-93f9-d4c3bc6b2c9a
caps.latest.revision: 53
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: c3e47e4a5ae297202ba43679fba393421880a7ea
ms.openlocfilehash: f91107cf76f48f60b23b7ee1f0f93352468a1422
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="wmi-event-watcher-task"></a>WMI イベント監視タスク
  WMI イベント監視タスクは、Windows Management Instrumentation Query Language (WQL) イベント クエリを使用して対象のイベントを指定することにより、Windows Management Instrumentation (WMI) イベントを監視します。 WMI イベント監視タスクは、次の目的で使用できます。  
  
-   ファイルがフォルダーに追加されたという通知を待機し、ファイルの処理を開始します。  
  
-   サーバー上の利用可能なメモリが、指定した割合を下回った場合、ファイルを削除するパッケージを実行します。  
  
-   アプリケーションのインストールを監視し、そのアプリケーションを使用するパッケージを実行します。  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] には、WMI 情報を読み取るタスクが含まれています。  
  
 このタスクの詳細については、次のトピックを参照してください。  
  
-   [WMI データ リーダー タスク](../../integration-services/control-flow/wmi-data-reader-task.md)  
  
## <a name="wql-queries"></a>WQL クエリ  
 WQL は SQL 言語仕様の 1 つで、WMI イベント通知やその他 WMI 固有の機能をサポートする拡張機能が付いています。 WQL の詳細については、 [MSDN ライブラリ](http://go.microsoft.com/fwlink/?linkid=62553)にある Windows Management Instrumentation のマニュアルを参照してください。  
  
> [!NOTE]  
>  WMI クラスは、Windows のバージョンによって異なります。  
  
 次のクエリは、CPU 使用率が 40% を超えた場合の通知を監視します。  
  
```  
SELECT * from __InstanceModificationEvent WITHIN 2 WHERE TargetInstance ISA 'Win32_Processor' and TargetInstance.LoadPercentage > 40  
```  
  
 次のクエリは、ファイルがフォルダーに追加された場合の通知を監視します。  
  
```  
SELECT * FROM __InstanceCreationEvent WITHIN 10 WHERE TargetInstance ISA "CIM_DirectoryContainsFile" and TargetInstance.GroupComponent= "Win32_Directory.Name=\"c:\\\\WMIFileWatcher\""   
```  
  
## <a name="custom-logging-messages-available-on-the-wmi-event-watcher-task"></a>WMI イベント監視タスクで使用できるカスタム ログ メッセージ  
 次の表は、WMI イベント監視タスクのカスタム ログ エントリの一覧です。 詳細については、「[Integration Services &#40;SSIS&#41; のログ記録](../../integration-services/performance/integration-services-ssis-logging.md)」を参照してください。  
  
|ログ エントリ|Description|  
|---------------|-----------------|  
|**WMIEventWatcherEventOccurred**|タスクが監視しているイベントが発生したことを示します。|  
|**WMIEventWatcherTimedout**|タスクがタイムアウトしたことを示します。|  
|**WMIEventWatcherWatchingForWMIEvents**|タスクが WQL クエリの実行を開始したことを示します。 このエントリには、クエリが含まれています。|  
  
## <a name="configuration-of-the-wmi-event-watcher-task"></a>WMI イベント監視タスクの構成  
 WMI データ リーダー タスクは、次の方法で構成できます。  
  
-   使用する WMI 接続マネージャーを指定します。  
  
-   WQL クエリの実行元を指定します。 実行元には、タスクの外部の変数またはファイルを設定できます。また、クエリはタスクのプロパティ内に格納できます。  
  
-   WMI イベントが発生したときにタスクが実行するアクションを指定します。 イベント通知およびイベント後の状態のログが記録できます。または、WMI イベント、通知、およびイベント後の状態に関連する情報を提供する、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のカスタム イベントを発生させることができます。  
  
-   イベントに対するタスクの応答方法を定義します。 タスクは、イベントに応じて、成功または失敗するように構成できます。または、単にイベントを再度監視するように構成することもできます。  
  
-   WMI クエリがタイムアウトしたときに、タスクが実行するアクションを指定します。 タイムアウトとタイムアウト後の状態のログを記録できます。または、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のカスタム イベントを発生させ、WMI イベントのタイムアウトを示し、タイムアウトとタイムアウトの状態のログを記録できます。  
  
-   タイムアウトに対するタスクの応答方法を定義します。 タスクは成功または失敗するように構成できます。または、単にイベントを再度監視するように構成することもできます。  
  
-   タスクがイベントを監視する回数を指定します。  
  
-   タイムアウトを指定します。  
  
 監視元がファイルの場合、WMI イベント監視タスクは、ファイル接続マネージャーを使用してファイルに接続します。 詳細については、「 [フラット ファイル接続マネージャー](../../integration-services/connection-manager/flat-file-connection-manager.md)」を参照してください。  
  
 WMI イベント監視タスクは、WMI 接続マネージャーを使用して、WMI 情報を読み取るサーバーに接続します。 詳細については、「 [WMI 接続マネージャー](../../integration-services/connection-manager/wmi-connection-manager.md)」を参照してください。  
  
 プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [[WMI イベント監視タスク エディター] &#40;[全般] ページ&#41;](../../integration-services/control-flow/wmi-event-watcher-task-editor-general-page.md)  
  
-   [[WMI イベント監視タスク エディター] &#40;[WMI オプション] ページ&#41;](../../integration-services/control-flow/wmi-event-watcher-task-editor-wmi-options-page.md)  
  
-   [[式] ページ](../../integration-services/expressions/expressions-page.md)  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーでこれらのプロパティを設定する方法については、次のトピックを参照してください。  
  
-   [タスクまたはコンテナーのプロパティを設定する](http://msdn.microsoft.com/library/52d47ca4-fb8c-493d-8b2b-48bb269f859b)  
  
## <a name="programmatic-configuration-of-the-wmi-event-watcher-task"></a>プログラムによる WMI イベント監視タスクの構成  
 プログラムによってこれらのプロパティを設定する方法の詳細については、次のトピックを参照してください。  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.WmiEventWatcherTask.WmiEventWatcherTask>  
  
  

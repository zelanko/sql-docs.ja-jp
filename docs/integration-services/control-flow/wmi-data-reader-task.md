---
title: "WMI データ リーダー タスク | Microsoft Docs"
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
  - "sql13.dts.designer.wmidatareadertask.f1"
helpviewer_keywords: 
  - "WQL [Integration Services]"
  - "WMI データ リーダー タスク [Integration Services]"
ms.assetid: dae57067-0275-4ac3-8f34-1b9d169f1112
caps.latest.revision: 49
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 49
---
# WMI データ リーダー タスク
  WMI データ リーダー タスクは、WQL (Windows Management Instrumentation Query Language) を使用してクエリを実行し、コンピューター システムに関する WMI から情報を返します。 WMI データ リーダー タスクは、次の目的で使用できます。  
  
-   ローカルまたはリモート コンピューター上の Windows イベント ログのクエリを実行し、その情報をファイルまたは変数に書き込みます。  
  
-   ハードウェア コンポーネントの存在、状態、またはプロパティに関する情報を取得し、この情報を使用して制御フロー内の他のタスクを実行するかどうかを決定します。  
  
-   アプリケーションの一覧を取得し、インストールされている各アプリケーションのバージョンを判別します。  
  
 WMI データ リーダー タスクは、次の方法で構成できます。  
  
-   使用する WMI 接続マネージャーを指定します。  
  
-   WQL クエリの実行元を指定します。 このクエリは、タスクのプロパティ内に格納できます。または、タスク外の変数またはファイル内にも格納できます。  
  
-   WQL クエリ結果の形式を定義します。 このタスクでは、テーブル、プロパティの名前と値のペア、またはプロパティ値の形式がサポートされています。  
  
-   クエリの実行先を指定します。 この実行先には、変数またはファイルを設定できます。  
  
-   クエリの実行先で、上書き、保持、または追加のいずれを行うかを示します。  
  
 実行元または実行先がファイルの場合、WMI データ リーダー タスクは、ファイル接続マネージャーを使用してファイルに接続します。 詳細については、「[フラット ファイル接続マネージャー](../../integration-services/connection-manager/flat-file-connection-manager.md)」をご覧ください。  
  
 WMI データ リーダー タスクは、WMI 接続マネージャーを使用して、WMI 情報を読み取るサーバーに接続します。 詳細については、「[WMI 接続マネージャー](../../integration-services/connection-manager/wmi-connection-manager.md)」をご覧ください。  
  
## WQL クエリ  
 WQL は SQL 言語仕様の 1 つで、WMI イベント通知やその他 WMI 固有の機能をサポートする拡張機能が付いています。 WQL の詳細については、[MSDN ライブラリ](http://go.microsoft.com/fwlink/?linkid=7022)にある Windows Management Instrumentation のマニュアルをご覧ください。  
  
> [!NOTE]  
>  WMI クラスは、Windows のバージョンによって異なります。  
  
 次の WQL クエリは、アプリケーション ログ イベント内のエントリを返します。  
  
```  
SELECT * FROM Win32_NTLogEvent WHERE LogFile = 'Application' AND (SourceName='SQLISService' OR SourceName='SQLISPackage') AND TimeGenerated > '20050117'  
```  
  
 次の WQL クエリは、論理ディスク情報を返します。  
  
```  
SELECT FreeSpace, DeviceId, Size, SystemName, Description FROM Win32_LlogicalDisk  
```  
  
 次の WQL クエリは、オペレーティング システムに対する QFE (Quick Fix Engineering) 更新の一覧を返します。  
  
```  
Select * FROM Win32_QuickFixEngineering  
```  
  
## WMI データ リーダー タスクで使用できるカスタム ログ メッセージ  
 次の表は、WMI データ リーダー タスクのカスタム ログ エントリの一覧です。 詳細については、「[Integration Services &#40;SSIS&#41; のログ記録](../../integration-services/performance/integration-services-ssis-logging.md)」と「[ログ記録用のカスタム メッセージ](../../integration-services/performance/custom-messages-for-logging.md)」を参照してください。  
  
|ログ エントリ|Description|  
|---------------|-----------------|  
|**WMIDataReaderGettingWMIData**|タスクが WMI データの読み取りを開始したことを示します。|  
|**WMIDataReaderOperation**|タスクで実行された WQL クエリを報告します。|  
  
## WMI データ リーダー タスクの構成  
 プロパティはプログラムによって設定するか、または [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから設定できます。  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [[WMI データ リーダー タスク エディター] &#40;[WMI オプション] ページ&#41;](../Topic/WMI%20Data%20Reader%20Task%20Editor%20\(WMI%20Options%20Page\).md)  
  
-   [[式] ページ](../Topic/Expressions%20Page.md)  
  
 プログラムによってこれらのプロパティを設定する方法については、次のトピックを参照してください。  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.WmiDataReaderTask.WmiDataReaderTask>  
  
## 関連タスク  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーでこれらのプロパティを設定する方法については、次のトピックを参照してください。  
  
-   [タスクまたはコンテナーのプロパティを設定する](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md)  
  
## 参照  
 [Integration Services タスク](../../integration-services/control-flow/integration-services-tasks.md)   
 [制御フロー](../../integration-services/control-flow/control-flow.md)  
  
  
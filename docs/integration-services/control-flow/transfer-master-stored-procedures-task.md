---
title: "Master ストアド プロシージャ転送タスク | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.transfermasterspstask.f1"
helpviewer_keywords: 
  - "Master ストアド プロシージャ転送タスク [Integration Services]"
ms.assetid: 81702560-48a3-46d1-a469-e41304c7af8e
caps.latest.revision: 25
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 25
---
# Master ストアド プロシージャ転送タスク
  Master ストアド プロシージャ転送タスクは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンス上の **master** データベース間で、1 つ以上のユーザー定義ストアド プロシージャを転送します。 **master** データベースからストアド プロシージャを転送するには、プロシージャの所有者が dbo である必要があります。  
  
 Master ストアド プロシージャ転送タスクは、すべてのストアド プロシージャまたは指定したストアド プロシージャのみを転送するように設定できます。 このタスクでは、システム ストアド プロシージャはコピーされません。  
  
 転送する master ストアド プロシージャが既に転送先に存在している場合もあります。 Master ストアド プロシージャ転送タスクでは、既存のストアド プロシージャの処理を次のように設定できます。  
  
-   既存のストアド プロシージャを上書きします。  
  
-   重複するストアド プロシージャが存在する場合、タスクを失敗とします。  
  
-   重複するストアド プロシージャをスキップします。  
  
 Master ストアド プロシージャ転送タスクは実行時に、2 つの SMO 接続マネージャーを使用して、転送元および転送先サーバーに接続します。 SMO 接続マネージャーの構成は Master ストアド プロシージャ転送タスクとは別に行い、Master ストアド プロシージャ転送タスクは SMO 接続マネージャーを参照します。 SMO 接続マネージャーは、サーバーと、サーバーに接続する際に使用する認証モードを指定します。 詳細については、「[SMO 接続マネージャー](../../integration-services/connection-manager/smo-connection-manager.md)」を参照してください。  
  
## SQL Server のインスタンス間でのストアド プロシージャの転送  
 Master ストアド プロシージャ転送タスクでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 転送元と転送先をサポートします。  
  
## イベント  
 Master ストアド プロシージャ転送タスクでは、転送されたストアド プロシージャの数を報告する情報イベントと、ストアド プロシージャが上書きされた場合の警告イベントが発生します。  
  
 Master ストアド プロシージャ転送タスクでは、増分中のログイン転送タスクの進捗状況は報告されません。0% または 100% 完了した場合のみ報告されます。  
  
## 実行値  
 タスクの **ExecutionValue** プロパティで定義する実行値は、転送されたストアド プロシージャの数を返します。 Master ストアド プロシージャ転送タスクの **ExecValueVariable** プロパティにユーザー定義変数を割り当てると、パッケージの他のオブジェクトからストアド プロシージャの転送に関する情報を使用できるようになります。 詳細については、「[Integration Services &#40;SSIS&#41; の変数](../../integration-services/integration-services-ssis-variables.md)」および「[パッケージで変数を使用する](../Topic/Use%20Variables%20in%20Packages.md)」を参照してください。  
  
## ログ エントリ  
 Master ストアド プロシージャ転送タスクには、次のようなカスタム ログ エントリがあります。  
  
-   TransferStoredProceduresTaskStartTransferringObjects  転送が開始されたことを報告するログ エントリです。 ログ エントリには、開始時刻が含まれます。  
  
-   TransferSStoredProceduresTaskFinishedTransferringObjects  転送が終了したことを報告するログ エントリです。 ログ エントリには、終了時刻が含まれます。  
  
 また、**OnInformation** イベントのログ エントリは転送されたストアド プロシージャの数を報告し、**OnWarning** イベントのログ エントリは転送先でストアド プロシージャが上書きされると書き込まれます。  
  
## セキュリティおよび権限  
 ソースの **master** データベースでストアド プロシージャの一覧を表示する権限が必要です。また、転送先サーバーの sysadmin サーバー ロールのメンバーであるか、転送先サーバーの **master** データベースでストアド プロシージャを作成する権限を持つユーザーである必要があります。  
  
## Master ストアド プロシージャ転送タスクの構成  
 プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [[Master ストアド プロシージャ転送タスク エディター] &#40;[全般] ページ&#41;](../Topic/Transfer%20Master%20Stored%20Procedures%20Task%20Editor%20\(General%20Page\).md)  
  
-   [[Master ストアド プロシージャ転送タスク エディター] &#40;[ストアド プロシージャ] ページ&#41;](../Topic/Transfer%20Master%20Stored%20Procedures%20Task%20Editor%20\(Stored%20Procedures%20Page\).md)  
  
-   [[式] ページ](../Topic/Expressions%20Page.md)  
  
 プログラムによってこれらのプロパティを設定する方法については、次のトピックを参照してください。  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.TransferStoredProceduresTask.TransferStoredProceduresTask>  
  
### プログラムによる Master ストアド プロシージャ転送タスクの構成  
  
## 関連タスク  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーでこれらのプロパティを設定する方法については、次のトピックを参照してください。  
  
-   [タスクまたはコンテナーのプロパティを設定する](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md)  
  
## 参照  
 [SQL Server オブジェクトの転送タスク](../../integration-services/control-flow/transfer-sql-server-objects-task.md)   
 [Integration Services タスク](../../integration-services/control-flow/integration-services-tasks.md)   
 [制御フロー](../../integration-services/control-flow/control-flow.md)  
  
  
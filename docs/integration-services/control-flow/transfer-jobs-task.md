---
title: "ジョブ転送タスク | Microsoft Docs"
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
  - "sql13.dts.designer.transferjobstask.f1"
helpviewer_keywords: 
  - "ジョブ転送タスク [Integration Services]"
ms.assetid: 1bf33885-9c5b-47e4-a549-f5920b66a1de
caps.latest.revision: 28
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 28
---
# ジョブ転送タスク
  ジョブ転送タスクは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンス間で 1 つ以上の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブを転送します。  
  
 ジョブ転送タスクは、すべてのジョブまたは指定したジョブのみを転送するように構成できます。 また、転送先で転送したジョブを有効にするかどうかも指定できます。  
  
 転送しようとするジョブが既に転送先に存在している場合もあります。 ジョブ転送タスクでは、既存のジョブの処理を次のように構成できます。  
  
-   既存のジョブを上書きします。  
  
-   重複するジョブが存在する場合、タスクを失敗させます。  
  
-   重複するジョブをスキップします。  
  
 実行時に、ジョブ転送タスクは 1 つまたは 2 つの SMO 接続マネージャーを使用して、転送元および転送先サーバーに接続します。 SMO 接続マネージャーはジョブ転送タスクとは別に構成され、ジョブ転送タスクで参照されます。 SMO 接続マネージャーは、サーバーと、このサーバーにアクセスするときに使用する認証モードを指定します。 詳細については、「[SMO 接続マネージャー](../../integration-services/connection-manager/smo-connection-manager.md)」を参照してください。  
  
## SQL Server のインスタンス間でのジョブの転送  
 ジョブ転送タスクは、転送元または転送先として、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をサポートします。 転送元または転送先として使用するバージョンに関する制限はありません。  
  
## イベント  
 ジョブ転送タスクでは、転送されたジョブの数を報告する情報イベントと、ジョブが上書きされた場合の警告イベントが発生します。 ジョブの転送の進捗状況は報告されません。0% または 100% 完了した場合のみ報告されます。  
  
## 実行値  
 タスクの **ExecutionValue** プロパティで定義される実行値は、転送されたジョブの数を返します。 ジョブ転送タスクの **ExecValueVariable** プロパティにユーザー定義変数を割り当てると、パッケージの他のオブジェクトからジョブの転送に関する情報を使用できるようになります。 詳細については、「[Integration Services (SSIS) の変数](../../integration-services/integration-services-ssis-variables.md)」および「[パッケージで変数を使用する](../Topic/Use%20Variables%20in%20Packages.md)」を参照してください。  
  
## ログ エントリ  
 ジョブ転送タスクには、次のようなカスタム ログ エントリがあります。  
  
-   TransferJobsTaskStarTransferringObjects   転送が開始されたことを報告するログ エントリです。 ログ エントリには、開始時刻が含まれます。  
  
-   TransferJobsTaskFinishedTransferringObjects    転送が終了したことを報告するログ エントリです。 ログ エントリには、終了時刻が含まれます。  
  
 また、**OnInformation** イベントのログ エントリは転送されたジョブの数を報告し、**OnWarning** イベントのログ エントリは転送先でジョブが上書きされると書き込まれます。  
  
## セキュリティおよび権限  
 ジョブを転送するユーザーは、sysadmin 固定サーバー ロールのメンバー、または転送元および転送先の両方の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの msdb データベースで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント固定データベース ロールのメンバーである必要があります。  
  
## ジョブ転送タスクの構成  
 プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [[ジョブ転送タスク エディター] ([全般] ページ)](../Topic/Transfer%20Jobs%20Task%20Editor%20\(General%20Page\).md)  
  
-   [[ジョブ転送タスク エディター] ([ジョブ] ページ)](../Topic/Transfer%20Jobs%20Task%20Editor%20\(Jobs%20Page\).md)  
  
-   [[式] ページ](../Topic/Expressions%20Page.md)  
  
 プログラムによってこれらのプロパティを設定する方法については、次のトピックを参照してください。  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.TransferJobsTask.TransferJobsTask>  
  
## 関連タスク  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーでこれらのプロパティを設定する方法については、次のトピックを参照してください。  
  
-   [タスクまたはコンテナーのプロパティを設定する](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md)  
  
## 参照  
 [Integration Services タスク](../../integration-services/control-flow/integration-services-tasks.md)   
 [制御フロー](../../integration-services/control-flow/control-flow.md)  
  
  
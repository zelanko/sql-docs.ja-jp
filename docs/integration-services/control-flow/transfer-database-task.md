---
title: "データベース転送タスク |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.transferdatabasetask.f1
helpviewer_keywords:
- Transfer Database task [Integration Services]
ms.assetid: b9a2e460-cdbc-458f-8df8-06b8b2de3d67
caps.latest.revision: 26
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 86e2b602632d1492d3889981af041c5ee38cfb6b
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="transfer-database-task"></a>データベース転送タスク
  データベース転送タスクは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の 2 つのインスタンスの間で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースを転送します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクトをコピーして転送するだけの他のタスクに対し、データベース転送タスクでは、データベースをコピーまたは移動できます。 このタスクを使用して、同じサーバー内でデータベースをコピーすることもできます。  
  
## <a name="offline-and-online-modes"></a>オフライン モードとオンライン モード  
 データベースは、オンライン モードまたはオフライン モードで転送できます。 オンライン モードでは、データベースがアタッチされたまま、SQL 管理オブジェクト (SMO) を使用して転送され、データベース オブジェクトがコピーされます。 オフライン モードでは、データベースがデタッチされた後、データベース ファイルがコピーまたは移動されます。転送が正常に完了した後、データベースが転送先にアタッチされます。 データベースのコピーの場合、コピーが正常に完了するとデータベースは転送元に再びアタッチされます。 オフライン モードでは、データベースは短時間にコピーされますが、転送が行われている間はデータベースを利用できなくなります。  
  
 オフライン モードを使用する場合は、転送元サーバーと転送先サーバー上でデータベース ファイルを格納するネットワーク ファイル共有を指定する必要があります。 このフォルダーが共有されていてユーザーがフォルダーにアクセスできる場合、 \\\computername\Program Files\myfolder\\という構文を使用してネットワーク共有を参照できます。 それ以外の場合は、 \\\computername\c$\Program Files\myfolder\\という構文を使用する必要があります。 後者の構文を使用するには、転送元と転送先のネットワーク共有に対する書き込みアクセスがユーザーに許可されている必要があります。  
  
## <a name="transfer-of-databases-between-versions-of-sql-server"></a>SQL Server のバージョン間でのデータベースの転送  
 データベース転送タスクは、異なるバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンス間でデータベースを転送できます。  
  
## <a name="events"></a>イベント  
 データベース転送タスクでは、エラー メッセージ転送の進捗状況は報告されません。0% または 100% 完了した場合のみ報告されます。  
  
## <a name="execution-value"></a>実行値  
 タスクの **ExecutionValue** プロパティで定義される実行値は、値 1 を返します。これは、他の転送タスクとは異なり、データベース転送タスクでは 1 つのデータベースしか転送できないためです。  
  
 データベース転送タスクの **ExecValueVariable** プロパティにユーザー定義変数を割り当てると、エラー メッセージ転送に関する情報をパッケージ内の他のオブジェクトで利用できるようになります。 詳細については、「[Integration Services &#40;SSIS&#41; の変数](../../integration-services/integration-services-ssis-variables.md)」と「[パッケージで変数を使用する](http://msdn.microsoft.com/library/7742e92d-46c5-4cc4-b9a3-45b688ddb787)」を参照してください。  
  
## <a name="log-entries"></a>ログ エントリ  
 データベース転送タスクには、次のカスタム ログ エントリが含まれています。  
  
-   SourceSQLServer: このログ エントリは、転送元サーバーの名前を一覧表示します。  
  
-   DestSQLServer: このログ エントリは、転送先サーバーの名前を一覧表示します。  
  
-   SourceDB: このログ エントリは、転送されたデータベースの名前を一覧表示します。  
  
 さらに、転送先データベースが上書きされたときに、 **OnInformation** イベントのログ エントリが書き込まれます。  
  
## <a name="security-and-permissions"></a>セキュリティおよび権限  
 オフライン モードを使用してデータベースを転送するには、パッケージを実行するユーザーが sysadmin サーバー ロールのメンバーである必要があります。  
  
 オンライン モードを使用してデータベースを転送するには、パッケージを実行するユーザーが sysadmin サーバー ロールのメンバーであるか、または選択されたデータベースのデータベース所有者 (dbo) である必要があります。  
  
## <a name="configuration-of-the-transfer-database-task"></a>データベース転送タスクの構成  
 データベースの転送が失敗した場合に転送元データベースへの再アタッチを試行するかどうかを指定できます。  
  
 さらに、データベース転送タスクでは、転送先に同じ名前のデータベースが存在する場合にそのデータベースを上書きするように構成できます。  
  
 転送プロセスの一部として、転送元データベースの名前を変更することもできます。 転送先の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに同じ名前のデータベースが存在する場合にデータベースを転送するには、転送元データベースの名前を変更することでデータベースを転送できます。 ただし、データベース ファイルの名前も異なっている必要があります。同じ名前のデータベース ファイルが転送先に既に存在すると、タスクは失敗します。  
  
 データベースをコピーする場合、データベースのサイズは、コピー先サーバーの **model** データベースのサイズより小さくすることはできません。 コピーするデータベースのサイズを大きくするか、 **model**データベースのサイズを小さくできます。  
  
 実行時、データベース転送タスクは、1 つまたは 2 つの SMO 接続マネージャーを使用して、転送元サーバーと転送先サーバーに接続します。 同じサーバー上にデータベースのコピーを作成する場合は、SMO 接続マネージャーが 1 つだけ必要です。 これらの SMO 接続マネージャーはデータベース転送タスクとは別に構成され、データベース転送タスクで参照されます。 SMO 接続マネージャーは、サーバーと、タスクがこのサーバーにアクセスするときに使用する認証モードを指定します。 詳細については、「 [SMO 接続マネージャー](../../integration-services/connection-manager/smo-connection-manager.md)」をご覧ください。  
  
 プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [データベース転送タスク エディター &#40;[全般] ページ&#41;](../../integration-services/control-flow/transfer-database-task-editor-general-page.md)  
  
-   [データベース転送タスク エディター &#40;[データベース] ページ&#41;](../../integration-services/control-flow/transfer-database-task-editor-databases-page.md)  
  
-   [[式] ページ](../../integration-services/expressions/expressions-page.md)  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーでこれらのプロパティを設定する方法については、次のトピックを参照してください。  
  
-   [タスクまたはコンテナーのプロパティを設定する](http://msdn.microsoft.com/library/52d47ca4-fb8c-493d-8b2b-48bb269f859b)  
  
## <a name="programmatic-configuration-of-the-transfer-database-task"></a>プログラムによるデータベース転送タスクの構成  
 プログラムによってこれらのプロパティを設定する方法の詳細については、次のトピックを参照してください。  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.TransferDatabaseTask.TransferDatabaseTask>  
  
  

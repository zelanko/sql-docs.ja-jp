---
title: "ログイン転送タスク |Microsoft ドキュメント"
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
- sql13.dts.designer.transferloginstask.f1
helpviewer_keywords:
- Transfer Logins task [Integration Services]
ms.assetid: 1df60fd6-c019-405d-8155-c330dbac2cc1
caps.latest.revision: 25
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 02215c15fbbbcb4f7fd5ee5638afa4e0092e86c9
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="transfer-logins-task"></a>ログイン転送タスク
  ログイン転送タスクは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンス間で 1 つ以上のログインを転送します。  
  
## <a name="transfer-logins-between-instances-of-sql-server"></a>SQL Server のインスタンス間でのログインの転送  
 ログイン転送タスクでは、転送元または転送先として、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をサポートします。  
  
## <a name="events"></a>イベント  
 ログイン転送タスクでは、転送されたログインの数を報告する情報イベントと、ログインが上書きされた場合の警告イベントが発生します。  
  
 ログインの転送の進捗状況は報告されません。0% または 100% 完了した場合のみ報告されます。  
  
## <a name="execution-value"></a>実行値  
 タスクの **ExecutionValue** プロパティで定義する実行値は、転送されたログインの数を返します。 ログイン転送タスクの **ExecValueVariable** プロパティにユーザー定義変数を割り当てると、パッケージの他のオブジェクトからログインの転送に関する情報を使用できるようになります。 詳細については、「[Integration Services (SSIS) の変数](../../integration-services/integration-services-ssis-variables.md)」および「[パッケージで変数を使用する](http://msdn.microsoft.com/library/7742e92d-46c5-4cc4-b9a3-45b688ddb787)」を参照してください。  
  
## <a name="log-entries"></a>ログ エントリ  
 ログイン転送タスクには、次のようなカスタム ログ エントリがあります。  
  
-   TransferLoginsTaskStarTransferringObjects   転送が開始されたことを報告するログ エントリです。 ログ エントリには、開始時刻が含まれます。  
  
-   TransferLoginsTaskFinishedTransferringObjects   転送が完了したことを報告するログ エントリです。 ログ エントリには、終了時刻が含まれます。  
  
 また、 **OnInformation** イベントのログ エントリは転送されたログインの数を報告し、 **OnWarning** イベントのログ エントリは転送先でログインが上書きされると書き込まれます。  
  
## <a name="security-and-permissions"></a>セキュリティおよび権限  
 転送元サーバーのログインを参照し、転送先サーバーにログインを作成するユーザーは、両方のサーバーのサーバー ロール sysadmin のメンバーでなければなりません。  
  
## <a name="configuration-of-the-transfer-logins-task"></a>ログイン転送タスクの構成  
 ログイン転送タスクは、すべてのログイン、指定したログインのみ、または指定したデータベースにアクセスしたすべてのログインを転送するように構成できます。 sa ログインは転送できません。 sa ログインの名前は変更できますが、名前を変更した sa ログインを転送することはできません。  
  
 また、ログインに関連付けられているセキュリティ識別子 (SID) をコピーするかどうかも指定できます。 ログイン転送タスクをデータベース転送タスクと共に使用する場合、SID を転送先にコピーする必要があります。コピーしない場合、転送したログインが転送先データベースで認識されません。  
  
 転送先では、転送されたログインは無効にされ、ランダムなパスワードが割り当てられます。 ログインを使用する前に、転送先サーバーの sysadmin ロールのメンバーがパスワードを変更して、ログインを有効にする必要があります。  
  
 転送するログインが既に転送先に存在している場合もあります。 ログイン転送タスクでは、既存のログインの処理を次のように構成できます。  
  
-   既存のログインを上書きします。  
  
-   重複するログインが存在する場合、タスクを失敗とします。  
  
-   重複するログインをスキップします。  
  
 ログイン転送タスクは実行時に、2 つの SMO 接続マネージャーを使用して、転送元および転送先サーバーに接続します。 SMO 接続マネージャーの構成はログイン転送タスクとは別に行い、ログイン転送タスクは SMO 接続マネージャーを参照します。 SMO 接続マネージャーは、サーバーと、サーバーに接続する際に使用する認証モードを指定します。 詳細については、「 [SMO 接続マネージャー](../../integration-services/connection-manager/smo-connection-manager.md)」を参照してください。  
  
 プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [[ログイン転送タスク エディター] ([全般] ページ)](../../integration-services/control-flow/transfer-logins-task-editor-general-page.md)  
  
-   [[ログイン転送タスク エディター] ([ログイン] ページ)](../../integration-services/control-flow/transfer-logins-task-editor-logins-page.md)  
  
-   [[式] ページ](../../integration-services/expressions/expressions-page.md)  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーでこれらのプロパティを設定する方法については、次のトピックを参照してください。  
  
-   [タスクまたはコンテナーのプロパティを設定する](http://msdn.microsoft.com/library/52d47ca4-fb8c-493d-8b2b-48bb269f859b)  
  
## <a name="programmatic-configuration-of-the-transfer-logins-task"></a>プログラムによるログイン転送タスクの構成  
 プログラムによってこれらのプロパティを設定する方法の詳細については、次のトピックを参照してください。  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.TransferLoginsTask.TransferLoginsTask>  
  
  

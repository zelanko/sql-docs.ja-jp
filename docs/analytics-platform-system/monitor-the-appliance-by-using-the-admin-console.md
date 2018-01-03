---
title: "管理コンソール (Analytics Platform System) を使用してアプライアンスを監視します。"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: 
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 294ba6ac-b1ff-46ea-ba32-d8b32cb4cdc2
caps.latest.revision: "26"
ms.openlocfilehash: db27003d4e1efd54a179551f585fb23ce9c0ed82
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="monitor-the-appliance-by-using-the-admin-console"></a>管理コンソールを使用してアプライアンスを監視します。
管理者コンソールは、アプライアンスの状態、ヘルス、およびパフォーマンス情報を表示する SQL Server PDW の web アプリケーションです。 ユーザーは、Internet Explorer で、管理コンソールに接続します。  
  
## <a name="About"></a>管理者コンソールについて  
![アプライアンス コンソールのホーム](./media/monitor-the-appliance-by-using-the-admin-console/SQL_Server_PDW_AdminConsol_ApplHome.png "SQL_Server_PDW_AdminConsol_ApplHome")  
  
**アプライアンス**  
ホーム (Home)  
アプライアンスの状態の概要を提供します。  
  
正常性  
各ノード内の各監視対象コンポーネントの正常性を示すインジケーターがアプライアンス トポロジを表示します。 使用すると、個々 のノードの現在の状態と、ノードのコンポーネントのプロパティを表示できます。  
  
ハードウェアとソフトウェアのアラートが表示されます。  
  
パフォーマンス モニター  
パフォーマンス モニターのグラフが表示されます。  
  
**Parallel Data Warehouse**  
ホーム (Home)  
PDW 状態の概要を提供します。  
  
セッション  
PDW ユーザーのアクティブなセッションを表示します。 これにより、リソースの競合を監視するのに役立ちます。  
  
クエリ  
実行中のクエリや最近完了したクエリの一覧を表示します。 存在する場合、関連のエラーが表示されます。 クエリの実行プランとノードの実行情報の詳細を表示する機能も用意されています。  
  
読み込みます  
存在する場合は、表示プラン、PDW の読み込み、および関連するエラーは、の現在の状態を読み込みます。  
  
バックアップ/復元を行う  
PDW のログを表示では、バックアップし、復元操作です。  
  
正常性  
各ノード内の各監視対象コンポーネントの正常性を示すインジケーターが PDW トポロジを表示します。 使用すると、個々 のノードの現在の状態と、ノードのコンポーネントのプロパティを表示できます。  
  
ハードウェアとソフトウェアのアラートが表示されます。  
  
リソース  
PDW のリソースのロックとその現在の状態の一覧を表示します。  
  
ストレージ  
PDW の記憶域使用率の概要を示します。  
  
パフォーマンス モニター  
PDW パフォーマンス モニターのグラフが表示されます。  
  
**HDInsight**  
ホーム (Home)  
HDInsight の状態の概要を提供します。  
  
HDFS  
HDInsight 領域使用率の概要し、上位 10 個のスペースのコンシューマーを示します。  
  
Map と Reduce  
MapReduce ジョブの状態をまとめたものです。  
  
正常性  
各ノード内の各監視対象コンポーネントの正常性を示すインジケーターが HDInsight トポロジを表示します。 使用すると、個々 のノードの現在の状態と、ノードのコンポーネントのプロパティを表示できます。  
  
ハードウェアとソフトウェアのアラートが表示されます。  
  
ストレージ  
HDInsight の記憶域使用率の概要を示します。  
  
パフォーマンス モニター  
パフォーマンス モニターのグラフが表示されます。  
  
> [!NOTE]  
> 管理者コンソールには、1024 x 768 の画面解像度があります。 管理コンソールには、1280 x 1024 以上の画面解像度で最適なが表示されます。  
  
## <a name="Connect"></a>管理者コンソールへの接続します。  
管理者コンソールに接続する必要があります。  
  
-   At 最低 Internet Explorer 10 のバージョン。  
  
-   管理コンソールにアクセスする権限です。 <!-- MISSING LINKS See [Grant Permissions to Use the Admin Console &#40;SQL Server PDW&#41;](../sqlpdw/grant-permissions-to-use-the-admin-console-sql-server-pdw.md).  -->  
  
-   コントロールのノードのクラスターの IP アドレス。  これは、SQL Server PDW 管理者から取得します。  
  
管理コンソールに接続するには、コントロールのノードのクラスターの IP アドレスを参照する Internet Explorer および https を使用します。 たとえば、コントロールのノードのクラスターの IP アドレスは`10.192.63.102`、入力`https://10.192.63.102`ブラウザーのアドレス バーにします。 最初の画面を要求、**ログイン**と**パスワード**です。 いずれか、SQL Server 認証ログインとパスワード、または、Windows 認証ログインと Windows パスワードを提供します。 Windows 認証ログインを使用して、管理コンソールは権限借用を使用します。  
  
## <a name="RelatedTasks"></a>管理コンソール タスク  
管理コンソールでは、次の監視機能を提供します。  
  
|||  
|-|-|  
|**情報の種類**|**管理コンソールにアクセスする方法**|  
|アプライアンスの全体的な状態|をクリックして**のアプライアンス状態**上部のメニューまたは**ホーム**です。|  
|オブジェクト エクスプローラーには|をクリックして**アラート**です。 詳細については、次を参照してください。[管理者コンソールのアラートについて &#40;です。Analytics Platform System &#41;](understanding-admin-console-alerts.md).|  
|アプライアンス コンポーネントとそれらの状態|をクリックして**のアプライアンス状態**上部のメニューまたは**ホーム**です。|  
|要求 (クエリ、読み込み、バックアップ、復元など) を監視|をクリックして**セッション**を現在アクティブまたは最近使用したセッションを表示します。<br /><br />をクリックして**クエリ**を現在アクティブなまたは最近使用したクエリを参照してください。 クエリに表示される情報には、読み込み、バックアップ、および復元が含まれています。<br /><br />をクリックして**ロック**にアクティブなロックを参照してください。|  
|読み込み、バックアップ、および復元に関する追加情報を監視します。|をクリックして**負荷**または**バックアップ/復元**です。|  
|パフォーマンス情報|をクリックして**パフォーマンス モニター**です。|  
  
## <a name="see-also"></a>参照  
[アプライアンスの監視 &#40;です。Analytics Platform System &#41;](appliance-monitoring.md)  
  

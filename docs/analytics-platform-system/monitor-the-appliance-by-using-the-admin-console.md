---
title: 管理者コンソールの Analytics Platform System での監視 |Microsoft Docs
description: Analytics Platform System では、アプライアンスの状態、正常性、およびパフォーマンス情報を表示する web アプリケーションは、管理コンソールです。 ユーザーは、インターネット ブラウザーを通じて管理コンソールに接続します。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 7fb3bf769d3145118359af0e33e3cf01a0b6d325
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960488"
---
# <a name="monitor-the-appliance-with-the-admin-console---analytics-platform-system"></a>管理コンソール - Analytics Platform System とアプライアンスを監視します。
管理者コンソールは、アプライアンスの状態、正常性、およびパフォーマンス情報を表示する SQL Server PDW の web アプリケーションです。 ユーザーは、Internet explorer の管理コンソールに接続します。  
  
## <a name="About"></a>管理者コンソールについて  
![アプライアンス コンソール ホーム](./media/monitor-the-appliance-by-using-the-admin-console/SQL_Server_PDW_AdminConsol_ApplHome.png "SQL_Server_PDW_AdminConsol_ApplHome")  
  
**アプライアンス**  
ホーム (Home)  
アプライアンスの状態の簡単な概要を提供します。  
  
Health  
アプライアンスのトポロジの各ノード内の各監視対象コンポーネントの正常性を示すインジケーターが表示されます。 個々 のノードの現在の状態とノードのコンポーネントのプロパティを表示することができます。  
  
ハードウェアとソフトウェアのアラートが表示されます。  
  
パフォーマンス モニター  
パフォーマンス モニターのグラフが表示されます。  
  
**Parallel Data Warehouse**  
ホーム (Home)  
PDW 状態の簡単な概要を提供します。  
  
セッション  
PDW ユーザーのアクティブなセッションが表示されます。 これは、リソースの競合を監視できます。  
  
クエリ  
クエリの実行および最近完了したクエリの一覧を表示します。 存在する場合は、関連するエラーを表示します。 またクエリの実行プランとノードの実行情報の詳細を表示する機能を提供します。  
  
読み込み  
表示は、存在する場合、プラン、PDW 負荷、および関連するエラーは、の現在の状態を読み込みます。  
  
バックアップと復元  
バックアップし、復元操作の PDW のログを表示します  
  
Health  
PDW のトポロジの各ノード内の各監視対象コンポーネントの正常性を示すインジケーターが表示されます。 個々 のノードの現在の状態とノードのコンポーネントのプロパティを表示することができます。  
  
ハードウェアとソフトウェアのアラートが表示されます。  
  
リソース  
PDW のリソースのロックとその現在の状態を一覧表示します。  
  
ストレージ  
PDW の記憶域使用率をまとめたものです。  
  
パフォーマンス モニター  
PDW のパフォーマンス モニターのグラフが表示されます。  
 
> [!NOTE]  
> 管理者コンソールには、1024 x 768 の画面解像度があります。 管理コンソールが最も高いは、1280 x 1024 以上の画面解像度が表示されます。  
  
## <a name="Connect"></a>管理者コンソールに接続するには  
管理コンソールに接続する必要があります。  
  
-   Internet Explorer バージョン 10 以降でします。  
  
-   管理コンソールにアクセスするアクセス許可。 <!-- MISSING LINKS See [Grant Permissions to Use the Admin Console &#40;SQL Server PDW&#41;](../sqlpdw/grant-permissions-to-use-the-admin-console-sql-server-pdw.md).  -->  
  
-   コントロールのノード クラスターの IP アドレス。  これは、SQL Server PDW 管理者から取得します。  
  
管理コンソールに接続するには、コントロールのノード クラスターの IP アドレスを参照する Internet Explorer および https を使用します。 たとえば、コントロールのノード クラスターの IP アドレスは`10.192.63.102`、入力`https://10.192.63.102`ブラウザーのアドレス バーにします。 最初の画面は要求、**ログイン**と**パスワード**します。 いずれか、SQL Server 認証ログインとパスワード、または Windows 認証ログインと Windows パスワードを提供します。 Windows 認証ログインを使用して、管理コンソールは権限借用を使用します。  
  
## <a name="RelatedTasks"></a>管理コンソール タスク  
管理コンソールでは、次を監視する機能を提供します。  
  
|||  
|-|-|  
|**情報の種類**|**管理コンソールにアクセスする方法**|  
|アプライアンスの全体的な状態|をクリックして**のアプライアンス状態**上部のメニューまたは**ホーム**します。|  
|オブジェクト エクスプローラーには|クリックして**アラート**します。 詳細については、次を参照してください。[管理者コンソールのアラートについて&#40;Analytics Platform System&#41;](understanding-admin-console-alerts.md)します。|  
|アプライアンスのコンポーネントとそれらの状態|をクリックして**のアプライアンス状態**上部のメニューまたは**ホーム**します。|  
|モニターの要求 (クエリや読み込み、バックアップ、復元を含む)|クリックして**セッション**を現在アクティブなまたは最近のセッションを参照してください。<br /><br />クリックして**クエリ**を現在アクティブなまたは最近のクエリを参照してください。 クエリに表示される情報には、読み込み、バックアップ、および復元が含まれています。<br /><br />クリックして**ロック**にアクティブなロックを参照してください。|  
|読み込み、バックアップ、および復元に関する追加情報を監視します。|クリックして**読み込み**または**バックアップ/復元**します。|  
|パフォーマンス情報|クリックして**パフォーマンス モニター**します。|  
  
## <a name="see-also"></a>参照  
[アプライアンスの監視&#40;Analytics Platform System&#41;](appliance-monitoring.md)  
  

---
title: "Set-powerpivotserviceapplication コマンドレット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: powershell
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 16d10e2d-d7e1-40f1-bc9d-a4e10c61af95
caps.latest.revision: 10
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 094bf7bdb701140a45dacf0236e59d8f9232e5d4
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="set-powerpivotserviceapplication-cmdlet"></a>Set-PowerPivotServiceApplication コマンドレット
  
 [!INCLUDE[ssas-appliesto-sqlas-all](../../includes/ssas-appliesto-sqlas-all.md)] 

  プロパティを設定、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーション。  

>[!NOTE] 
>この記事には、古くなった情報と例があります。 最新バージョンには、Get-help コマンドレットを使用します。
  
 **適用対象:** SharePoint 2010 および SharePoint 2013  
  
## <a name="syntax"></a>構文  
  
```  
Set-PowerPivotServiceApplication [-Identity] <SPGeminiServiceApplicationPipeBind> [-AdministrationConnectionPoolSize <int>] [-AllowCustomWindowsCredentials] [-BusinessHoursEndTime <string>] [-BusinessHoursStartTime <string>] [-CachedDatabaseholdLimit <int>] [-Confirm <switch>] [-ConnectionPoolSize <int>] [-ConnectionPoolTimeout <int>] [-DataLoadTimeout <int>] [-DataRefreshFailureThreshold <int>] [-DataRefreshInactiveWorkbooksThreshold <int>] [-DataRefreshMaxHistory <int>] [-HealthBasedAllocation <switch>] [-LoadsToConnectionsRatioCollectionInterval <int>] [-LoadsToConnectionsRatioLimit <int>] [-MemoryDatabaseHoldLimit <int>] [-QueryReportingInterval <int>] [-RoundRobinAllocation <switch>] [-UnattendedAccount <string>] [-UsageDataRetentionPeriod <int>] [-UsageExpectedResponseUpperLimit <int>] [-UsageLongResponseUpperLimit <int>] [-UsageQuickResponseUpperLimit <int>] [-UsageTrivialResponseUpperLimit <int>] [-UsageUpdateDayLimit <int>] [<CommonParameters>]  
```  
  
## <a name="description"></a>Description  
 Set-PowerPivotServiceApplication コマンドレットは、ファーム内の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションのプロパティを更新します。 Identity パラメーターは必須です。 プロパティを更新するサービス アプリケーションの GUID を提供する必要があります。  
  
 変更内容を確認するには、次のコマンドレットを実行します。 Get-powerpivotserviceapplication-Identity \<GUID > | 形式の一覧です。  
  
## <a name="parameters"></a>パラメーター  
  
### <a name="-identity-spgeminiserviceapplicationpipebind"></a>Id \<SPGeminiServiceApplicationPipeBind >  
 更新するサービス アプリケーションを指定します。 有効な GUID または有効なのインスタンスを型として使用することがあります [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーション オブジェクトです。 Get-PowerPivotServiceApplication を使用して、オブジェクトのインスタンスを返すことができます。  
  
|||  
|-|-|  
|必須/省略可能|true|  
|位置|0|  
|既定値||  
|パイプライン入力の受け入れ|true|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-administrationconnectionpoolsize-int"></a>-Administrationconnectionpoolsize & \<int >  
 用に作成された接続プール内の開いている接続の数を指定する、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Analysis Services への接続にサービスを提供します。 各 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス インスタンスが同じコンピューター上の Analysis Services インスタンスに独立した管理接続を開きます。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービスでは、アイドル状態の接続を確認し、サーバーのヘルスを監視するために管理接続を再利用する、独立したプールを作成します。 接続数の既定値は 200 です。 有効値は、-1 (無制限)、0 (管理接続プールを無効にする)、または 1 ～ 10000 です。 0 を選択すると、すべての接続が新しく作成されます。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値|200|  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-allowcustomwindowscredentials-switchparameter"></a>-Allowcustomwindowscredentials [\<SwitchParameter >]  
 スケジュール所有者が任意の Windows 資格情報を入力して、データ更新スケジュールを実行できるかどうかを指定します。 このチェック ボックスを選択した場合 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションは作成され、保存された資格情報のセットごとに対象アプリケーションを管理します。 既定では、true に設定されています。 この機能をオフにするには、AllowCustomWindowsCredentials:$false を設定します。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-businesshoursendtime-string"></a>-Businesshoursendtime &\<文字列 >  
 営業日を定義する時間の範囲の終了点を指定します。 データ更新スケジュールを営業時間後に実行すると、通常の営業時間中に生成されたトランザクション データを取得できます。 既定値は午後 8:00 です。  有効な値は、引用符に囲んだ形で、午前または 午後の クロック時間で指定されます (たとえば、"08:00PM")。 時間は 1 から 12 までの範囲で指定する必要があります。 分は 1 から 59 までの範囲で指定する必要があります。  
  
 営業日の完全な時間の範囲を指定するには、BusinessHoursStartTime と BusinessHoursEndTime の両方を設定する必要があります。 2 つのパラメーターは、営業日を構成する時間の間隔を定義します。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値|8 PM|  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-businesshoursstarttime-string"></a>-Businesshoursstarttime &\<文字列 >  
 営業日を定義する時間の範囲の開始点を指定します。 データ更新スケジュールを営業時間後に実行すると、通常の営業時間中に生成されたトランザクション データを取得できます。 既定値は午前 4:00 です。  有効な値は、引用符に囲んだ形で、午前または 午後の クロック時間で指定されます (たとえば、"04:00AM")。 時間は 1 から 12 までの範囲で指定する必要があります。 分は 1 から 59 までの範囲で指定する必要があります。  
  
 営業日の完全な時間の範囲を指定するには、BusinessHoursStartTime と BusinessHoursEndTime の両方を設定する必要があります。 2 つのパラメーターは、営業日を構成する時間の間隔を定義します。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値|4 AM|  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-cacheddatabaseholdlimit-int"></a>-Cacheddatabaseholdlimit & \<int >  
 非アクティブなデータベースがメモリからアンロードされた後にファイル システム上に保持される時間を指定します。 既定では 120 時間です。 クリーンアップ ジョブでは、この設定を使用して、削除するファイルを特定します。 168 時間 (メモリ内で 48 時間、キャッシュ内で 120 時間) 非アクティブなすべての [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データベースは、クリーンアップ ジョブによってディスクから削除されます。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値|120|  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-confirm-switch"></a>確認\<スイッチ >  
 コマンドを実行する前に確認メッセージを表示します。 既定では、この値は有効にされています。 コマンドで確認応答を省略するには、コマンドで Confirm:$false を指定してください。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-connectionpoolsize-int"></a>-Connectionpoolsize & \<int >  
 アイドル状態の接続の最大数を指定する、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービスが、SharePoint ユーザーごとに個別の接続プールを作成する [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データセット、およびバージョンの組み合わせです。 既定値は 1000 です。 有効値は、-1 (無制限)、0 (ユーザー接続プールを無効にする)、または 1 ～ 10000 です。 これらの接続プールを使用すると、同じユーザーによる同じ読み取り専用データに対する継続的な接続を、サービスでより効率的にサポートできます。 接続プールを無効にすると、すべての接続が新しく作成されます。 接続プール サイズの制限を変更しても (値を 0 に設定した場合も)、接続が切断されることはありません。 接続プールは、データに接続するときの待ち時間を短縮するためのものです。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービスは、接続プールの設定に基づいて接続を拒否することはありません。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値|1000|  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-connectionpooltimeout-int"></a>-Connectionpooltimeout & \<int >  
 アイドルのデータ接続が開いたままになる分数を指定します。 既定値は 1800 秒 (30 分) です。 この期間に、同じ SharePoint ユーザーから同じ [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データに対する読み取り専用の要求が送られた場合、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションはアイドル状態のデータ接続を再利用します。 指定した期間にそのデータに対する要求がそれ以上受信されなかった場合は、接続がプールから削除されます。 有効値は 1 ～ 3600 秒です。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値|1800|  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-dataloadtimeout-int"></a>-Dataloadtimeout & \<int >  
 データの読み込み要求を転送した SQL Server Analysis Services ( [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ) インスタンスからの応答を[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]サービス アプリケーションが待機する時間を変更します。 非常に大規模なデータセットには、ネットワーク上で移動する時間がかかるための十分な時間を許可する必要があります、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Excel ブックを取得し、移動するサービス インスタンス、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] クエリ処理の Analysis Services インスタンスへのデータです。 既定値は 1800 秒 (30 分) です。 有効な値の範囲は 1 ～ 3600 秒です。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値|1800|  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-datarefreshfailurethreshold-int"></a>-Datarefreshfailurethreshold & \<int >  
 スケジュールが無効にされる前に連続するエラーの数を指定します。 既定値は、10 です。 更新のエラーのためにスケジュールを無効にしない場合は 0 を入力することもできます。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値|10|  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-datarefreshinactiveworkbooksthreshold-int"></a>-Datarefreshinactiveworkbooksthreshold & \<int >  
 スケジュールを無効にするデータ更新サイクルの数を指定します。「0」を入力すると、非アクティブでもスケジュールは無効になりません。 既定値は 10 サイクルです。  
  
 ブックは、複数のデータ更新サイクルにわたって接続イベントが存在しない場合に非アクティブであると評価されます。 データ更新サイクルは、データ更新操作の成功や失敗に関係なく、(スケジュールまたは [今すぐ実行] 操作によって) データ更新操作がトリガーされるたびにカウントされます。 ブックに対する接続要求がないままで一定のサイクル数 (既定では 10) を経過すると、非アクティブが原因でデータ更新スケジュールが無効になります。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値|10|  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-datarefreshmaxhistory-int"></a>-Datarefreshmaxhistory & \<int >  
 データの更新処理の履歴を保持する期間を指定します。 この情報は、データ更新を使用するブックごとに保持されるデータ更新の履歴ページに表示されます。 表示されます、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 管理ダッシュ ボード。 既定値は 365 日です。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値|365|  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-healthbasedallocation-switch"></a>-Healthbasedallocation &\<スイッチ >  
 使用可能な CPU またはメモリ リソースが最も多い [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint サーバーに接続要求を転送する、状態に応じた割り当てアルゴリズムを指定します。 これは、既定の割り当てアルゴリズムです。 HealthBasedAllocation と RoundRobinBasedAllocation は、相互に排他的です。 どちらか一方を指定する必要があります。 それらの両方を false に設定すると、HealthBasedAllocation が使用されます。これはデフォルトであるためです。 両方とも true に設定すると、検証エラーが発生します。 これらのパラメーターの構文には、パラメーター名のみを入力するか、parameter:$true または parameter:$false のように入力します。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-loadstoconnectionsratiocollectioninterval-int"></a>-Loadstoconnectionsratiocollectioninterval & \<int >  
 読み込み対接続の比率を計算するために、読み込みイベントおよび接続イベントをカウントする間隔 (時間) を指定します。 既定では、システムは 4 時間ごとに新しい比率を計算します。 有効値は 1 ～ 24 です。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値|4|  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-loadstoconnectionsratiolimit-int"></a>-Loadstoconnectionsratiolimit & \<int >  
 サーバーの正常性の指標として使用される、接続イベント上の読み込みイベントの比率を指定します。 既定値は 20% です。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値|20|  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-memorydatabaseholdlimit-int"></a>-Memorydatabaseholdlimit & \<int >  
 非アクティブなデータベースのデータに対する新しい要求を処理するために、そのデータベースをメモリ内に保持する時間を指定します。 アクティブなデータベースは、そのデータベースに対してクエリを実行している限り、メモリ内に常に保持されます。アクティブでなくなると、そのデータに対する要求が発生する場合に備えて、データベースはメモリ内に一定期間保持されます。 既定値は 48 時間です。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値|48|  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-queryreportinginterval-int"></a>-Queryreportinginterval & \<int >  
 使用状況イベントとして報告する前にクエリ応答の統計情報を収集する秒数を指定します。 既定では 300 秒です。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値|300|  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-roundrobinallocation-switch"></a>-Roundrobinallocation &\<スイッチ >  
 接続要求を転送するラウンド ロビン割り当てアルゴリズムを指定 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint サーバーの場合は、代替のサーバーの負荷に関係なく、使用可能なサーバー間で均等に要求します。 HealthBasedAllocation と RoundRobinBasedAllocation は、相互に排他的です。 どちらか一方を指定する必要があります。 それらの両方を false に設定すると、HealthBasedAllocation が使用されます。これはデフォルトであるためです。 両方とも true に設定すると、検証エラーが発生します。 これらのパラメーターの構文には、パラメーター名のみを入力するか、parameter:$true または parameter:$false のように入力します。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-unattendedaccount-string"></a>-Unattendedaccount &\<文字列 >  
 実行するための定義済みのアカウントを保存する Secure Store Service アプリケーションのターゲット アプリケーションの名前を示す [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データは、ジョブを更新します。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-usagedataretentionperiod-int"></a>-Usagedataretentionperiod & \<int >  
 使用状況データとサーバーの状態統計の履歴を保持する日数を指定します。 既定値は 365 日です。 この値を 0 に設定すると、すべての履歴を無期限に保持します。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値|365|  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-usageexpectedresponseupperlimit-int"></a>-Usageexpectedresponseupperlimit & \<int >  
 想定される要求と応答のやり取りが完了するまでの時間を定義する上限を設定します。 既定では 3000 ミリ秒です。 1000 ～ 3000 ミリ秒で完了する要求は、レポート目的では予期された応答と見なされます。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値|3000|  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-usagelongresponseupperlimit-int"></a>-Usagelongresponseupperlimit & \<int >  
 長い要求と応答のやり取りが完了するまでの時間を定義する上限を設定します。  上限値は 10000 ミリ秒です。 この上限を超えるすべての要求は、上限のしきい値がない超過カテゴリに分類されます。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値|10000|  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-usagequickresponseupperlimit-int"></a>-Usagequickresponseupperlimit & \<int >  
 迅速な要求と応答のやり取りが完了するまでの時間を定義する上限を設定します。 既定値は 1,000 ミリ秒です。 500 ～ 1000 ミリ秒で完了する要求は、レポート目的では迅速な応答と見なされます。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値|1000|  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-usagetrivialresponseupperlimit-int"></a>-Usagetrivialresponseupperlimit & \<int >  
 データ コレクション目的で、関連すると見なされるには短かすぎる応答時間のカテゴリを指定します。 このカテゴリに分類されるほとんどの応答は、サーバー間の通信です。 既定では、この値は 500 ミリ秒です。 0 ～ 500 ミリ秒で完了する要求は簡易要求であり、レポートでは無視されます。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値|500|  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-usageupdatedaylimit-int"></a>-Usageupdatedaylimit & \<int >  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 管理ダッシュボードのレポートによって使用されるデータ ファイルの更新エラーについて、警告をトリガーするしきい値 (日数) を指定します。 既定では、システムは使用状況データを毎日更新します。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 管理レポートのデータ ソースでは、管理ダッシュ ボード.xlsx ファイルは、同じスケジュールで更新します。 .xlsx ファイルが指定の日数を超えて更新されない場合は、ファイルが古くなったことを示す正常性ルールがトリガーされます。 既定値は 5 日です。 有効値は 1 ～ 30 です。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値|5|  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="commonparameters"></a>\<CommonParameters >  
 このコマンドレットは共通のパラメーターをサポートしています (Verbose、Debug、ErrorAction、ErrorVariable、WarningAction、WarningVariable、OutBuffer、および OutVariable)。 詳細については、「 [About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825)」を参照してください。  
  
## <a name="inputs-and-outputs"></a>入力および出力  
 入力型は、コマンドレットにパイプできるオブジェクトの型です。 戻り値の型は、コマンドレットが返すオブジェクトの型です。  
  
|||  
|-|-|  
|入力|[なし] :|  
|出力|[なし] :|  
  
## <a name="example-1"></a>例 1  
  
```  
C:\PS>Set-PowerPivotServiceApplication -identity 1234567-890a-bcde-fghijklm -AllowCustomWindowsCredentials:$false -UnattendedAccount "MyTargetApp"  
```  
  
 この例では、任意の Windows 資格情報を格納するために Secure Store Service 対象アプリケーションを自動的に作成および管理するデータ更新機能をオフにします。 また、設定、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 自動データ更新アカウントを定義済みの対象アプリケーションにします。  
  
 Get-powerpivotserviceapplication を使用して、有効な ID を取得します。  
  
## <a name="example-2"></a>例 2  
  
```  
C:\PS>Set-PowerPivotServiceApplication -identity 1234567-890a-bcde-fghijklm -HealthBasedAllocation  
```  
  
 この例では、使用可能なリソースが最も多いサーバーに接続要求を転送する、状態に応じた割り当てアルゴリズムを指定します。  
  
 Get-powerpivotserviceapplication を使用して、有効な ID を取得します。  
  
## <a name="example-3"></a>例 3  
  
```  
C:\PS>Set-PowerPivotServiceApplication -identity 1234567-890a-bcde-fghijklmn -BusinessHoursStartTime "07:15AM" -BusinessHoursEndTime "08:00PM"  
```  
  
 この例は、最初と最後のスケジュール設定のスケジュール オプションとして使用する、営業日の時間を設定する方法を示しています。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データ更新します。 スケジュールは、営業日の最後にデータ更新を実行するための営業時間後オプションを指定できます。  
  
 Get-powerpivotserviceapplication を使用して、有効な ID を取得します。  
  
  


---
title: managed_backup.fn_get_health_status (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fn_get_health_status_TSQL
- smart_admin.fn_get_health_status_TSQL
- smart_admin.fn_get_health_status
- fn_get_health_status
dev_langs:
- TSQL
helpviewer_keywords:
- smart_admin.fn_get_health_status
- fn_get_health_status
ms.assetid: b376711d-444a-4b5e-b483-8df323b4e31f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b921846b0fc27e59ff0874cdbf0827095bfc7db4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68140656"
---
# <a name="managedbackupfngethealthstatus-transact-sql"></a>managed_backup.fn_get_health_status (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  一定の時間を拡張イベントによって報告されたエラーの集計の数の 1 つまたは複数の行は 0、テーブルを返します。  
  
 関数を使用して、管理者がスマートでサービスの正常性状態を報告現在[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]Smart admin でサポートされています。 返されるエラーに関連するように[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]します。  
  
 
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```sql  
managed_backup.fn_get_health_status([@begin_time = ] 'time_1' , [ @end_time = ] 'time_2')  
```  
  
##  <a name="Arguments"></a> 引数  
 [@begin_time]  
 エラーの集計数を計算する期間の開始時刻。  @begin_timeパラメーター型は DATETIME です。 既定値は NULL です。 値が NULL の場合、この関数は現在の時刻の 30 分前に報告されたイベントから処理します。  
  
 [ @end_time]  
 エラーの集計数を計算する期間の終了時刻。 @end_timeパラメーターは DATETIME で、既定値は NULL です。 値が NULL の場合、この関数は現在の時刻まで、拡張イベントを処理します。  
  
## <a name="table-returned"></a>返されるテーブル  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|number_of_storage_connectivity_errors|ssNoversion|プログラムが Windows Azure ストレージ アカウントに接続するときに、接続エラーの数。|  
|number_of_sql_errors|ssNoversion|プログラムが SQL Server エンジンに接続するときに返されるエラーの数。|  
|number_of_invalid_credential_errors|ssNoversion|プログラムで SQL 資格情報を使用して認証を行うときに返されるエラーの数。|  
|number_of_other_errors|ssNoversion|接続、SQL、資格情報以外のカテゴリに関するエラーの数。|  
|number_of_corrupted_or_deleted_backups|ssNoversion|削除または破損したバックアップ ファイルの数。|  
|number_of_backup_loops|ssNoversion|バックアップ エージェントで構成されたすべてのデータベースがスキャン回数[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]します。|  
|number_of_retention_loops|ssNoversion|保有期間を評価するためにデータベースがスキャンされた回数。|  
  
## <a name="best-practices"></a>ベスト プラクティス  
 このような集計されたカウントは、システム正常性の監視に使用できます。 たとえば、だった of_retention_loops 列が 0 で 30 分の場合は、保有期間の管理が時間かかっているか、正常に動作しない可能性です。 については、問題の問題と拡張イベント ログを確認する必要がありますに 0 以外のエラー列がある可能性があります。 または、ストアド プロシージャを使用して**managed_backup.sp_get_backup_diagnostics**エラーの詳細を検索する Extended イベントの一覧を取得します。  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>アクセス許可  
 必要があります**選択**関数に対する権限。  
  
## <a name="examples"></a>使用例  
  
-   次の例では、関数を実行した時点の 30 分前から集計されたエラー数が返されます。  
  
    ```  
    SELECT *  
    FROM managed_backup.fn_get_health_status(NULL, NULL)  
  
    ```  
  
-   次の例では、集計されたエラーは、現在の週の数を返します。  
  
    ```  
    Use msdb  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
    SELECT *  
    FROM managed_backup.fn_get_health_status(@startofweek, @endofweek)  
  
    ```  
  
  

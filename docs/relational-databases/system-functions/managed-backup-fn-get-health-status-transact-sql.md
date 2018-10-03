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
manager: craigg
ms.openlocfilehash: 98ebc20d497165d4e2d80438bcd711490fd6bc8c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47799372"
---
# <a name="managedbackupfngethealthstatus-transact-sql"></a>managed_backup.fn_get_health_status (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  指定した期間の拡張イベントによって報告されたエラーの集計数に関する 0 行、1 行、または複数の行から成るテーブルを返します。  
  
 Smart Admin の下にあるサービスの正常性状態を報告するために、この関数が使用されます。現在、[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]は Smart Admin でサポートされています。 返されるエラーに関連するように[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]します。  
  
 
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```sql  
managed_backup.fn_get_health_status([@begin_time = ] 'time_1' , [ @end_time = ] 'time_2')  
```  
  
##  <a name="Arguments"></a> 引数  
 [@begin_time]  
 エラーの集計数を計算する期間の開始時刻。  @begin_timeパラメーター型は DATETIME です。 既定値は NULL になります。 値が NULL の場合、この関数は現在の時刻の 30 分前に報告されたイベントから処理します。  
  
 [ @end_time]  
 エラーの集計数を計算する期間の終了時刻。 @end_timeパラメーターは DATETIME で、既定値は NULL です。 値が NULL の場合、この関数は現在の時刻までの拡張イベントを処理します。  
  
## <a name="table-returned"></a>返されるテーブル  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|number_of_storage_connectivity_errors|ssNoversion|プログラムが Windows Azure ストレージ アカウントに接続したときの接続エラーの数。|  
|number_of_sql_errors|ssNoversion|プログラムが SQL Server エンジンに接続したときに返されたエラーの数。|  
|number_of_invalid_credential_errors|ssNoversion|プログラムが SQL 資格情報を使用して認証しようとしたときに返されたエラーの数。|  
|number_of_other_errors|ssNoversion|接続、SQL、資格情報以外のカテゴリに関するエラーの数。|  
|number_of_corrupted_or_deleted_backups|ssNoversion|削除されるか破損したバックアップ ファイルの数。|  
|number_of_backup_loops|ssNoversion|バックアップ エージェントで構成されたすべてのデータベースがスキャン回数[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]します。|  
|number_of_retention_loops|ssNoversion|保有期間を評価するためにデータベースがスキャンされた回数。|  
  
## <a name="best-practices"></a>ベスト プラクティス  
 このような集計されたカウントは、システム正常性の監視に使用できます。 たとえば、number_ of_retention_loops 列が 30 分間 0 だった場合、保有期間の管理に長時間がかかる可能性や保有期間の管理が正常に動作しない可能性があります。 エラー列が 0 以外の場合は問題を示す可能性があるため、拡張イベント ログで問題がないかどうかを確認する必要があります。 または、ストアド プロシージャを使用して**managed_backup.sp_get_backup_diagnostics**エラーの詳細を検索する Extended イベントの一覧を取得します。  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>アクセス許可  
 必要があります**選択**関数に対する権限。  
  
## <a name="examples"></a>使用例  
  
-   次の例では、関数を実行した時点の 30 分前から集計されたエラー数が返されます。  
  
    ```  
    SELECT *  
    FROM managed_backup.fn_get_health_status(NULL, NULL)  
  
    ```  
  
-   次の例では、現在の週について集計されたエラー数が返されます。  
  
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
  
  

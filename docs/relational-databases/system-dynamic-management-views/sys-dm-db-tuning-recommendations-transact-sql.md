---
title: dm_db_tuning_recommendations (Transact-sql) |Microsoft Docs
description: SQL Server と Azure SQL Database で、潜在的なパフォーマンスの問題と推奨される修正を見つける方法について説明します
ms.custom: ''
ms.date: 07/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_db_tuning_recommendations
- dm_db_tuning_recommendations
- sys.dm_db_tuning_recommendations_TSQL
- dm_db_tuning_recommendations_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- database tuning recommendations feature [SQL Server], sys.dm_db_tuning_recommendations dynamic management view
- sys.dm_db_tuning_recommendations dynamic management view
ms.assetid: ced484ae-7c17-4613-a3f9-6d8aba65a110
author: jovanpop-msft
ms.author: jovanpop
monikerRange: =azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: e8c18ce07ba5e36dcbdb5750db77edf17495c7b9
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81285513"
---
# <a name="sysdm_db_tuning_recommendations-transact-sql"></a>sys.dm\_db\_チューニング\_に関する推奨事項 (transact-sql)
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

  チューニングの推奨設定に関する詳細情報を返します。  
  
 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] では、動的管理ビューは、データベースの包含に影響する情報を公開することも、ユーザーがアクセスできる他のデータベースに関する情報を公開することもできません。 この情報を公開しないように、接続されたテナントに属していないデータを含むすべての行がフィルターで除外されます。

| **列名** | **データの種類** | **説明** |
| --- | --- | --- |
| **name** | **nvarchar (4000)** | 推奨事項の一意の名前。 |
| **type** | **nvarchar (4000)** | 推奨設定を生成した自動チューニングオプションの名前。たとえば、次のようになります。`FORCE_LAST_GOOD_PLAN` |
| **reason** | **nvarchar (4000)** | この推奨事項が提供された理由。 |
| **有効\_期限** | **datetime2** | この推奨事項が初めて生成されたとき。 |
| **最終\_更新** | **datetime2** | この推奨事項が最後に生成された時刻。 |
| **state** | **nvarchar (4000)** | 推奨事項の状態を説明する JSON ドキュメント。 次のフィールドを使用できます。<br />-   `currentValue`-推奨事項の現在の状態。<br />-   `reason`-推奨設定が現在の状態である理由を示す定数。|
| **実行\_可能\_なアクション** | **bit** | 1 = 推奨事項は、スクリプトを使用[!INCLUDE[tsql_md](../../includes/tsql-md.md)]してデータベースに対して実行できます。<br />0 = データベースに対して推奨設定を実行することはできません (例: 情報のみ、または推奨事項を元に戻します)。 |
| **is\_revertable\_action** | **bit** | 1 = 推奨事項は、データベースエンジンによって自動的に監視および元に戻すことができます。<br />0 = 推奨事項を自動的に監視して元に戻すことはできません。 ほとんど&quot;の&quot;実行可能な&quot;アクション&quot;は revertable になります。 |
| **実行\_アクション\_の\_開始時刻** | **datetime2** | 推奨事項が適用される日付。 |
| **アクション\_\_実行期間** | **time** | 実行アクションの期間。 |
| **実行\_アクション\_の\_開始者** | **nvarchar (4000)** | `User`= ユーザーは、推奨事項に手動で強制されたプランです。 <br /> `System`= システムに自動的に適用される推奨事項。 |
| **アクション\_\_の実行\_開始時刻** | **datetime2** | 推奨事項が適用された日付。 |
| **アクション\_\_の開始\_時刻を元に戻す** | **datetime2** | 推奨事項が元に戻された日付。 |
| **元\_に\_戻す操作の期間** | **time** | 元に戻す操作の期間。 |
| **元\_に\_戻す\_操作の開始** | **nvarchar (4000)** | `User`= ユーザー手動で強制されていない推奨プラン。 <br /> `System`= システムは自動的に推奨設定を戻しました。 |
| **アクション\_\_開始\_時刻を元に戻す** | **datetime2** | 推奨事項が元に戻された日付。 |
| **学生** | **int** | 0-100 スケールでのこの推奨事項の推定値/影響 (より優れたもの) |
| **住所** | **nvarchar(max)** | 推奨事項についての詳細が記載された JSON ドキュメント。 次のフィールドを使用できます。<br /><br />`planForceDetails`<br />-    `queryId`-低下した\_クエリのクエリ id。<br />-    `regressedPlanId`-低下したプランの plan_id。<br />-   `regressedPlanExecutionCount`-回帰が検出されるまでの低下した plan を使用したクエリの実行回数。<br />-    `regressedPlanAbortedCount`-低下したプランの実行中に検出されたエラーの数。<br />-    `regressedPlanCpuTimeAverage`-回帰が検出される前に低下したクエリによって消費される平均 CPU 時間 (マイクロ秒)。<br />-    `regressedPlanCpuTimeStddev`-回帰が検出される前に低下したクエリによって消費される CPU 時間の標準偏差。<br />-    `recommendedPlanId`-強制する計画の plan_id。<br />-   `recommendedPlanExecutionCount`-回帰が検出される前に強制される必要があるプランを持つクエリの実行回数。<br />-    `recommendedPlanAbortedCount`-プランの実行中に強制される必要がある検出されたエラーの数。<br />-    `recommendedPlanCpuTimeAverage`-強制的に実行する必要がある (回帰が検出される前に計算された) プランで実行されたクエリによって消費される平均 CPU 時間 (マイクロ秒)。<br />-    `recommendedPlanCpuTimeStddev`回帰が検出される前に低下したクエリによって消費される CPU 時間の標準偏差。<br /><br />`implementationDetails`<br />-  `method`-回帰を修正するために使用する必要があるメソッド。 値は常`TSql`にです。<br />-    `script` - [!INCLUDE[tsql_md](../../includes/tsql-md.md)]推奨されるプランを強制するために実行するスクリプト。 |
  
## <a name="remarks"></a>Remarks  
 によって`sys.dm_db_tuning_recommendations`返される情報は、データベースエンジンによってクエリパフォーマンスの潜在的な回帰が識別され、保存されない場合に更新されます。 推奨事項は、が[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]再起動されるまで保持されます。 サーバーの再利用後に保持する場合は、データベース管理者がチューニングの推奨設定のバックアップコピーを定期的に作成する必要があります。 

 `currentValue``state`列のフィールドには、次の値が含まれる場合があります。
 
 | Status | 説明 |
 |--------|-------------|
 | `Active` | 推奨事項はアクティブであり、まだ適用されていません。 ユーザーは推奨設定のスクリプトを取得し、手動で実行できます。 |
 | `Verifying` | 推奨事項はに[!INCLUDE[ssde_md](../../includes/ssde_md.md)]よって適用され、内部検証プロセスは、強制されたプランのパフォーマンスを低下したプランと比較します。 |
 | `Success` | 推奨事項が正常に適用されました。 |
 | `Reverted` | パフォーマンスを大幅に向上させることができないため、推奨事項は元に戻されます。 |
 | `Expired` | 推奨事項の有効期限が切れているため、もう適用できません。 |

[JSON ドキュメント`state`の列に含まれるのは、現在の状態の推奨事項である理由を示しています。 [理由] フィールドの値は次のようになります。 

| 原因 | 説明 |
|--------|-------------|
| `SchemaChanged` | 参照されるテーブルのスキーマが変更されたため、推奨設定の有効期限が切れました。 新しいスキーマで新しいクエリプランの回帰が検出されると、新しい推奨事項が作成されます。 |
| `StatisticsChanged`| 参照されるテーブルの統計が変更されたため、推奨設定の有効期限が切れました。 新しい統計に基づいて新しいクエリプランの回帰が検出されると、新しい推奨事項が作成されます。 |
| `ForcingFailed` | クエリで推奨されるプランを強制することはできません。 Query_store_plan ビュー `last_force_failure_reason`でを[sys.query_store_plan](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md)見つけて、エラーの原因を見つけます。 |
| `AutomaticTuningOptionDisabled` | `FORCE_LAST_GOOD_PLAN`オプションは、検証プロセス中にユーザーによって無効にされます。 ALTER `FORCE_LAST_GOOD_PLAN` database SET AUTOMATIC_TUNING 使用してオプションを有効にするか[&#40;transact-sql&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)ステートメントを使用するか、 `[details]` [スクリプトに含まれるスクリプト] 列を使用して手動でプランを強制してください。 |
| `UnsupportedStatementType` | クエリに対してプランを強制することはできません。 サポートされていないクエリ`INSERT BULK`の例としては、カーソルとステートメントがあります。 |
| `LastGoodPlanForced` | 推奨事項が正常に適用されました。 |
| `AutomaticTuningOptionNotEnabled`| [!INCLUDE[ssde_md](../../includes/ssde_md.md)]パフォーマンスが低下する可能性がある`FORCE_LAST_GOOD_PLAN`ことを確認しましたが、オプションが有効になっていません。 [ALTER database SET AUTOMATIC_TUNING &#40;transact-sql&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)を参照してください。 推奨設定を手動で`FORCE_LAST_GOOD_PLAN`適用するか、オプションを有効にします。 |
| `VerificationAborted`| 再起動またはクエリストアクリーンアップが原因で、検証プロセスが中止されました。 |
| `VerificationForcedQueryRecompile`| パフォーマンスが大幅に改善されないため、クエリが再コンパイルされます。 |
| `PlanForcedByUser`| ユーザーは[sp_query_store_force_plan &#40;transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-query-store-force-plan-transact-sql.md)プロシージャを使用して手動でプランを強制しています。 ユーザーが明示的に何らかのプランを強制する場合、データベースエンジンは推奨設定を適用しません。 |
| `PlanUnforcedByUser` | ユーザーは[sp_query_store_unforce_plan &#40;transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-query-store-unforce-plan-transact-sql.md)プロシージャを使用して、手動でプランを強制解除します。 ユーザーが明示的に推奨プランを元に戻したため、データベースエンジンは現在のプランをそのまま使用し、将来、何らかのプラン回帰が発生した場合に新しい推奨設定を生成します。 |

 [詳細] 列の統計情報には、ランタイムプランの統計情報 (現在の CPU 時間など) は表示されません。 推奨事項の詳細は、回帰の検出時に取得され[!INCLUDE[ssde_md](../../includes/ssde_md.md)] 、特定されたパフォーマンスの回帰の理由を説明します。 および`regressedPlanId`を`recommendedPlanId`使用して[クエリストアカタログビュー](../../relational-databases/performance/how-query-store-collects-data.md)に対してクエリを実行し、正確なランタイムプランの統計情報を検索します。

## <a name="examples-of-using-tuning-recommendations-information"></a>チューニングの推奨設定情報の使用例  

### <a name="example-1"></a>例 1
次の例では[!INCLUDE[tsql](../../includes/tsql-md.md)] 、特定のクエリに対して適切なプランを強制する、生成されたスクリプトを取得します。  
 
```sql
SELECT name, reason, score,
    JSON_VALUE(details, '$.implementationDetails.script') AS script,
    details.* 
FROM sys.dm_db_tuning_recommendations
CROSS APPLY OPENJSON(details, '$.planForceDetails')
    WITH (  [query_id] int '$.queryId',
            regressed_plan_id int '$.regressedPlanId',
            last_good_plan_id int '$.recommendedPlanId') AS details
WHERE JSON_VALUE(state, '$.currentValue') = 'Active';
```
### <a name="example-2"></a>例 2
次の例では[!INCLUDE[tsql](../../includes/tsql-md.md)] 、特定のクエリに対して適切なプランを強制する、生成されたスクリプトと、推定されるゲインに関する追加情報を取得します。

```sql
SELECT reason, score,
      script = JSON_VALUE(details, '$.implementationDetails.script'),
      planForceDetails.*,
      estimated_gain = (regressedPlanExecutionCount + recommendedPlanExecutionCount)
                  *(regressedPlanCpuTimeAverage - recommendedPlanCpuTimeAverage)/1000000,
      error_prone = IIF(regressedPlanErrorCount > recommendedPlanErrorCount, 'YES','NO')
FROM sys.dm_db_tuning_recommendations
CROSS APPLY OPENJSON (Details, '$.planForceDetails')
    WITH (  [query_id] int '$.queryId',
            regressedPlanId int '$.regressedPlanId',
            recommendedPlanId int '$.recommendedPlanId',
            regressedPlanErrorCount int,
            recommendedPlanErrorCount int,
            regressedPlanExecutionCount int,
            regressedPlanCpuTimeAverage float,
            recommendedPlanExecutionCount int,
            recommendedPlanCpuTimeAverage float
          ) AS planForceDetails;
```

### <a name="example-3"></a>例 3
次の例では[!INCLUDE[tsql](../../includes/tsql-md.md)] 、特定のクエリに対して適切なプランを強制する、生成されたスクリプトと、クエリストアに格納されているクエリテキストとクエリプランを含む追加情報を取得します。

```sql
WITH cte_db_tuning_recommendations
AS (SELECT reason,
        score,
        query_id,
        regressedPlanId,
        recommendedPlanId,
        current_state = JSON_VALUE(state, '$.currentValue'),
        current_state_reason = JSON_VALUE(state, '$.reason'),
        script = JSON_VALUE(details, '$.implementationDetails.script'),
        estimated_gain = (regressedPlanExecutionCount + recommendedPlanExecutionCount)
                * (regressedPlanCpuTimeAverage - recommendedPlanCpuTimeAverage)/1000000,
        error_prone = IIF(regressedPlanErrorCount > recommendedPlanErrorCount, 'YES','NO')
    FROM sys.dm_db_tuning_recommendations
    CROSS APPLY OPENJSON(Details, '$.planForceDetails')
    WITH ([query_id] int '$.queryId',
        regressedPlanId int '$.regressedPlanId',
        recommendedPlanId int '$.recommendedPlanId',
        regressedPlanErrorCount int,    
        recommendedPlanErrorCount int,
        regressedPlanExecutionCount int,
        regressedPlanCpuTimeAverage float,
        recommendedPlanExecutionCount int,
        recommendedPlanCpuTimeAverage float
        )
    )
SELECT qsq.query_id,
    qsqt.query_sql_text,
    dtr.*,
    CAST(rp.query_plan AS XML) AS RegressedPlan,
    CAST(sp.query_plan AS XML) AS SuggestedPlan
FROM cte_db_tuning_recommendations AS dtr
INNER JOIN sys.query_store_plan AS rp ON rp.query_id = dtr.query_id
    AND rp.plan_id = dtr.regressedPlanId
INNER JOIN sys.query_store_plan AS sp ON sp.query_id = dtr.query_id
    AND sp.plan_id = dtr.recommendedPlanId
INNER JOIN sys.query_store_query AS qsq ON qsq.query_id = rp.query_id
INNER JOIN sys.query_store_query_text AS qsqt ON qsqt.query_text_id = qsq.query_text_id;
```

推奨事項ビューの値のクエリに使用できる JSON 関数の詳細については、「」の[!INCLUDE[ssde_md](../../includes/ssde_md.md)]「 [json サポート](../../relational-databases/json/index.md)」を参照してください。
  
## <a name="permissions"></a>アクセス許可  

に`VIEW SERVER STATE`は[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]権限が必要です。   
で[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]は`VIEW DATABASE STATE` 、データベースに対する権限が必要です。   

## <a name="see-also"></a>参照  
 [自動チューニング](../../relational-databases/automatic-tuning/automatic-tuning.md)   
 [database_automatic_tuning_options &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-database-automatic-tuning-options-transact-sql.md)   
 [database_query_store_options &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [JSON サポート](../../relational-databases/json/index.md)
 

---
title: dm_db_tuning_recommendations (トランザクション-SQL) |マイクロソフトドキュメント
description: SQL Server および Azure SQL データベースで潜在的なパフォーマンスの問題と推奨される修正プログラムを見つける方法を確認する方法を学習します。
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285513"
---
# <a name="sysdm_db_tuning_recommendations-transact-sql"></a>db\_\_チューニング\_に関する推奨事項をsys.dmする (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

  チューニングの推奨事項に関する詳細情報を返します。  
  
 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] では、動的管理ビューは、データベースの包含に影響する情報を公開することも、ユーザーがアクセスできる他のデータベースに関する情報を公開することもできません。 この情報が公開されないようにするために、接続されたテナントに属していないデータを含むすべての行が除外されます。

| **列名** | **データ型** | **説明** |
| --- | --- | --- |
| **name** | **nvarchar(4000)** | 推奨の一意の名前。 |
| **type** | **nvarchar(4000)** | 推奨を生成した自動チューニング オプションの名前。`FORCE_LAST_GOOD_PLAN` |
| **reason** | **nvarchar(4000)** | この推奨事項が提供された理由。 |
| **の\_有効な** | **datetime2** | この推奨事項が初めて生成された。 |
| **前回\_の更新** | **datetime2** | この推奨事項が最後に生成された時刻。 |
| **状態** | **nvarchar(4000)** | 推奨事項の状態を記述する JSON ドキュメント。 以下のフィールドが使用可能です。<br />-   `currentValue`- 推奨事項の現在の状態。<br />-   `reason`- 推奨が現在の状態にある理由を記述する定数。|
| **は\_実行可能\_なアクションです** | **bit** | 1 = 推奨はスクリプトを介して[!INCLUDE[tsql_md](../../includes/tsql-md.md)]データベースに対して実行できます。<br />0 = データベースに対して推奨を実行することはできません (情報のみ、または推奨を元に戻した場合など)。 |
| **は\_元に\_戻す操作です** | **bit** | 1 = 推奨事項は、データベース エンジンによって自動的に監視および元に戻すことができます。<br />0 = 推奨事項を自動的に監視および元に戻すことはできません。 実行可能&quot;な&quot;操作のほとんどは、&quot;元に&quot;戻す必要があります。 |
| **実行\_アクション\_開始\_時刻** | **datetime2** | 推奨が適用された日付。 |
| **実行\_アクション\_期間** | **time** | 実行アクションの継続時間。 |
| **によって\_開始\_された\_実行アクション** | **nvarchar(4000)** | `User`= ユーザーは、推奨事項で手動で強制計画します。 <br /> `System`= システムが自動的に適用される推奨。 |
| **アクション\_\_の開始時刻\_を実行する** | **datetime2** | 推奨が適用された日付。 |
| **アクション\_\_開始時刻\_を元に戻す** | **datetime2** | 推奨事項が元に戻された日付。 |
| **アクション\_\_期間を元に戻す** | **time** | 元に戻す操作の期間。 |
| **によって\_開始\_されたアクション\_を元に戻す** | **nvarchar(4000)** | `User`= ユーザーが手動で強制されていない推奨プランです。 <br /> `System`= システムが自動的に推奨を元に戻しました。 |
| **アクション\_\_開始時刻を\_元に戻す** | **datetime2** | 推奨事項が元に戻された日付。 |
| **score** | **int** | 0~100 スケールでのこの推奨の推定値/影響量(大きいほど良い) |
| **詳細** | **nvarchar(max)** | 推奨事項の詳細を含む JSON ドキュメント。 以下のフィールドが使用可能です。<br /><br />`planForceDetails`<br />-    `queryId`-\_回帰クエリのクエリ ID。<br />-    `regressedPlanId`- 後退計画のplan_id。<br />-   `regressedPlanExecutionCount`- 回帰が検出されるまでの、回帰プランを使用したクエリの実行回数。<br />-    `regressedPlanAbortedCount`- 回帰計画の実行中に検出されたエラーの数。<br />-    `regressedPlanCpuTimeAverage`- 回帰が検出されるまでの、回帰クエリによって消費された平均 CPU 時間 (マイクロ秒単位)。<br />-    `regressedPlanCpuTimeStddev`- 回帰が検出される前に、回帰クエリによって消費された CPU 時間の標準偏差。<br />-    `recommendedPlanId`- 強制されるべき計画のplan_id。<br />-   `recommendedPlanExecutionCount`- 回帰が検出される前に強制的に実行するプランを使用したクエリの実行数。<br />-    `recommendedPlanAbortedCount`- プランの実行中に検出されたエラーのうち、強制する必要がある数。<br />-    `recommendedPlanCpuTimeAverage`- 強制するプランで実行されるクエリで消費される平均 CPU 時間 (マイクロ秒) (回帰が検出される前に計算されます)。<br />-    `recommendedPlanCpuTimeStddev`回帰が検出される前に、回帰クエリによって消費された CPU 時間の標準偏差。<br /><br />`implementationDetails`<br />-  `method`- 回帰を修正するために使用するメソッド。 値は常`TSql`にです。<br />-    `script` - [!INCLUDE[tsql_md](../../includes/tsql-md.md)]推奨プランを強制するために実行する必要があります。 |
  
## <a name="remarks"></a>解説  
 返される`sys.dm_db_tuning_recommendations`情報は、データベース エンジンがクエリ パフォーマンスの低下の可能性を特定したときに更新され、永続化されません。 推奨は再起動されるまで[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]保持されます。 データベース管理者は、サーバーのリサイクル後にチューニング推奨のバックアップ コピーを定期的に作成する必要があります。 

 `currentValue`列のフィールド`state`には、次の値が含まれます。
 
 | Status | 説明 |
 |--------|-------------|
 | `Active` | 推奨事項はアクティブで、まだ適用されていません。 ユーザーは、推奨スクリプトを受け取り、手動で実行できます。 |
 | `Verifying` | 勧告は、内部[!INCLUDE[ssde_md](../../includes/ssde_md.md)]検証プロセスによって適用され、強制プランのパフォーマンスと回帰計画とを比較します。 |
 | `Success` | 推奨事項が正常に適用されました。 |
 | `Reverted` | パフォーマンスが大幅に向上しないため、推奨は元に戻されます。 |
 | `Expired` | 推奨は期限切れになり、適用できなくなります。 |

列の`state`JSON ドキュメントには、現在の状態で推奨される理由を記述する理由が含まれています。 理由フィールドの値は次のようになります。 

| 理由 | 説明 |
|--------|-------------|
| `SchemaChanged` | 参照先テーブルのスキーマが変更されたため、推奨が期限切れになりました。 新しいスキーマで新しいクエリ プランの回帰が検出された場合、新しい推奨が作成されます。 |
| `StatisticsChanged`| 参照先テーブルの統計変更により、推奨期限が切れました。 新しい統計に基づいて新しいクエリ プラン回帰が検出された場合、新しい推奨が作成されます。 |
| `ForcingFailed` | 推奨プランをクエリに強制することはできません。 `last_force_failure_reason` [sys.query_store_plan](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md)ビューで、エラーの原因を見つけます。 |
| `AutomaticTuningOptionDisabled` | `FORCE_LAST_GOOD_PLAN`チェックプロセス中にユーザーが無効にします。 ALTER `FORCE_LAST_GOOD_PLAN` DATABASE SET を使用してオプション[を有効にAUTOMATIC_TUNING Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)ステートメント`[details]`&#40;するか、列のスクリプトを使用してプランを手動で強制します。 |
| `UnsupportedStatementType` | クエリに対してプランを強制することはできません。 サポートされていないクエリの例としては、カーソルと`INSERT BULK`ステートメントがあります。 |
| `LastGoodPlanForced` | 推奨事項が正常に適用されました。 |
| `AutomaticTuningOptionNotEnabled`| [!INCLUDE[ssde_md](../../includes/ssde_md.md)]潜在的なパフォーマンスの低下を特定`FORCE_LAST_GOOD_PLAN`しましたが、オプションが有効になっていない - [Transact-SQL&#41;&#40;ALTER DATABASE SET AUTOMATIC_TUNING](../../t-sql/statements/alter-database-transact-sql-set-options.md)を参照してください。 推奨事項を手動で適用`FORCE_LAST_GOOD_PLAN`するか、オプションを有効にします。 |
| `VerificationAborted`| 再起動またはクエリ ストアのクリーンアップにより、検証プロセスが中止されました。 |
| `VerificationForcedQueryRecompile`| パフォーマンスが大幅に向上しないため、クエリは再コンパイルされます。 |
| `PlanForcedByUser`| ユーザーは[、&#40;Transact-SQL&#41;プロシージャ sp_query_store_force_planを使用して、手動でプラン&#40;](../../relational-databases/system-stored-procedures/sp-query-store-force-plan-transact-sql.md)強制しました。 ユーザーが明示的に何らかの計画を強制することを決定した場合、データベース エンジンは推奨を適用しません。 |
| `PlanUnforcedByUser` | ユーザーは[、&#40;の Transact-SQL&#41;プロシージャ sp_query_store_unforce_planを使用して、手動でプラン&#40;強制的に](../../relational-databases/system-stored-procedures/sp-query-store-unforce-plan-transact-sql.md)実行解除します。 ユーザーが推奨プランを明示的に元に戻したので、データベース エンジンは現在の計画を使用し続け、将来計画の回帰が発生した場合に新しい推奨事項を生成します。 |

 詳細列の統計には、ランタイム・プランの統計 (現在の CPU 時間など) は表示されません。 推奨事項の詳細は、回帰検出時に取得され、特定された[!INCLUDE[ssde_md](../../includes/ssde_md.md)]パフォーマンス回帰の理由を説明します。 クエリ`regressedPlanId``recommendedPlanId`[ストアカタログ ビュー](../../relational-databases/performance/how-query-store-collects-data.md)を使用してクエリを実行し、正確なランタイム プランの統計情報を検索します。

## <a name="examples-of-using-tuning-recommendations-information"></a>チューニング推奨情報の使用例  

### <a name="example-1"></a>例 1
次の例は、[!INCLUDE[tsql](../../includes/tsql-md.md)]任意のクエリに対して良いプランを強制する生成されたスクリプトを取得します。  
 
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
次の例は、[!INCLUDE[tsql](../../includes/tsql-md.md)]任意のクエリに対して良いプランを強制する生成されたスクリプトと、推定ゲインに関する追加情報を取得します。

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
次の例では、[!INCLUDE[tsql](../../includes/tsql-md.md)]クエリ のクエリとクエリ ストアに格納されているクエリ プランを含む追加情報に対して、優れたプランを強制する生成されたスクリプトを取得します。

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

推奨事項ビューで値を照会するために使用できる JSON 関数の詳細については[、JSON サポート](../../relational-databases/json/index.md)([!INCLUDE[ssde_md](../../includes/ssde_md.md)]での) を参照してください。
  
## <a name="permissions"></a>アクセス許可  

に`VIEW SERVER STATE`アクセス許可[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]が必要です。   
での`VIEW DATABASE STATE`データベースの権限が必要[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。   

## <a name="see-also"></a>参照  
 [自動チューニング](../../relational-databases/automatic-tuning/automatic-tuning.md)   
 [&#40;のデータ&#41;を&#40;database_automatic_tuning_optionsします。](../../relational-databases/system-catalog-views/sys-database-automatic-tuning-options-transact-sql.md)   
 [トランザクションSQL&#41;&#40;sys.database_query_store_options](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [JSON サポート](../../relational-databases/json/index.md)
 

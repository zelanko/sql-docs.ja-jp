---
title: sys.dm_db_tuning_recommendations (TRANSACT-SQL) |Microsoft ドキュメント
description: 潜在的なパフォーマンスの問題を検出する方法について説明し、SQL Server と Azure SQL Database の修正を推奨
ms.custom: ''
ms.date: 07/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
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
caps.latest.revision: 37
author: jovanpop-msft
ms.author: jovanpop
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || >= sql-server-2017 || = sqlallproducts-allversions
ms.openlocfilehash: fc933666e31c45fc78fb6d303ca1e7d3b5874d55
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sysdmdbtuningrecommendations-transact-sql"></a>sys.dm\_db\_チューニング\_(TRANSACT-SQL) の推奨事項
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

  チューニングに関する推奨事項に関する詳細な情報を返します。  
  
 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]、動的管理ビューは、データベースの包含に影響を与えるまたはユーザーがアクセスを他のデータベースに関する情報が公開される情報を公開できません。 この情報が公開されないように、接続されたテナントに属していないデータを含む行はすべてフィルターで除外されます。

| **列名** | **データ型** | **Description** |
| --- | --- | --- |
| **name** | **nvarchar (4000)** | 推奨設定の一意の名前。 |
| **type** | **nvarchar (4000)** | たとえば、推奨を生成する自動チューニング オプションの名前 `FORCE_LAST_GOOD_PLAN` |
| **reason** | **nvarchar (4000)** | なぜこの推奨設定が指定された理由。 |
| **valid\_since** | **datetime2** | 初めてこの推奨設定が生成されました。 |
| **last\_refresh** | **datetime2** | この推奨設定が生成された最終時刻。 |
| **状態** | **nvarchar (4000)** | 推奨設定の状態を記述する JSON ドキュメントです。 次のフィールドを使用できます。<br />-   `currentValue` 推奨設定の現在の状態。<br />-   `reason` – 現在の状態で、推奨事項の理由を表現する定数。|
| **is\_executable\_action** | **bit** | 1 = を使用してデータベースに対して実行できる、推奨事項[!INCLUDE[tsql_md](../../includes/tsql_md.md)]スクリプト。<br />0 = データベースに対して、推奨事項を実行することはできません (例: についてのみ、または元に戻された推奨) |
| **\_revertable\_アクション** | **bit** | 1 = 推奨設定を自動的に監視およびデータベース エンジンによって元に戻します。<br />0 = 推奨設定を自動的に監視および元に戻すできることはできません。 ほとんど&quot;実行可能&quot;されるアクションが&quot;revertable&quot;です。 |
| **execute\_action\_start\_time** | **datetime2** | 推奨設定が適用された日付。 |
| **execute\_action\_duration** | **time** | Execute アクションは、の期間です。 |
| **execute\_action\_initiated\_by** | **nvarchar (4000)** | `User` = ユーザーは、手動で、推奨設定でプランを強制します。 <br /> `System` = システムは、推奨設定を自動的に適用されます。 |
| **execute\_action\_initiated\_time** | **datetime2** | 推奨設定が適用された日付。 |
| **元に戻す\_アクション\_開始\_時間** | **datetime2** | 推奨設定は元に戻さ日です。 |
| **元に戻す\_アクション\_期間** | **time** | 元に戻す操作の期間です。 |
| **revert\_action\_initiated\_by** | **nvarchar (4000)** | `User` = ユーザー unforced 手動で推奨される計画します。 <br /> `System` = システムには、推奨設定が自動的に戻されます。 |
| **元に戻す\_アクション\_開始\_時間** | **datetime2** | 推奨設定は元に戻さ日です。 |
| **score** | **int** | 0 ~ 100 でこの推奨事項に与える影響の値を推定スケール (が大きいほどパフォーマンスは向上) |
| **details** | **nvarchar(max)** | 詳細については、推奨設定を含む JSON ドキュメントです。 次のフィールドを使用できます。<br /><br />`planForceDetails`<br />-    `queryId` -クエリ\_後退したクエリの id。<br />-    `regressedPlanId` 機能低下したプランの plan_id します。<br />-   `regressedPlanExecutionCount` -、回帰の前に低下したプランとクエリの実行の数が検出されました。<br />-    `regressedPlanAbortedCount` 機能低下したプランの実行中に検出されたエラーの番号。<br />-    `regressedPlanCpuTimeAverage` -平均 CPU 時間が、回帰が検出される前に、後退したクエリで使用します。<br />-    `regressedPlanCpuTimeStddev` 標準偏差、回帰の前に低下したクエリで使用された CPU 時間が検出されました。<br />-    `recommendedPlanId` -plan_id プランを強制する必要があります。<br />-   `recommendedPlanExecutionCount`-、回帰が検出される前に強制するか、プランとクエリの実行回数。<br />-    `recommendedPlanAbortedCount` -強制するか、プランの実行中に検出されたエラーの数。<br />-    `recommendedPlanCpuTimeAverage` -平均 CPU 時間が、プランを強制する必要があります (、回帰が検出される前に計算) で実行されるクエリによって消費されています。<br />-    `recommendedPlanCpuTimeStddev` 回帰直線の前に低下したクエリで使用された CPU 時間の標準偏差が検出されました。<br /><br />`implementationDetails`<br />-  `method` メソッドを回帰の修正に使用する必要があります。 値は常に`TSql`です。<br />-    `script` - [!INCLUDE[tsql_md](../../includes/tsql_md.md)] 推奨されるプランを強制的に実行されるスクリプトです。 |
  
## <a name="remarks"></a>解説  
 によって返される情報`sys.dm_db_tuning_recommendations`データベース エンジンは、潜在的なクエリ パフォーマンスの低下を識別し、永続化されていないときに更新されます。 推奨設定が保持されますのみ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を再起動します。 データベース管理者は、サーバーの再利用後も保持する場合は、チューニングの推奨設定のバックアップ コピーを定期的に作成する必要があります。 

 `currentValue` フィールドに、`state`列は、次の値を持つ可能性があります。
 | [状態] | Description |
 |--------|-------------|
 | `Active` | アクティブで、まだ適用されていないをお勧めします。 ユーザーは、推奨設定スクリプトを実行し、それを手動で実行できます。 |
 | `Verifying` | 推奨設定が適用される[!INCLUDE[ssde_md](../../includes/ssde_md.md)]と内部の検証プロセスが低下したプランのプランのパフォーマンスを比較します。 |
 | `Success` | 推奨設定が正常に適用されます。 |
 | `Reverted` | パフォーマンスが著しく向上が存在しないために、推奨設定が戻されます。 |
 | `Expired` | 推奨事項は、有効期限が切れたし、今後は適用できません。 |

JSON ドキュメントで`state`列が理由は、現在の状態で、推奨事項を説明する理由が含まれています。 [理由] フィールドの値があります。 

| Reason | Description |
|--------|-------------|
| `SchemaChanged` | 参照先のテーブルのスキーマが変更されたために、推奨設定が期限切れです。 |
| `StatisticsChanged`| 参照先のテーブルの統計情報の変更により、推奨設定が期限切れです。 |
| `ForcingFailed` | 推奨されるプランをクエリに適用できません。 検索、`last_force_failure_reason`で、 [sys.query_store_plan](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md)失敗の理由を確認するビュー。 |
| `AutomaticTuningOptionDisabled` | `FORCE_LAST_GOOD_PLAN` オプションは、検証プロセス中に、ユーザーが無効です。 有効にする`FORCE_LAST_GOOD_PLAN`オプションを使用して[AUTOMATIC_TUNING 設定データベースの ALTER &#40;TRANSACT-SQL&#41; ](../../t-sql/statements/alter-database-transact-sql-set-options.md)ステートメントまたは強制的に、プラン内のスクリプトを使用して手動で`[details]`列です。 |
| `UnsupportedStatementType` | クエリにプランを適用できません。 サポートされていないクエリの例としては、カーソルと`INSERT BULK`ステートメントです。 |
| `LastGoodPlanForced` | 推奨設定が正常に適用されます。 |
| `AutomaticTuningOptionNotEnabled`| [!INCLUDE[ssde_md](../../includes/ssde_md.md)] 潜在的なパフォーマンスの低下を識別ですが、`FORCE_LAST_GOOD_PLAN`オプションが有効でない – 表示[AUTOMATIC_TUNING 設定データベースの ALTER &#40;TRANSACT-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)です。 推奨設定を手動で適用または有効にする`FORCE_LAST_GOOD_PLAN`オプション。 |
| `VerificationAborted`| 検証プロセスが再起動またはクエリのストアのクリーンアップにより中止されました。 |
| `VerificationForcedQueryRecompile`| 大幅なパフォーマンス向上がないために、クエリが再コンパイルされます。 |
| `PlanForcedByUser`| プランを使用して、ユーザーが手動で強制[sp_query_store_force_plan &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-query-store-force-plan-transact-sql.md)プロシージャです。 |
| `PlanUnforcedByUser` | プランを使用して、ユーザーが手動で現時点[sp_query_store_unforce_plan &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-query-store-unforce-plan-transact-sql.md)プロシージャです。 |

 [詳細] 列の統計では、プランのランタイム統計情報 (たとえば、現在の CPU 時間) は表示されません。 推奨事項の詳細が回帰の検出時に実行され、理由を説明[!INCLUDE[ssde_md](../../includes/ssde_md.md)]パフォーマンスの低下を識別します。 使用して`regressedPlanId`と`recommendedPlanId`クエリに[クエリ ストアのカタログ ビュー](../../relational-databases/performance/how-query-store-collects-data.md)計画の正確なランタイム統計情報が見つかりません。

## <a name="using-tuning-recommendations-information"></a>チューニング推奨設定の情報を使用します。  
 次のクエリを使用すると、問題を修正する T-SQL スクリプトを取得します。  
 
```
SELECT name, reason, score,
        JSON_VALUE(details, '$.implementationDetails.script') as script,
        details.* 
FROM sys.dm_db_tuning_recommendations
    CROSS APPLY OPENJSON(details, '$.planForceDetails')
                WITH (  query_id int '$.queryId',
                        regressed_plan_id int '$.regressedPlanId',
                        last_good_plan_id int '$.recommendedPlanId') as details
WHERE JSON_VALUE(state, '$.currentValue') = 'Active'
```
  
 推奨設定のビューでクエリの値に使用できる JSON 関数の詳細については、次を参照してください。[の JSON サポート](../../relational-databases/json/index.md)で[!INCLUDE[ssde_md](../../includes/ssde_md.md)]です。
  
## <a name="permissions"></a>権限  

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]が必要です`VIEW SERVER STATE`権限です。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]が必要です、`VIEW DATABASE STATE`データベースの権限です。   

## <a name="see-also"></a>参照  
 [自動調整](../../relational-databases/automatic-tuning/automatic-tuning.md)   
 [sys.database_automatic_tuning_options &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-automatic-tuning-options-transact-sql.md)   
 [sys.database_query_store_options &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [JSON のサポート](../../relational-databases/json/index.md)
 

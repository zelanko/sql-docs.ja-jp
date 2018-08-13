---
title: sys.dm_db_tuning_recommendations (TRANSACT-SQL) |Microsoft Docs
description: 潜在的なパフォーマンスの問題を検索する方法について説明し、SQL Server と Azure SQL Database での修正プログラムをお勧めします。
ms.custom: ''
ms.date: 07/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
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
monikerRange: =azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: f90bdf2966092f003e45b3bb6c8d80710875b59a
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39554252"
---
# <a name="sysdmdbtuningrecommendations-transact-sql"></a>sys.dm\_db\_チューニング\_(TRANSACT-SQL) の推奨事項
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

  チューニングの推奨事項に関する詳細な情報を返します。  
  
 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]、動的管理ビューは、データベースの包含に影響を与えるまたはユーザーがアクセスを他のデータベースに関する情報が公開される情報を公開できません。 この情報が公開されないように、接続されたテナントに属していないデータを含む行はすべてフィルターで除外されます。

| **列名** | **データ型** | **[説明]** |
| --- | --- | --- |
| **name** | **nvarchar (4000)** | 推奨設定の一意の名前。 |
| **type** | **nvarchar (4000)** | たとえば、推奨を生成した自動チューニング オプションの名前 `FORCE_LAST_GOOD_PLAN` |
| **reason** | **nvarchar (4000)** | なぜこの推奨事項が提供されている理由です。 |
| **valid\_since** | **datetime2** | 最初にこの推奨事項が生成されました。 |
| **last\_refresh** | **datetime2** | この推奨事項が生成された最後の時刻。 |
| **state** | **nvarchar (4000)** | 推奨事項の状態を記述する JSON ドキュメントです。 次のフィールドを使用できます。<br />-   `currentValue` -推奨事項の現在の状態。<br />-   `reason` -定数を推奨事項は、現在の状態の理由について説明します。|
| **is\_executable\_action** | **bit** | 1 = を使用してデータベースに対して実行できる推奨事項[!INCLUDE[tsql_md](../../includes/tsql_md.md)]スクリプト。<br />0 = データベースに対して、推奨事項を実行することはできません (例: についてのみ、または元に戻された推奨事項) |
| **\_revertable\_アクション** | **bit** | 1 = 推奨事項を自動的に監視し、データベース エンジンによって元に戻されます。<br />0 = 推奨事項を自動的に監視および元に戻すできることはできません。 ほとんど&quot;実行可能ファイル&quot;アクション&quot;revertable&quot;します。 |
| **execute\_action\_start\_time** | **datetime2** | 推奨事項の適用の日付。 |
| **execute\_action\_duration** | **time** | Execute アクションは、の期間です。 |
| **execute\_action\_initiated\_by** | **nvarchar (4000)** | `User` = ユーザーは、推奨設定でプランを手動で適用します。 <br /> `System` = システムは、推奨事項を自動的に適用されます。 |
| **execute\_action\_initiated\_time** | **datetime2** | 推奨事項が適用された日付。 |
| **元に戻す\_アクション\_開始\_時間** | **datetime2** | 日付は、推奨事項が元に戻されます。 |
| **元に戻す\_アクション\_期間** | **time** | 元に戻す操作の期間です。 |
| **revert\_action\_initiated\_by** | **nvarchar (4000)** | `User` = 推奨プランの手動で unforced ユーザー。 <br /> `System` = システムは、推奨事項を自動的に元に戻されます。 |
| **元に戻す\_アクション\_開始\_時間** | **datetime2** | 日付は、推奨事項が元に戻されます。 |
| **score** | **int** | この推奨事項では、0 ~ 100 の値または影響を推定スケール (が大きいほど良い) |
| **details** | **nvarchar(max)** | 推奨事項の詳細を含む JSON ドキュメントです。 次のフィールドを使用できます。<br /><br />`planForceDetails`<br />-    `queryId` -クエリ\_後退したクエリの id。<br />-    `regressedPlanId` -後退したプランの plan_id します。<br />-   `regressedPlanExecutionCount` -、回帰の前に、後退したプランとクエリの実行の数が検出されました。<br />-    `regressedPlanAbortedCount` -後退したプランの実行中にエラーが検出された数。<br />-    `regressedPlanCpuTimeAverage` -平均 CPU 時間が、回帰が検出される前に、後退したクエリで使用します。<br />-    `regressedPlanCpuTimeStddev` 標準偏差、回帰の前に、後退したクエリによって消費される CPU 時間が検出されました。<br />-    `recommendedPlanId` -plan_id プランを強制する必要があります。<br />-   `recommendedPlanExecutionCount`-プランの回帰が検出される前に強制する必要がありますを使用して、クエリの実行回数です。<br />-    `recommendedPlanAbortedCount` -適用する必要があるプランの実行中にエラーが検出された数。<br />-    `recommendedPlanCpuTimeAverage` -平均 CPU 時間を強制する必要があります (計算、回帰が検出される前に) プランで実行されるクエリによって消費されます。<br />-    `recommendedPlanCpuTimeStddev` 回帰直線の前に、後退したクエリで使用された CPU 時間の標準偏差が検出されました。<br /><br />`implementationDetails`<br />-  `method` -メソッド、回帰を修正するために使用する必要があります。 値は常に`TSql`します。<br />-    `script` - [!INCLUDE[tsql_md](../../includes/tsql_md.md)] 推奨されるプランを強制的に実行されるスクリプトです。 |
  
## <a name="remarks"></a>コメント  
 によって返される情報`sys.dm_db_tuning_recommendations`データベース エンジンは、潜在的なクエリ パフォーマンスの低下を識別し、永続化されていないときに更新されます。 推奨事項がまでのみ保持[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を再起動します。 データベース管理者は、サーバーの再利用後も保持する場合は、チューニング推奨設定のバックアップ コピーを定期的に作成する必要があります。 

 `currentValue` フィールドに、`state`列は、次の値がある可能性があります。
 | 状態 | 説明 |
 |--------|-------------|
 | `Active` | アクティブであり、まだ適用されていません。 お勧めします。 ユーザーは、推奨設定スクリプトを作成し、それを手動で実行できます。 |
 | `Verifying` | 推奨事項の適用によって[!INCLUDE[ssde_md](../../includes/ssde_md.md)]と内部の検証プロセスが機能低下したプランの強制プランのパフォーマンスを比較します。 |
 | `Success` | 推奨事項が正常に適用されます。 |
 | `Reverted` | パフォーマンスが著しく向上することがないために、推奨事項は元に戻します。 |
 | `Expired` | 推奨事項は、有効期限が切れたし、もはや適用することはできません。 |

JSON ドキュメント`state`列が現在の状態で、推奨事項である理由を説明する理由が含まれています。 [理由] フィールドの値は次のようになります。 

| Reason | 説明 |
|--------|-------------|
| `SchemaChanged` | 推奨事項には、参照先のテーブルのスキーマが変更されたため、有効期限が切れました。 |
| `StatisticsChanged`| 推奨事項は、参照先のテーブルで統計を変更したため有効期限が切れました。 |
| `ForcingFailed` | 推奨されるプランは、クエリに強制することはできません。 検索、`last_force_failure_reason`で、 [sys.query_store_plan](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md)失敗の理由を確認するビュー。 |
| `AutomaticTuningOptionDisabled` | `FORCE_LAST_GOOD_PLAN` オプションは、検証プロセス中に、ユーザーが無効です。 有効にする`FORCE_LAST_GOOD_PLAN`オプションを使用して[AUTOMATIC_TUNING 設定データベースの ALTER &#40;TRANSACT-SQL&#41; ](../../t-sql/statements/alter-database-transact-sql-set-options.md)ステートメントまたは強制的に、プラン内のスクリプトを使用して手動で`[details]`列。 |
| `UnsupportedStatementType` | クエリにプランを強制することはできません。 サポートされていないクエリの例は、カーソルと`INSERT BULK`ステートメント。 |
| `LastGoodPlanForced` | 推奨事項が正常に適用されます。 |
| `AutomaticTuningOptionNotEnabled`| [!INCLUDE[ssde_md](../../includes/ssde_md.md)] 潜在的なパフォーマンスの低下、識別されたが、`FORCE_LAST_GOOD_PLAN`オプションが有効になっていないを参照してください: [AUTOMATIC_TUNING 設定データベースの ALTER &#40;TRANSACT-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)。 推奨事項を手動で適用または有効にする`FORCE_LAST_GOOD_PLAN`オプション。 |
| `VerificationAborted`| 検証プロセスが再起動またはクエリ ストアのクリーンアップにより中止されました。 |
| `VerificationForcedQueryRecompile`| クエリは、大幅なパフォーマンス向上がないために再コンパイルされます。 |
| `PlanForcedByUser`| プランを使用して、ユーザーが手動で強制[sp_query_store_force_plan &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-query-store-force-plan-transact-sql.md)プロシージャ。 |
| `PlanUnforcedByUser` | プランを使用して、ユーザーが手動で動作[sp_query_store_unforce_plan &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-query-store-unforce-plan-transact-sql.md)プロシージャ。 |

 [詳細] 列の統計では、プランのランタイム統計情報 (たとえば、現在の CPU 時間) は表示されません。 推奨事項の詳細の回帰の検出時に行われ、理由について説明します[!INCLUDE[ssde_md](../../includes/ssde_md.md)]パフォーマンスの低下を識別します。 使用`regressedPlanId`と`recommendedPlanId`クエリに[クエリ ストアのカタログ ビュー](../../relational-databases/performance/how-query-store-collects-data.md)プランの正確なランタイム統計情報を検索します。

## <a name="using-tuning-recommendations-information"></a>チューニングの推奨事項の情報を使用してください。  
取得する次のクエリを使用することができます、[!INCLUDE[tsql](../../includes/tsql-md.md)]問題を解決するスクリプト。  
 
```sql
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
  
 推奨事項のビューでクエリの値に使用できる JSON 関数の詳細については、次を参照してください。[の JSON サポート](../../relational-databases/json/index.md)で[!INCLUDE[ssde_md](../../includes/ssde_md.md)]します。
  
## <a name="permissions"></a>アクセス許可  

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]、必要があります`VIEW SERVER STATE`権限。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]が必要です、`VIEW DATABASE STATE`データベースの権限。   

## <a name="see-also"></a>参照  
 [自動チューニング](../../relational-databases/automatic-tuning/automatic-tuning.md)   
 [sys.database_automatic_tuning_options &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-automatic-tuning-options-transact-sql.md)   
 [sys.database_query_store_options &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [JSON のサポート](../../relational-databases/json/index.md)
 

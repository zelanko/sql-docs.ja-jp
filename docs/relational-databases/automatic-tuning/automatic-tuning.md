---
title: "自動チューニング |Microsoft ドキュメント"
description: "SQL Server と Azure SQL データベースで自動チューニングについてください。"
ms.custom: 
ms.date: 08/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: automatic-tuning
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance tuning [SQL Server]
ms.assetid: 
caps.latest.revision: 
author: jovanpop-msft
ms.author: jovanpop
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 04d8ac47233e0556cd54ed9fb2b3d22080b4ee42
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2018
---
# <a name="automatic-tuning"></a>自動調整
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

  自動チューニングは、潜在的なクエリ パフォーマンスの問題に関する洞察を提供し、解決策を推奨して、特定された問題を自動的に解決するデータベース機能です。

自動チューニング[!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)]潜在的なパフォーマンスの問題が検出され、修正措置を適用することができます常に通知するかにより、[!INCLUDE[ssde_md](../../includes/ssde_md.md)]パフォーマンスの問題を自動的に修復します。
自動チューニング[!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)]特定し、によるパフォーマンスの問題を修正することができます**SQL プランの選択による後退**です。 自動チューニング[!INCLUDE[ssazure_md](../../includes/ssazure_md.md)]必要なインデックスを作成し、未使用のインデックスを削除します。

[!INCLUDE[ssde_md](../../includes/ssde_md.md)] データベースで実行され、自動的に、ワークロードのパフォーマンスを向上するクエリを監視します。 [!INCLUDE[ssde_md](../../includes/ssde_md.md)] 自動的に調整して、ワークロードにデータベースを動的に適応して、クエリのパフォーマンスを向上させることができますな組み込みのメカニズムがあります。 これには使用できる 2 つの自動調整機能があります。

 -  **計画の自動修正**(で利用可能な[!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)]と[!INCLUDE[ssazure_md](../../includes/ssazure_md.md)]) の問題のあるクエリ実行プランを識別して、SQL の修正プログラムは、パフォーマンスの問題を計画します。
 -  **自動インデックス管理**(でのみ使用可能な[!INCLUDE[ssazure_md](../../includes/ssazure_md.md)])、データベースに追加するインデックスとインデックスを削除するかを識別します。

## <a name="why-automatic-tuning"></a>なぜ自動チューニングですか?

重要なを識別する、ワークロードを監視している従来のデータベースの管理の主なタスクのいずれかの[!INCLUDE[tsql_md](../../includes/tsql_md.md)]クエリ、インデックスのパフォーマンスを向上させるために追加する必要がありますをほとんど使用されないインデックス。 [!INCLUDE[ssde_md](../../includes/ssde_md.md)] クエリおよび監視する必要のあるインデックスの詳細な洞察を提供します。 、データベースを常に監視データがハード面倒なタスクの多数のデータベースを処理する場合に特にです。 データベースの数が膨大を管理するは効率的に実行することでない可能性があります。 監視して、データベースを手動で調整、代わりに監視の一部を委任し、チューニングするアクションを検討する可能性があります[!INCLUDE[ssde_md](../../includes/ssde_md.md)]自動チューニング機能を使用します。

### <a name="how-does-automatic-tuning-works"></a>自動調整動作がどのようにしますか。

自動調整して、継続的な監視および分析プロセス常に、ワークロードの特性を学習するには、潜在的な問題と改善点を特定します。

![自動チューニング処理](./media/tuning-process.png)

このプロセスは、どのインデックスとプランがワークロードのパフォーマンスを向上させるし、どのようなインデックスが、ワークロードに影響を見つけることによって、ワークロードに動的に対応するデータベースを使用します。 この調査結果に基づいてと、ワークロードのパフォーマンスを改善するチューニングのアクションが適用されます自動チューニングします。 さらに、データベースでは、継続的に、ワークロードのパフォーマンスが向上することを確認する自動チューニングによって行われた変更を加えた後のパフォーマンスを監視します。 パフォーマンスが向上していないすべての操作は自動的に戻されます。 この検証プロセスは、自動チューニングすることによって行われた変更がワークロードのパフォーマンスを低下していないことを確認する主要機能です。

## <a name="automatic-plan-correction"></a>計画の自動修正

計画の自動修正が自動調整機能を識別する**SQL プランの選択による後退**し自動的に最後の既知の適切なプランを強制することで問題を修正します。

### <a name="what-is-sql-plan-choice-regression"></a>SQL プランの選択による後退とは何ですか。

[!INCLUDE[ssdenoversion_md](../../includes/ssdenoversion_md.md)] 別の SQL プランを使用して実行することがあります、[!INCLUDE[tsql_md](../../includes/tsql_md.md)]クエリ。 クエリ プランは、統計、インデックス、およびその他の要因によって異なります。 いくつかの実行に使用する最適なプラン[!INCLUDE[tsql_md](../../includes/tsql_md.md)]時間の経過と共にクエリを変更する可能性があります。 場合によっては、新しいプランを 1 つ前よりも高くできない可能性があり、新しいプラン パフォーマンスの低下が発生する可能性があります。

 ![SQL プランの選択による後退](media/plan-choice-regression.png "SQL プランの選択による後退") 

以前正常な計画し、force を使用する代わりに、現在 1 つを検索する必要があります、プランの選択による後退を確認するたびに`sp_query_store_force_plan`プロシージャです。
[!INCLUDE[ssde_md](../../includes/ssde_md.md)] [!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)]に関する情報が表示プラン機能低下した修正措置をお勧めします。
さらに、[!INCLUDE[ssde_md](../../includes/ssde_md.md)]を使用すると、このプロセスを自動化し、完全に[!INCLUDE[ssde_md](../../includes/ssde_md.md)]プランの変更に関連する検出されたすべての問題を修正します。

### <a name="automatic-plan-choice-correction"></a>自動プラン選択の修正

[!INCLUDE[ssde_md](../../includes/ssde_md.md)] プランの選択による後退が検出されるたびに、最後の既知の適切なプランに切り替える自動的にできます。

![SQL プラン選択の補正](media/force-last-good-plan.png "SQL プラン選択の修正") 

[!INCLUDE[ssde_md](../../includes/ssde_md.md)] どの潜在的なプランの選択による後退が正しくないプランではなく使用する計画を含むを自動的に検出します。
ときに、[!INCLUDE[ssde_md](../../includes/ssde_md.md)]最後に適用される既知の適切な計画を自動的に監視プランのパフォーマンスです。 新しいプランが強制されます強制プランが低下したプランよりも高くない場合は、および[!INCLUDE[ssde_md](../../includes/ssde_md.md)]新しいプランをコンパイルします。 場合[!INCLUDE[ssde_md](../../includes/ssde_md.md)]強制プランが低下したものよりも良い、強制プランが保持されます (たとえば、次の統計情報やスキーマの変更) 上に再コンパイルされるまで低下したプランよりもをお勧めすることを確認します。

### <a name="enabling-automatic-plan-choice-correction"></a>自動プラン選択の補正を有効にします。

データベースごとに自動調整を有効にし、プラン変更の機能低下が検出されたときは最後の正常なプランを適用することを指定できます。 自動調整は、次のコマンドを使って有効にします。

```   
ALTER DATABASE current
SET AUTOMATIC_TUNING ( FORCE_LAST_GOOD_PLAN = ON ); 
```
必ず、このオプションを後、[!INCLUDE[ssde_md](../../includes/ssde_md.md)]は自動推定の CPU 向上は 10 秒より高いまたは推奨される計画で、新しいプランでのエラーの数がエラーの数よりも高い位置には、推奨設定を強制していることを確認します強制プランが、現在のものよりも向上します。

### <a name="alternative---manual-plan-choice-correction"></a>代わりに、手動プラン選択の修正

自動調整しないときは、ユーザーが定期的にシステムを監視し、機能低下したクエリを検索する必要があります。 以前正常な計画し、現在 1 つを使用せずに強制的にユーザーを検索する任意のプランが低下した場合`sp_query_store_force_plan`プロシージャです。 ベスト プラクティスは、古いプランが統計またはインデックスの変更のために有効な可能性があるために、最後の既知の適切なプランを強制することです。 最後の既知の適切なプランを強制的ユーザーは、実行プランを強制的に使用されるクエリのパフォーマンスを監視し、そのプランが期待どおりに動作を確認する必要があります。 監視と分析の結果に応じてプランを強制するかまたはユーザーは、クエリを最適化するために他の何らかの方法を見つける必要があります。
手動で強制適用されたプランいない強制するか、forever ため、[!INCLUDE[ssde_md](../../includes/ssde_md.md)]最適なプランを適用できる必要があります。 ユーザーまたは DBA が最終的に強制プランを使用して、`sp_query_store_unforce_plan`され、let、[!INCLUDE[ssde_md](../../includes/ssde_md.md)]最適なプランを検索します。

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] すべての必要なビューとパフォーマンスを監視し、クエリのストア内の問題の解決に必要な手順を提供します。

[!INCLUDE[sssql15-md](../../includes/sssql15-md.md)]クエリのストアのシステム ビューを使用してプランの選択による後退を見つけることができます。 [!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)]、[!INCLUDE[ssde_md](../../includes/ssde_md.md)]を検出し、潜在的なプランの選択による後退と推奨される操作に適用されるを示しています、 [sys.dm_db_tuning_recommendations &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-db-tuning-recommendations-transact-sql.md)ビュー。 問題の重要性の問題と識別されたクエリ、後退したプランの ID、比較については、基準として使用されていたプランの ID などの詳細についての情報を表示し、[!INCLUDE[tsql_md](../../includes/tsql_md.md)]修正を実行できるステートメント、問題があります。

| 型 | description | datetime | score | 詳細情報 | … |
| --- | --- | --- | --- | --- | --- |
| `FORCE_LAST_GOOD_PLAN` | CPU 時間が 4 ms から 14 ミリ秒に変更されました | 3/17/2017 | 83 | `queryId` `recommendedPlanId` `regressedPlanId` `T-SQL` |   |
| `FORCE_LAST_GOOD_PLAN` | 37 ms から 84 ミリ秒に変更された CPU 時間 | 3/16/2017 | 26 | `queryId` `recommendedPlanId` `regressedPlanId` `T-SQL` |   |

この表示から一部の列は、次の一覧で説明します。
 - 種類は推奨される操作の`FORCE_LAST_GOOD_PLAN`します。
 - 説明情報を含む理由[!INCLUDE[ssde_md](../../includes/ssde_md.md)]このプランの変更が、潜在的なパフォーマンスの低下があると認識します。
 - 日時を設定すると、潜在的な回帰が検出されました。
 - この推奨事項のスコア付けします。 
 - 機能低下したプランを強制的に、問題を修正するプランの ID の ID、検出されたプランの ID などの問題に関する詳細[!INCLUDE[tsql_md](../../includes/tsql_md.md)]などの問題の修正を適用するスクリプト。詳細が格納されている[JSON 形式](../../relational-databases/json/index.md)です。

使用して、問題と、推定に関する追加情報を修正するスクリプトを入手する次のクエリが得られます。

```   
SELECT reason, score,
      script = JSON_VALUE(details, '$.implementationDetails.script'),
      planForceDetails.*,
      estimated_gain = (regressedPlanExecutionCount+recommendedPlanExecutionCount)
                  *(regressedPlanCpuTimeAverage-recommendedPlanCpuTimeAverage)/1000000,
      error_prone = IIF(regressedPlanErrorCount>recommendedPlanErrorCount, 'YES','NO')
FROM sys.dm_db_tuning_recommendations
  CROSS APPLY OPENJSON (Details, '$.planForceDetails')
    WITH (  [query_id] int '$.queryId',
            [current plan_id] int '$.regressedPlanId',
            [recommended plan_id] int '$.recommendedPlanId',

            regressedPlanErrorCount int,
            recommendedPlanErrorCount int,

            regressedPlanExecutionCount int,
            regressedPlanCpuTimeAverage float,
            recommendedPlanExecutionCount int,
            recommendedPlanCpuTimeAverage float

          ) as planForceDetails;
```

[!INCLUDE[ssresult-md](../../includes/ssresult-md.md)]     

| reason | score | スクリプト (script) | query\_id | current plan\_id | プランをお勧め\_id | 推定\_取得 | error\_prone
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 3 つの ms から 46 ミリ秒に変更された CPU 時間 | 36 | EXEC sp\_クエリ\_格納\_強制的\_プラン 12、17 です。 | 12 | 28 | 17 | 11.59 | 0

`estimated_gain` 現在のプランではなく、推奨されるプランが実行される場合を保存すると秒の推定数を表します。 ゲインが 10 秒より大きい場合、現在のプランではなく、推奨されるプランを強制するか。 ある場合 (たとえば、タイムアウトまたは中断された実行数) の多くのエラーよりも、現在のプランで、推奨される計画、列`error_prone`値に設定が`YES`です。 エラーが発生しやすいプランは、現在のものではなく、推奨されるプランを適用する理由別の理由です。

[!INCLUDE[ssde_md](../../includes/ssde_md.md)]プランの選択による後退以外の場合は継続的な監視とパフォーマンスの問題の修正を識別するために必要なすべての情報には、面倒な可能性がありますを提供します。 自動チューニングと、このプロセスがはるかに簡単になります。

## <a name="automatic-index-management"></a>自動インデックス管理

[!INCLUDE[ssazure_md](../../includes/ssazure_md.md)]、インデックス管理が容易なので[!INCLUDE[ssazure_md](../../includes/ssazure_md.md)]は、ワークロードについて学習し、データがインデックスは常に最適にすることを確認します。 適切なインデックスの設計は、ワークロードの最適なパフォーマンスを非常に重要にして、自動インデックス管理を使用して、インデックスを最適化できます。 自動インデックス管理いずれかが正しくないインデックス付きのデータベースでパフォーマンスの問題を修正または管理でき、既存のデータベース スキーマのインデックスを強化できます。 自動チューニング[!INCLUDE[ssazure_md](../../includes/ssazure_md.md)]は、次の操作を実行します。

 - テーブルからデータを読み取る T-SQL クエリのパフォーマンスが向上するインデックスを識別します。
 - 冗長なインデックスまたはインデックスを削除することがある時間の長い期間では使用されなかったを識別します。 不要なインデックスを削除すると、テーブル内のデータを更新するクエリのパフォーマンスが向上します。

### <a name="why-do-you-need-index-management"></a>インデックス管理が必要な理由

インデックスは、テーブルからデータを読み取るクエリの一部を高速化します。ただし、データを更新するクエリ速度が低下することができます。 インデックスを作成するときに、どのような列を慎重に分析する必要があります、インデックスに含める必要があります。 いくつかのインデックスは、しばらくしてから必要はありません。 したがってを定期的に特定し、任意のメリットをもたらすいないインデックスを削除する必要があります。 未使用のインデックスを無視する場合は何の利点もデータを読み取るクエリのデータを更新するクエリのパフォーマンスが減少します。 未使用のインデックスでは、追加の更新プログラムが不要なログが必要なため、システム全体のパフォーマンスも影響します。

テーブルからデータの読み取りし、更新プログラムの最小限の影響があるクエリのパフォーマンスを向上させるインデックスの最適なセットを検索すると、連続的かつ複雑な分析が必要があります。

[!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] 組み込みインテリジェンスを使用して、クエリを分析する高度なルールは、現在のワークロードに最適になるインデックスを識別し、インデックスを削除する可能性があります。 Azure SQL データベースにより、最小限必要なその他のクエリに影響を最小化されたデータを読み取るクエリの最適化がインデックスのセットを使用しています。

### <a name="automatic-index-management"></a>自動インデックス管理

検出、に加えて[!INCLUDE[ssazure_md](../../includes/ssazure_md.md)]識別された推奨事項を自動的に適用できます。 許可する場合もあります組み込みの規則が、データベースのパフォーマンスを向上する場合は、[!INCLUDE[ssazure_md](../../includes/ssazure_md.md)]インデックスを自動的に管理します。

Azure SQL データベースの自動調整を有効にし、自動調整機能が、ワークロードを完全に管理できるように、次を参照してください。 [Azure ポータルを使用して Azure SQL データベースの自動調整を有効に](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-automatic-tuning-enable)です。

ときに、 [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] CREATE INDEX や DROP INDEX の推奨設定を適用したインデックスの影響を受けるクエリのパフォーマンスを自動的に監視します。 影響を受けるクエリのパフォーマンスが向上する場合にのみ、新しいインデックスが保持されます。 インデックスがないのために実行速度が低下するいくつかのクエリがある場合、ドロップされたインデックスは自動的に再作成されます。

### <a name="automatic-index-management-considerations"></a>自動インデックス管理の考慮事項

必要なインデックスの作成に必要なアクション[!INCLUDE[ssazure_md](../../includes/ssazure_md.md)]リソースを消費し、一時的にワークロードのパフォーマンスに影響する可能性があります。 ワークロードのパフォーマンス上のインデックス作成の影響を最小限に抑えるには、Azure SQL データベースは、インデックスの管理操作の適切な時間枠を検索します。 データベースには十分なときに開始して延期されました。 データベースは、ワークロードを実行するリソースを必要とする場合は、チューニング操作、メンテナンス タスクを使用できる未使用のリソース。 自動インデックス管理の 1 つの重要な機能は、アクションの確認です。 Azure SQL データベースが作成するか、インデックスを削除すると、監視プロセスは、アクションが、パフォーマンスを向上することを確認するワークロードのパフォーマンスを分析します。 大幅に向上 – を導入していない場合は、アクションがすぐに戻ります。 これにより、Azure SQL データベースにより、自動アクション悪い影響を与えない、ワークロードのパフォーマンス。 自動チューニングによって作成されたインデックスは、基になるスキーマに対するメンテナンス操作に対して透過的です。 削除するか、列名の変更などスキーマの変更は自動的に作成されたインデックスの有無によってはブロックされません。 Azure SQL データベースで自動的に作成されるインデックスを削除時にすぐに関連するテーブルまたは列を削除します。

### <a name="alternative---manual-index-management"></a>代わりに、手動のインデックスの管理

自動インデックス管理なしユーザーが 手動でクエリを実行する必要があります[sys.dm_db_missing_index_details と #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-details-transact-sql.md)可能性がありますがパフォーマンスを向上させる、このビューで詳細情報を使用してインデックスを作成し、クエリのパフォーマンスを監視して手動でインデックスを検索するビュー。 削除するインデックスを検索するには、するために、ユーザーはほとんど使用されない検索インデックスにインデックスの運用上の使用状況の統計を監視する必要があります。

[!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] このプロセスを簡略化します。 [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] ワークロードを分析して、新しいインデックスを高速実行するクエリを識別し、使用されていないか、重複するインデックスを特定します。 詳細に変更する必要がありますのあるインデックスの id について[Azure ポータルで推奨インデックスを検索](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-advisor-portal)です。

## <a name="see-also"></a>参照  
 [ALTER DATABASE SET AUTOMATIC_TUNING &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [sys.database_automatic_tuning_options &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-database-automatic-tuning-options-transact-sql.md)  
 [sys.dm_db_tuning_recommendations &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-db-tuning-recommendations-transact-sql.md)   
 [sys.dm_db_missing_index_details と #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-details-transact-sql.md)   
 [sp_query_store_force_plan &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-query-store-force-plan-transact-sql.md)     
 [sp_query_store_unforce_plan &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-query-store-unforce-plan-transact-sql.md)           
 [sys.database_query_store_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [JSON 関数](../../relational-databases/json/index.md)

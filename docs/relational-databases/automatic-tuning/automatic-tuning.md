---
title: 自動チューニング |Microsoft Docs
description: SQL Server と Azure SQL Database での自動チューニングについて説明します。
ms.custom: ''
ms.date: 08/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- performance tuning [SQL Server]
ms.assetid: ''
author: jovanpop-msft
ms.author: jovanpop
monikerRange: =azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 365834e3c1cd239a245c1523947a359b7c2dcc57
ms.sourcegitcommit: 4baa8d3c13dd290068885aea914845ede58aa840
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/13/2020
ms.locfileid: "79289120"
---
# <a name="automatic-tuning"></a>自動チューニング
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

自動チューニングは、潜在的なクエリ パフォーマンスの問題に関する洞察を提供し、解決策を推奨して、特定された問題を自動的に解決するデータベース機能です。

の自動チューニング[!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)]では、潜在的なパフォーマンスの問題が検出されるたびに通知され、是正措置[!INCLUDE[ssde_md](../../includes/ssde_md.md)]を適用したり、パフォーマンスの問題を自動的に修正したりすることができます。
自動チューニングを[!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)]使用すると、**クエリ実行プランの選択の回帰**によって発生するパフォーマンスの問題を特定し、修正することができます。 また、自動[!INCLUDE[ssazure_md](../../includes/ssazure_md.md)]チューニングでは、必要なインデックスを作成し、未使用のインデックスを削除します。 クエリ実行プランの詳細については、「[実行プラン](../../relational-databases/performance/execution-plans.md)」を参照してください。

は[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 、データベースで実行されるクエリを監視し、ワークロードのパフォーマンスを自動的に向上させます。 に[!INCLUDE[ssde_md](../../includes/ssde_md.md)]は、データベースをワークロードに動的に適合させることによって、クエリのパフォーマンスを自動的に調整して向上させることができるインテリジェンスメカニズムが組み込まれています。 次の2つの自動チューニング機能を使用できます。

 -  **自動プラン修正**は、問題のあるクエリ実行プランを識別し、クエリ実行プランのパフォーマンスの問題を修正します。 **適用対象**:[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (開始値 [!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)]) および [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]
 -  **自動インデックス管理**では、データベースに追加する必要があるインデックスと、削除する必要があるインデックスが識別されます。 **適用対象**:[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]

## <a name="why-automatic-tuning"></a>自動チューニングを行う理由

従来のデータベース管理の主なタスクの3つは、ワークロードの[!INCLUDE[tsql_md](../../includes/tsql-md.md)]監視、重要なクエリの識別、パフォーマンス向上のために追加する必要があるインデックス、および使用頻度の低い識別を行うことです。 で[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]は、監視する必要があるクエリとインデックスについて詳細な洞察を得ることができます。 ただし、データベースを常に監視することは厄介で面倒なタスクであり、多数のデータベースを処理する場合は特にそうなります。 非常に多くのデータベースを管理することは、効率的に行うことができない場合があります。 データベースの監視とチューニングを手動で行うのではなく、監視とチューニングアクションの一部を、 [!INCLUDE[ssde_md](../../includes/ssde_md.md)]自動チューニング機能を使用してに委任することを検討してください。

### <a name="how-does-automatic-tuning-work"></a>自動チューニングのしくみ

自動チューニングは、継続的な監視と分析のプロセスであり、ワークロードの特性を常に把握し、潜在的な問題と改善点を特定します。

![自動チューニング プロセス](./media/tuning-process.png)

このプロセスにより、ワークロードのパフォーマンスを向上させる可能性のあるインデックスとプラン、およびワークロードに影響を与えるインデックスを見つけることによって、データベースをワークロードに動的に適合させることができます。 これらの検出結果に基づき、自動チューニングでは、ワークロードのパフォーマンスを向上させるチューニング アクションを適用します。 さらに、データベースは、自動チューニングによって行われた変更の後にパフォーマンスを継続的に監視して、ワークロードのパフォーマンスを向上させることができます。 パフォーマンスを向上させなかったアクションは、自動的に元に戻されます。 この検証プロセスは、自動チューニングによる変更がワークロードのパフォーマンスを低下させていないことを確認する主要機能です。

## <a name="automatic-plan-correction"></a>自動プラン修正

自動プラン修正は自動チューニング機能であり、**実行プランの選択の回帰**を識別し、前回正常起動時のプランを強制することによって自動的に問題を修正します。 クエリ実行プランとクエリオプティマイザーの詳細については、「[クエリ処理アーキテクチャガイド](../../relational-databases/query-processing-architecture-guide.md)」を参照してください。

### <a name="what-is-execution-plan-choice-regression"></a>実行プランの選択の回帰とは

で[!INCLUDE[ssdenoversion_md](../../includes/ssdenoversion_md.md)]は、さまざまな実行プランを使用[!INCLUDE[tsql_md](../../includes/tsql-md.md)]してクエリを実行できます。 クエリプランは、統計、インデックス、およびその他の要因によって異なります。 [!INCLUDE[tsql_md](../../includes/tsql-md.md)]クエリの実行に使用する最適なプランは、時間の経過と共に変更される可能性があります。 場合によっては、新しいプランが前のプランよりも優れているとは限りません。新しいプランでは、パフォーマンスの回帰が発生する可能性があります。

 ![クエリ実行プランの選択の回帰](media/plan-choice-regression.png "クエリ実行プランの選択の回帰") 

プランの選択に回帰がある場合は、以前の良好なプランを見つけて、現在のプランでは`sp_query_store_force_plan`なく、それを強制する必要があります。
[!INCLUDE[ssde_md](../../includes/ssde_md.md)]の[!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)]には、低下したプランと推奨される是正措置に関する情報が記載されています。
また、 [!INCLUDE[ssde_md](../../includes/ssde_md.md)]では、このプロセスを完全に自動化[!INCLUDE[ssde_md](../../includes/ssde_md.md)]し、プランの変更に関連する問題を修正することができます。

### <a name="automatic-plan-choice-correction"></a>自動プラン選択の修正

[!INCLUDE[ssde_md](../../includes/ssde_md.md)]プラン選択の回帰が検出されるたびに、最新の既知の正常なプランに自動的に切り替えることができます。

![クエリ実行プランの選択の修正](media/force-last-good-plan.png "クエリ実行プランの選択の修正") 

[!INCLUDE[ssde_md](../../includes/ssde_md.md)]は、不適切なプランの代わりに使用する必要があるプランを含め、プランの選択の可能性のある回帰を自動的に検出します。
が[!INCLUDE[ssde_md](../../includes/ssde_md.md)]最後の既知の正常なプランを適用すると、強制されたプランのパフォーマンスを自動的に監視します。 強制プランが低下したプランよりも適切でない場合、新しいプランは強制されず、 [!INCLUDE[ssde_md](../../includes/ssde_md.md)]は新しいプランをコンパイルします。 によっ[!INCLUDE[ssde_md](../../includes/ssde_md.md)]て強制されたプランが低下したプランよりも優れていることが確認された場合、再コンパイルが行われるまで (次の統計更新やスキーマの変更など)、強制プランは低下したプランよりも優れている場合に保持されます。

> [!NOTE]
> 自動的に強制された実行プランは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスの再起動の間は保持されません。

### <a name="enabling-automatic-plan-choice-correction"></a>自動プラン選択修正の有効化

データベースごとに自動調整を有効にし、プラン変更の機能低下が検出されたときは最後の正常なプランを適用することを指定できます。 自動調整は、次のコマンドを使って有効にします。

```sql   
ALTER DATABASE current
SET AUTOMATIC_TUNING ( FORCE_LAST_GOOD_PLAN = ON ); 
```

このオプションを有効にすると[!INCLUDE[ssde_md](../../includes/ssde_md.md)] 、では、推定 CPU 到達率が10秒を超える場合、または新しいプランのエラー数が推奨されるプランのエラー数よりも多い場合、によって自動的に推奨設定が強制されます。また、強制されたプランが現在のプランより優れていることを確認します。

### <a name="alternative---manual-plan-choice-correction"></a>代替 - 手動プラン選択修正

自動調整しないときは、ユーザーが定期的にシステムを監視し、機能低下したクエリを検索する必要があります。 いずれかのプランを低下したする場合は、ユーザーが以前の良好なプランを見つけて、 `sp_query_store_force_plan`現在のプランではなく強制的に実行する必要があります。 統計やインデックスの変更が原因で古いプランが無効になる可能性があるため、前回の既知の良好なプランを強制的に適用することをお勧めします。 前回正常起動時のプランを強制的に実行するユーザーは、強制プランを使用して実行されるクエリのパフォーマンスを監視し、強制されたプランが想定どおりに動作することを確認する必要があります。 監視と分析の結果に応じて、プランを強制するか、ユーザーがクエリを最適化する他の方法を見つける必要があります。
は最適なプランを適用できる必要があるため[!INCLUDE[ssde_md](../../includes/ssde_md.md)] 、手動で強制されたプランを強制的に強制しないようにする必要があります。 ユーザーまたは DBA は、最終的にはプロシージャを`sp_query_store_unforce_plan`使用してプランを[!INCLUDE[ssde_md](../../includes/ssde_md.md)]強制解除し、最適なプランを検索できるようにする必要があります。 

> [!TIP]
> または、[**強制されたプランを含むクエリ**クエリストア] ビューを使用して、プランを検索して強制しないようにします。

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クエリストアのパフォーマンスを監視し、問題を修正するために必要なすべてのビューと手順について説明します。

で[!INCLUDE[sssql15-md](../../includes/sssql15-md.md)]は、クエリストアシステムビューを使用して、プラン選択の回帰を見つけることができます。 で[!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)]は、 [!INCLUDE[ssde_md](../../includes/ssde_md.md)]によって、プランの選択による回帰が検出され、 [dm_db_tuning_recommendations &#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-tuning-recommendations-transact-sql.md)ビューで適用される推奨の操作が示されます。 ビューには、問題に関する情報、問題の重要度、および特定されたクエリ、低下したプランの ID、比較の基準として使用されたプランの ID、および問題を解決[!INCLUDE[tsql_md](../../includes/tsql-md.md)]するために実行できるステートメントなどの詳細が表示されます。

| type | description | DATETIME | スコア | details | ... |
| --- | --- | --- | --- | --- | --- |
| `FORCE_LAST_GOOD_PLAN` | CPU 時間が4ミリ秒から14ミリ秒に変更されました | 3/17/2017 | 83 | `queryId` `recommendedPlanId` `regressedPlanId` `T-SQL` |   |
| `FORCE_LAST_GOOD_PLAN` | CPU 時間が37ミリ秒から84ミリ秒に変更されました | 3/16/2017 | 26 | `queryId` `recommendedPlanId` `regressedPlanId` `T-SQL` |   |

このビューのいくつかの列について、次の一覧で説明します。
 - 推奨される操作の種類-`FORCE_LAST_GOOD_PLAN`
 - このプランの変更が[!INCLUDE[ssde_md](../../includes/ssde_md.md)]パフォーマンスの低下の可能性を示す情報を含む説明
 - 潜在的な回帰が検出された日時
 - この推奨事項のスコア
 - 検出されたプランの ID、低下したプランの id、問題を修正するために必要なプランの ID、 [!INCLUDE[tsql_md](../../includes/tsql-md.md)]問題を修正するために適用される可能性のあるスクリプトなどの問題について詳しく説明します。詳細は[JSON 形式](../../relational-databases/json/index.md)で格納されます

次のクエリを使用して、問題を修正するスクリプトと、推定されるゲインに関する追加情報を取得します。

```sql   
SELECT reason, score,
      script = JSON_VALUE(details, '$.implementationDetails.script'),
      planForceDetails.*,
      estimated_gain = (regressedPlanExecutionCount + recommendedPlanExecutionCount)
                  * (regressedPlanCpuTimeAverage - recommendedPlanCpuTimeAverage)/1000000,
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

[!INCLUDE[ssresult-md](../../includes/ssresult-md.md)]     

| reason | スコア | script | クエリ\_id | 現在の\_プラン id | 推奨さ\_れるプラン id | 推定\_ゲイン | エラー\_が発生しやすい
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| CPU 時間が3ミリ秒から46ミリ秒に変更されました | 36 | EXEC sp\_クエリ\_ストア\_force\_プラン 12, 17; | 12 | 28 | 17 | 11.59 | 0

`estimated_gain`現在のプランの代わりに推奨プランを実行する場合に保存される推定秒数を表します。 ゲインが10秒を超える場合は、現在のプランではなく、推奨されるプランを強制する必要があります。 現在のプランで、推奨されるプランよりも多くのエラー (タイムアウトや中断された実行など) が発生した`error_prone`場合、列は値`YES`に設定されます。 エラーが発生しやすい計画は、現在のプランではなく、推奨プランを強制する必要があるもう1つの理由です。

[!INCLUDE[ssde_md](../../includes/ssde_md.md)]は、プランの選択の回帰を識別するために必要なすべての情報を提供します。継続的な監視とパフォーマンスの問題の修正は、面倒なプロセスである可能性があります。 自動チューニングでは、このプロセスがはるかに簡単になります。

> [!NOTE]
> Dm_db_tuning_recommendations DMV のデータは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスの再起動の間は保持されません。

## <a name="automatic-index-management"></a>インデックスの自動管理

で[!INCLUDE[ssazure_md](../../includes/ssazure_md.md)]は、ワークロードについ[!INCLUDE[ssazure_md](../../includes/ssazure_md.md)]て学習し、常に最適なインデックスを作成することにより、インデックスの管理が簡単になります。 適切なインデックスの設計は、ワークロードの最適なパフォーマンスにとって不可欠であり、インデックスの自動管理はインデックスを最適化するのに役立ちます。 インデックスの自動管理では、正しくインデックスが付けられていないデータベースでのパフォーマンスの問題を修正することも、既存のデータベース スキーマのインデックスを維持および改善することもできます。 での自動[!INCLUDE[ssazure_md](../../includes/ssazure_md.md)]チューニングでは、次のアクションが実行されます。

 - テーブルからデータを読み取る[!INCLUDE[tsql_md](../../includes/tsql-md.md)]クエリのパフォーマンスを向上させることができるインデックスを識別します。
 - 削除される可能性のある長い期間内に使用されなかった冗長なインデックスまたはインデックスを識別します。 不要なインデックスを削除すると、テーブル内のデータを更新するクエリのパフォーマンスが向上します。

### <a name="why-do-you-need-index-management"></a>インデックスの管理が必要な理由

インデックスはテーブルからデータを読み取るクエリの一部を高速化しますが、データを更新するクエリの速度が低下する場合があります。 インデックスを作成するタイミングと、インデックスに含める必要がある列を慎重に分析する必要があります。 一部のインデックスはしばらくすると必要でなくなる場合があります。 したがって、利点が得られないインデックスを定期的に識別して削除する必要があります。 未使用のインデックスを無視すると、データを読み取るクエリの利点が得られず、データを更新するクエリのパフォーマンスが低下します。 また、未使用のインデックスはシステムの全体のパフォーマンスに影響します。これは、追加の更新に不要なログが必要になるためです。

テーブルからデータを読み取るクエリのパフォーマンスを向上させ、更新への影響を最小限に抑える最適なインデックスのセットを見つけるには、継続的で複雑な分析が必要になる場合があります。

[!INCLUDE[ssazure_md](../../includes/ssazure_md.md)]では、クエリを分析し、現在のワークロードに最適なインデックスを識別する組み込みのインテリジェンスおよび高度なルールが使用され、インデックスが削除される可能性があります。 Azure SQL Database は、データを読み取るクエリを最適化する必要最小限のインデックス セットがあり、他のクエリへの影響が最小限に抑えられていることを確認します。

### <a name="automatic-index-management"></a>インデックスの自動管理

検出に加え、で[!INCLUDE[ssazure_md](../../includes/ssazure_md.md)]は、特定された推奨事項を自動的に適用することができます。 組み込みのルールによってデータベースのパフォーマンスが向上する場合は、インデックスを[!INCLUDE[ssazure_md](../../includes/ssazure_md.md)]自動的に管理することができます。

で[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]自動チューニングを有効にし、自動チューニング機能でワークロードを完全に管理できるようにするには、「 [Azure portal を使用した Azure SQL Database での自動チューニングの有効化](/azure/sql-database/sql-database-automatic-tuning-enable)」を参照してください。

が[!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] CREATE index または DROP INDEX 推奨設定を適用すると、インデックスの影響を受けるクエリのパフォーマンスが自動的に監視されます。 影響を受けるクエリのパフォーマンスが向上した場合にのみ、新しいインデックスが保持されます。 インデックスが存在しないために実行速度が遅いクエリがある場合、削除されたインデックスは自動的に再作成されます。

### <a name="automatic-index-management-considerations"></a>インデックスの自動管理に関する考慮事項

で必要なインデックスを作成する[!INCLUDE[ssazure_md](../../includes/ssazure_md.md)]ために必要な操作は、リソースを消費する可能性があり、ワークロードのパフォーマンスに影響を一時的にます。 インデックスの作成によるワークロードのパフォーマンスへの[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]影響を最小限に抑えるため、では、任意のインデックス管理操作に適した時間枠が検索されます。 チューニング アクションは、データベースでワークロードを実行するためのリソースが必要な場合は延期され、メンテナンス タスクに使用できる十分な未使用のリソースがデータベースにあるときは開始されます。 インデックスの自動管理の 1 つの重要な機能は、アクションの検証です。 が[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]インデックスを作成または削除すると、監視プロセスによってワークロードのパフォーマンスが分析され、アクションによってパフォーマンスが向上したことが確認されます。 大幅な改善が行われなかった場合は、すぐに操作が元に戻されます。 これにより[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] 、自動アクションがワークロードのパフォーマンスに悪影響を与えないようにします。 自動チューニングによって作成されたインデックスは、基になるスキーマでのメンテナンス操作に対して透過的です。 自動的に作成されたインデックスがあることで、列の削除や名前変更などのスキーマ変更がブロックされることはありません。 によって[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]自動的に作成されたインデックスは、関連するテーブルまたは列が削除されるとすぐに削除されます。

### <a name="alternative---manual-index-management"></a>代替-手動によるインデックス管理

自動インデックス管理を使用しない場合、ユーザーは、Transact-sql&#41;ビューに手動でクエリを実行するか、で[!INCLUDE[ssManStudio](../../includes/ssManStudio-md.md)]パフォーマンスダッシュボードレポートを使用して、パフォーマンスを向上させる可能性のあるインデックスを検索し、このビューに示されている詳細を使用してインデックスを作成し、クエリのパフォーマンスを手動で監視する必要があり[ます &#40;dm_db_missing_index_details。](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-details-transact-sql.md) 削除する必要があるインデックスを見つけるために、ユーザーはインデックスの操作の使用状況の統計を監視して、使用頻度の低いインデックスを検索する必要があります。

[!INCLUDE[ssazure_md](../../includes/ssazure_md.md)]このプロセスを簡略化します。 [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)]ワークロードを分析し、新しいインデックスを使用してより高速に実行できるクエリを識別し、未使用または重複したインデックスを識別します。 変更する必要があるインデックスの識別の詳細については、「[Azure Portal を使用した SQL Database Advisor](https://docs.microsoft.com/azure/sql-database/sql-database-advisor-portal)」参照してください。

## <a name="see-also"></a>参照  
 [ALTER DATABASE SET AUTOMATIC_TUNING &#40;Transact-sql&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [database_automatic_tuning_options &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-database-automatic-tuning-options-transact-sql.md)  
 [dm_db_tuning_recommendations &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-tuning-recommendations-transact-sql.md)   
 [dm_db_missing_index_details &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-details-transact-sql.md)   
 [sp_query_store_force_plan &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-query-store-force-plan-transact-sql.md)     
 [sp_query_store_unforce_plan &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-query-store-unforce-plan-transact-sql.md)           
 [database_query_store_options &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [JSON 関数](../../relational-databases/json/index.md)    
 [実行プラン](../../relational-databases/performance/execution-plans.md)    
 [パフォーマンスの監視とチューニング](../../relational-databases/performance/monitor-and-tune-for-performance.md)     
 [パフォーマンス監視およびチューニング ツール](../../relational-databases/performance/performance-monitoring-and-tuning-tools.md)     
 [クエリストアを使用したパフォーマンスの監視](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)  
 [クエリ調整アシスタント](../../relational-databases/performance/upgrade-dbcompat-using-qta.md)

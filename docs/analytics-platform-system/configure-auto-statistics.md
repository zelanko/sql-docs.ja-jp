---
title: 自動統計 (Analytics Platform System)
description: 分析プラットフォーム システム AU7 で導入された自動統計機能をについて説明します。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/24/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 1c0f4623adad35ab874330b42aa54f6e1b91d961
ms.sourcegitcommit: fc3cd23685c6b9b6972d6a7bab2cc2fc5ebab5f2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/25/2018
---
# <a name="configure-auto-statistics"></a>統計の自動構成します。

作成と統計情報を自動的に更新する統計の自動を使用する並列データ ウェアハウスを構成する方法を説明します。  クエリ プランを向上させるためにこの機能を使用して、クエリのパフォーマンス向上します。

**適用されます:** APS (AU7 以降)

## <a name="what-are-statistics"></a>統計情報とは
クエリ最適化に関する統計は、テーブルの 1 つまたは複数の列の値の分布に関する統計情報を含むオブジェクトです。 クエリ オプティマイザーの基数を推定するこれらの統計情報を使用すると、クエリ内の行の数になります。 これらの基数の推定には、高品質のクエリ プランを作成するクエリ オプティマイザーが有効にします。 例として、AP では、MPP クエリ オプティマイザーで使用して基数の推定値をランダム再生またはこれと join 句で使用する 2 つのテーブルのうち、小さい方をレプリケートするかを選択は、クエリのパフォーマンスを向上します。  詳細については、次を参照してください[統計](../relational-databases/statistics/statistics.md)と[DBCC show_statistics で。](../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)

## <a name="what-are-auto-statistics"></a>統計の自動とは
統計の自動クエリ オプティマイザーを作成し、クエリ プランを向上させるために自動的に更新する統計はありません。 統計が古くなる可能性の読み込み後に挿入、更新し、操作を削除します。 自動統計のないのどの列には、統計情報が必要があるし、統計を更新する必要がある場合を確認して、独自の分析を実行する必要があります。

統計の自動 には、次の 3 つの設定が含まれています。 

### <a name="autocreatestatistics"></a>AUTO_CREATE_STATISTICS
自動統計の作成オプション AUTO_CREATE_STATISTICS は ON です、クエリ オプティマイザーがクエリ プランの基数の推定を向上させるために、必要に応じて、クエリ述語内の個々 の列に関する統計を作成します。 これらの 1 列ずつの統計は、既存の統計オブジェクトにまだヒストグラムがない列について作成されます。

### <a name="autoupdatestatistics"></a>AUTO_UPDATE_STATISTICS 
統計の自動更新オプション AUTO_UPDATE_STATISTICS がオンの場合、古くなっている可能性がある統計がクエリ オプティマイザーによって判断され、それらがクエリで使用されると更新されます。 古くなった操作が挿入、更新、削除、またはマージの統計情報は、テーブルのデータ分布が変わるまたはインデックス付きビュー。 クエリ オプティマイザーでは、統計が前回更新されてから発生したデータ変更の数をカウントし、その変更の数をしきい値と比較することで、統計が古くなっている可能性がないかを判断します。 このしきい値は、テーブルまたはインデックス付きビューの行数に基づいて決められます。

### <a name="autoupdatestatisticsasync"></a>AUTO_UPDATE_STATISTICS_ASYNC
統計の非同期更新オプション AUTO_UPDATE_STATISTICS_ASYNC によって、クエリ オプティマイザーで統計の同期更新と非同期更新のどちらを使用するかが決まります。 Ap、統計の非同期更新オプションは、既定で ON と、クエリ オプティマイザーが統計情報を非同期的に更新します。 AUTO_UPDATE_STATISTICS_ASYNC オプションは、インデックス、クエリ述語、および CREATE STATISTICS ステートメントを使用して作成された統計内の 1 つの列に対して作成された統計オブジェクトに適用されます。

## <a name="configuration-settings-for-system-administrators"></a>システム管理者の構成設定
APS AU7 にアップグレードすると、統計の自動は既定で有効にします。 システム管理者を有効または無効で統計の自動、[機能スイッチ](appliance-feature-switch.md)アプライアンス Configuration Manager でのオプションです。  有効にすると、ユーザーは、データベースごとの統計情報の設定を変更できます。
機能スイッチ値を変更するには、AP 上のサービスの再起動が必要です。

## <a name="change-auto-statistics-settings-on-a-database"></a>データベースの自動統計設定を変更します。
自動統計は、システム管理者によって有効になっている、ときに行うこともできます[ALTER DATABASE (並列データ ウェアハウス)](/sql/t-sql/statements/alter-database-parallel-data-warehouse)データベースで統計情報設定を変更します。 自動統計機能スイッチが有効な場合、システム管理者によって、AU7 へのアップグレード後に作成されたすべての新しいデータベースは有効になっている自動統計情報があります。 AU7 へのアップグレード前に、から存在するすべてのデータベースでは、無効になっている自動統計情報があります。 次の例では、既存のデータベース myPDW の自動統計を有効します。

```sql
ALTER DATABASE myPDW SET AUTO_CREATE_STATISTICS ON
ALTER DATABASE myPDW SET AUTO_UPDATE_STATISTICS ON 
ALTER DATABASE myPDW SET AUTO_UPDATE_STATISTICS_ASYNC ON
```
 
AUTO_UPDATE STATISTICS_ASYNC のオプションは、AUTO_UPDATE_STATISTICS が ON の場合にのみ機能します。  したがって、統計が更新されない AUTO_UPDATE_STATISTICS は OFF ですし、AUTO_UPDATE_STATISTICS_ASYNC は ON です。 

### <a name="error-messages"></a>エラー メッセージ
「PDW では、このオプションはサポートされていません」エラー メッセージが表示する可能性があります。  このエラーは、統計の自動、システム管理者が有効になっていないと、ALTER DATABASE の統計のオプションを設定、自動のいずれかを試行したときに発生します。 

### <a name="limitations-and-restrictions"></a>制限事項と制約事項
自動統計情報は、テーブルの外部では機能しません。 

### <a name="check-the-current-values"></a>現在の値を確認します。
次のクエリでは、すべてのデータベースの自動統計情報の設定の現在の値を返します。

```sql
SELECT NAME
    , IS_AUTO_CREATE_STATS_ON 
    , IS_AUTO_UPDATE_STATS_ON
    , IS_AUTO_UPDATE_STATS_ASYNC_ON
FROM
    sys.databases;
```

戻り値の設定の 1 の場合は、0 は、設定がオフです。 

## <a name="next-steps"></a>次の手順
クエリの実行方法を表示するには、次を参照してください[アクティブなクエリの監視。](monitoring-active-queries.md)

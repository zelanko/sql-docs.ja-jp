---
title: 自動統計 (Analytics Platform System)
description: Analytics Platform System AU7 で導入された自動統計機能をについて説明します。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 06/27/2018
ms.author: murshedz
ms.reviewer: martinle
monikerRange: '>= aps-pdw-2016-au7 || = sqlallproducts-allversions'
ms.openlocfilehash: caed6b9d126e09bc70a61c73b5100d689f81b011
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961278"
---
# <a name="configure-auto-statistics"></a>統計の自動構成します。

作成と統計情報を自動的に更新の自動統計を使用する並列データ ウェアハウスを構成する方法について説明します。  クエリのプランを向上させるためにこの機能を使用し、クエリのパフォーマンスが向上します。

**適用対象:** AP (2016 AU7 以降)

## <a name="what-are-statistics"></a>統計情報とは
クエリ最適化に関する統計は、テーブルの 1 つまたは複数の列の値の分布に関する統計情報が含まれているオブジェクトです。 クエリ オプティマイザーのカーディナリティの推定にこれらの統計情報を使用するや、クエリ内の行の数。 これらのカーディナリティの推定には、高品質のクエリ プランを作成するクエリ オプティマイザーが有効にします。 Ap、例としては、MPP クエリ オプティマイザーでは、カーディナリティの推定をランダム再生または複製そうと join 句で使用する 2 つのテーブルのうち、小さい方を選択するは、クエリのパフォーマンスを向上します。  詳細については、次を参照してください[統計](../relational-databases/statistics/statistics.md)と[DBCC show_statistics で。](../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)

## <a name="what-are-auto-statistics"></a>統計の自動とは
自動統計は、クエリ オプティマイザーで作成し、クエリ プランを向上させるために自動的に更新する統計情報です。 統計で、読み込み後に期限切れになることができます、挿入、更新、および操作を削除します。 自動の統計のない列に必要な統計情報と統計情報を更新する必要がある場合を理解する独自の分析を行う必要があります。

自動統計には、次の 3 つの設定が含まれています。 

### <a name="autocreatestatistics"></a>AUTO_CREATE_STATISTICS
統計の自動作成オプション AUTO_CREATE_STATISTICS が ON の場合、クエリ プランのカーディナリティの推定を向上させるために、クエリ オプティマイザーによってクエリ述語内の個々の列に関する統計が必要に応じて作成されます。 これらの 1 列ずつの統計は、既存の統計オブジェクトにまだヒストグラムがない列について作成されます。

### <a name="autoupdatestatistics"></a>AUTO_UPDATE_STATISTICS 
統計の自動更新オプション AUTO_UPDATE_STATISTICS がオンの場合、古くなっている可能性がある統計がクエリ オプティマイザーによって判断され、それらがクエリで使用されると更新されます。 挿入、更新、削除、またはマージの各操作によってテーブルまたはインデックス付きビューのデータの分布が変わると、統計は古くなったと判断されます。 クエリ オプティマイザーでは、統計が前回更新されてから発生したデータ変更の数をカウントし、その変更の数をしきい値と比較することで、統計が古くなっている可能性がないかを判断します。 このしきい値は、テーブルまたはインデックス付きビューの行数に基づいて決められます。

### <a name="autoupdatestatisticsasync"></a>AUTO_UPDATE_STATISTICS_ASYNC
統計の非同期更新オプション AUTO_UPDATE_STATISTICS_ASYNC によって、クエリ オプティマイザーで統計の同期更新と非同期更新のどちらを使用するかが決まります。 Ap、統計の非同期更新オプションは、既定で ON と、クエリ オプティマイザーが統計情報を非同期的に更新します。 AUTO_UPDATE_STATISTICS_ASYNC オプションは、インデックスに対して作成された統計オブジェクト、クエリ述語内の列に対して 1 列ずつ作成された統計オブジェクト、および CREATE STATISTICS ステートメントを使用して作成された統計に適用されます。

## <a name="configuration-settings-for-system-administrators"></a>システム管理者の構成設定
APS AU7 へのアップグレード後は、自動統計は既定で有効にします。 システム管理者を有効または無効で統計の自動、[機能スイッチ](appliance-feature-switch.md)アプライアンス Configuration Manager でのオプション。  有効にすると、ユーザーは、データベースごとの統計情報の設定を変更できます。
すべての機能スイッチの値を変更するには、AP 上、サービスの再起動が必要です。

## <a name="change-auto-statistics-settings-on-a-database"></a>データベースの自動統計設定を変更します。
使用することができます、システム管理者によって自動統計を有効にする、 [ALTER DATABASE (並列データ ウェアハウス)](../t-sql/statements/alter-database-transact-sql.md?tabs=sqlpdw)データベースで統計情報の設定を変更します。 自動統計機能スイッチは、システム管理者によって有効になっている、AU7 へのアップグレード後に作成されたすべての新しいデータベースが自動統計が有効になります。 AU7 へのアップグレードの前に存在しているすべてのデータベースがある自動統計情報が無効になっています。 次の例で、既存のデータベース myPDW の自動統計。

```sql
ALTER DATABASE myPDW SET AUTO_CREATE_STATISTICS ON
ALTER DATABASE myPDW SET AUTO_UPDATE_STATISTICS ON 
ALTER DATABASE myPDW SET AUTO_UPDATE_STATISTICS_ASYNC ON
```
 
AUTO_UPDATE STATISTICS_ASYNC のオプションは、AUTO_UPDATE_STATISTICS が ON の場合にのみ機能します。  そのため、統計は更新されません AUTO_UPDATE_STATISTICS が OFF の場合と AUTO_UPDATE_STATISTICS_ASYNC は ON です。 

### <a name="error-messages"></a>エラー メッセージ
「PDW では、このオプションはサポートされていません」エラー メッセージが表示する可能性があります。  このエラーは、システム管理者が統計の自動有効になっていないと、ALTER DATABASE の自動のいずれかの統計オプションを設定すると発生します。 

### <a name="limitations-and-restrictions"></a>制限事項と制約事項
自動統計は、テーブルの外部では機能しません。 

### <a name="check-the-current-values"></a>現在の値を確認してください。
次のクエリでは、すべてのデータベースの自動統計情報の設定の現在の値を返します。

```sql
SELECT NAME
    , IS_AUTO_CREATE_STATS_ON 
    , IS_AUTO_UPDATE_STATS_ON
    , IS_AUTO_UPDATE_STATS_ASYNC_ON
FROM
    sys.databases;
```

1 の設定には、戻り値が入っていて 0 は、設定がオフです。 

## <a name="next-steps"></a>次の手順
クエリの実行方法を確認するを参照してください[アクティブなクエリの監視。](monitoring-active-queries.md)

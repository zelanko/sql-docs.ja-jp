---
title: Data Migration Assistant (SQL Server) の設定の構成 |Microsoft Docs
description: 構成ファイル内の値を更新することで、Data Migration Assistant の設定を構成する方法について説明します
ms.custom: ''
ms.date: 03/12/2019
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Assess
ms.assetid: ''
author: HJToland3
ms.author: rajpo
manager: jroth
ms.openlocfilehash: a360c86edc08916f1e28157a54503f64c152dec7
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66794386"
---
# <a name="configure-settings-for-data-migration-assistant"></a>Data Migration Assistant の設定を構成します。

Dma.exe.config ファイルで構成値を設定して、Data Migration Assistant の特定の動作を微調整できます。 この記事では、キーの構成値について説明します。

コンピューターに次のフォルダーに、Data Migration Assistant のデスクトップ アプリケーションと、コマンド ライン ユーティリティでは、dma.exe.config ファイルを見つけることができます。

- デスクトップ アプリケーション

  %Programfiles%\\Microsoft Data Migration Assistant\\dma.exe.config

- コマンド ライン ユーティリティ

  %Programfiles%\\Microsoft Data Migration Assistant\\dmacmd.exe.config 

必ずすべての変更を行う前に元の構成ファイルのコピーを保存してください。 変更を行った後、Data Migration Assistant の新しい構成値を有効にするを再起動します。

## <a name="number-of-databases-to-assess-in-parallel"></a>並列で評価するためのデータベースの数

Data Migration Assistant は、並列で複数のデータベースを評価します。 評価時に Data Migration Assistant は、データベース スキーマを理解するのには、データ層アプリケーション (dacpac) を抽出します。 この操作では、同じサーバー上の複数のデータベースが並列で評価される場合は、タイムアウトになることができます。 

Data Migration Assistant のバージョン 2.0 以降では、制御できますこの、parallelDatabases 構成値を設定しています。 既定値は 8 です。

```
<advisorGroup>

<workflowSettings>

<assessment parallelDatabases="8" />

</workflowSettings>

</advisorGroup>
```




## <a name="number-of-databases-to-migrate-in-parallel"></a>並列移行するデータベースの数

Data Migration Assistant は移行を並列に複数のデータベースが前に移行するログイン。 移行中に、Data Migration Assistant は、ソース データベースのバックアップを作成、必要に応じて、バックアップをコピーし、ターゲット サーバー上に復元します。 移行のための複数のデータベースが選択されている場合は、タイムアウト エラーが発生する可能性があります。 

この問題が発生した場合は、Data Migration Assistant の v2.0 以降 parallelDatabases 構成値を小さきます。 全体的な移行時間を短縮する値を大きくことができます。

```
<advisorGroup>

<workflowSettings>

<migration parallelDatabases="8″ />

</workflowSettings>

</advisorGroup>
```


## <a name="dacfx-settings"></a>DacFX の設定

評価中に Data Migration Assistant は、データベース スキーマを理解するのには、データ層アプリケーション (dacpac) を抽出します。 この操作は失敗と非常に大規模なデータベースは、タイムアウトまたはサーバーの負荷がかかった場合。 以降のデータ移行 v1.0 では、エラーを回避するために、次の構成値を変更できます。 

> [!NOTE]
> 全体&lt;dacfx&gt;エントリは既定でコメントされています。 コメントを削除し、必要に応じて、値を変更します。

- commandTimeout

   このパラメーター IDbCommand.CommandTimeout プロパティを設定する*秒*します。 (既定 = 60)

- databaseLockTimeout

   このパラメーターは[SET LOCK\_タイムアウト タイムアウト\_期間](../t-sql/statements/set-lock-timeout-transact-sql.md)で*ミリ秒*します。 (既定 = 5000)

- maxDataReaderDegreeOfParallelism

  このパラメーターは、使用する SQL 接続プールの接続の数を設定します。 (既定値 = 8)

```
<advisorGroup>

<advisorSettings>

<dacFx  commandTimeout="60" databaseLockTimeout="5000"
maxDataReaderDegreeOfParallelism="8"/>

</advisorSettings>

</advisorGroup>
```

## <a name="stretch-database-recommendation-threshold"></a>Stretch Database は:推奨事項のしきい値

[SQL Server Stretch Database](https://docs.microsoft.com/sql/sql-server/stretch-database/stretch-database)、ウォームおよびコールド トランザクション データを Microsoft SQL Server 2016 から Azure に動的に拡張することができます。 ターゲットのコールド データの大量のトランザクション データベースの Stretch Database。 最初に Stretch Database の推奨事項の記憶域機能の推奨事項の下には、テーブルを識別と思われることが、この機能から得られるし、この機能については、表を可能にするために必要な変更を識別します。

Data Migration Assistant の v2.0 以降、recommendedNumberOfRows 構成値を使用して、Stretch Database 機能の対象テーブルについては、このしきい値を制御できます。 既定値は 100,000 行です。 さらに小さなテーブルの拡張機能を分析する場合は、それに応じて値を低くします。

```
<advisorGroup>

<advisorSettings>

<stretchDBAdvisor  recommendedNumberOfRows="100000" />

</advisorSettings>

</advisorGroup>
```


## <a name="sql-connection-timeout"></a>SQL 接続のタイムアウト

制御することができます、 [SQL 接続のタイムアウト](https://msdn.microsoft.com/library/system.data.sqlclient.sqlconnection.connectiontimeout(v=vs.110).aspx)の接続のタイムアウト値を指定した秒数に設定して、評価または移行の実行中にソースとターゲットのインスタンス。 既定値は 15 秒です。

```
<appSettings>

<add key="ConnectionTimeout" value="15" />

</appSettings>
```


## <a name="see-also"></a>関連項目

[データ移行アシスタントをダウンロード](https://www.microsoft.com/download/details.aspx?id=53595)

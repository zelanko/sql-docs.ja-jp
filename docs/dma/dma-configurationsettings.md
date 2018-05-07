---
title: 構成設定 (SQL Server データ Migration Assistant) |Microsoft ドキュメント
ms.custom: ''
ms.date: 08/31/2017
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.suite: sql
ms.technology: dma
ms.tgt_pltfrm: ''
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Assess
ms.assetid: ''
caps.latest.revision: ''
author: HJToland3
ms.author: jtoland
manager: craigg
ms.openlocfilehash: 4b42f816755b312f95609bd25ac6122b8fbf321c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="configuration-settings-for-data-migration-assistant"></a>データ Migration Assistant の構成設定

データ Migration Assistant の dma.exe.config ファイルの構成値を使用して特定の動作を微調整することができます。 この記事では、キーの構成値について説明します。

コンピューターに次のフォルダーにデータ Migration Assistant のデスクトップ アプリケーションおよびコマンド ライン ユーティリティの dma.exe.config ファイルを検索できます。

- デスクトップ アプリケーション

  %Programfiles%\\Microsoft データ Migration Assistant\\dma.exe.config

- コマンド ライン ユーティリティ

  %Programfiles%\\Microsoft データ Migration Assistant\\dmacmd.exe.config 

変更を加える前に、元の構成ファイルのコピーを保存することを確認します。 変更を行った後、データ Migration Assistant for、新しい構成値を有効にするを再起動します。

## <a name="number-of-databases-to-assess-in-parallel"></a>並列で評価するデータベースの数

データ移行アシスタントは、並列で複数のデータベースを評価します。 評価中にデータ Migration Assistant は、データベース スキーマを理解するのには、データ層アプリケーション (dacpac) を抽出します。 この操作には、同じサーバー上の複数のデータベースが並列に評価される場合のタイムアウトことができます。 

データ Migration Assistant バージョン 2.0 以降では、制御するこのでできます、parallelDatabases 構成値を設定します。 既定値は 8 です。

```
<advisorGroup>

<workflowSettings>

<assessment parallelDatabases="8" />

</workflowSettings>

</advisorGroup>
```




## <a name="number-of-databases-to-migrate-in-parallel"></a>並列移行するデータベースの数

前に、並列で複数のデータベースを移行データ Migration Assistant 移行ログインします。 移行中に、データ Migration Assistant はソース データベースのバックアップを作成、必要に応じて、バックアップをコピーし、対象サーバー上に復元します。 移行のいくつかのデータベースを選択するとタイムアウト エラーが発生する可能性があります。 

この問題が発生した場合、データ Migration Assistant バージョン 2.0 で始まる parallelDatabases 構成値を削減できます。 全体的な移行時間を短縮する値を大きくことができます。

```
<advisorGroup>

<workflowSettings>

<migration parallelDatabases=”8″ />

</workflowSettings>

</advisorGroup>
```


## <a name="dacfx-settings"></a>DacFX の設定

評価中にデータ Migration Assistant は、データベース スキーマを理解するのには、データ層アプリケーション (dacpac) を抽出します。 この操作は失敗と非常に大規模なデータベースは、タイムアウト、またはサーバーの負荷がかかっている場合。 以降のデータ移行 v1.0 では、エラーを回避するのには、次の構成値を変更することができます。 

> [!NOTE]
> 全体&lt;dacfx&gt;エントリが既定ではコメントです。 コメントを削除し、必要に応じて値を変更します。

- CommandTimeout

   これは、プロパティを設定します IDbCommand.CommandTimeout*秒*です。 (既定 = 60)

- databaseLockTimeout

   これに相当[SET LOCK\_タイムアウト タイムアウト\_期間](../t-sql/statements/set-lock-timeout-transact-sql.md)で*ミリ秒*です。 (既定 = 5000)

- maxDataReaderDegreeOfParallelism

   使用する SQL 接続プールの接続の数。 (既定値 = 8)

```
<advisorGroup>

<advisorSettings>

<dacFx  commandTimeout="60" databaseLockTimeout="5000"
maxDataReaderDegreeOfParallelism="8"/>

</advisorSettings>

</advisorGroup>
```


## <a name="stretch-database-recommendation-threshold"></a>Stretch Database: 推奨設定のしきい値

[SQL Server Stretch Database](https://docs.microsoft.com/sql/sql-server/stretch-database/stretch-database)、ウォーム データとコールド トランザクション データから Microsoft SQL Server 2016 を Azure に動的にストレッチできます。 Stretch データベース コールド データの大量のトランザクション データベースを対象にします。 記憶域機能の推奨設定で、Stretch Database、推奨事項が最初にテーブルを識別と思われることは、この機能を利用してから、この機能のテーブルを有効にするために必要な変更を識別します。

データ Migration Assistant バージョン 2.0 以降、recommendedNumberOfRows 構成値を使用して、Stretch Database 機能を修飾するためにテーブルには、このしきい値を制御できます。 既定値は、100,000 行です。 さらに小さくテーブルのストレッチの機能を分析する場合、値より低いそれに応じて。

```
<advisorGroup>

<advisorSettings>

<stretchDBAdvisor  recommendedNumberOfRows="100000" />

</advisorSettings>

</advisorGroup>
```


## <a name="sql-connection-timeout"></a>SQL 接続のタイムアウト

制御することができます、 [SQL 接続のタイムアウト](https://msdn.microsoft.com/library/system.data.sqlclient.sqlconnection.connectiontimeout(v=vs.110).aspx)の接続のタイムアウト値を指定した秒数に設定して、評価や、移行を実行中にソースとターゲットのインスタンス。 既定値は 15 秒です。

```
<appSettings>

<add key="ConnectionTimeout" value="15" />

</appSettings>
```


## <a name="see-also"></a>参照

[データ移行アシスタントをダウンロード](https://www.microsoft.com/download/details.aspx?id=53595)

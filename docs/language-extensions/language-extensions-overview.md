---
title: SQL Server 言語拡張とは?
titleSuffix: ''
description: 言語拡張は、外部コードの実行に使用される SQL Server の機能です。 SQL Server 2019 では、Java、Python、R がサポートされています。 リレーショナル データは、機能拡張フレームワークを使用して外部コードで使用できます。
author: dphansen
ms.author: davidph
ms.date: 10/07/2020
ms.topic: overview
ms.prod: sql
ms.technology: language-extensions
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 09d5643b3a39493843adc0ad2da716b7fda1b332
ms.sourcegitcommit: fe59f8dc27fd633f5dfce54519d6f5dcea577f56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/09/2020
ms.locfileid: "91934900"
---
# <a name="what-is-sql-server-language-extensions"></a>SQL Server 言語拡張とは?
[!INCLUDE [SQL Server 2019 and later](../includes/applies-to-version/sqlserver2019.md)]

言語拡張は、外部コードの実行に使用される SQL Server の機能です。 リレーショナル データは、[機能拡張フレームワーク](concepts/extensibility-framework.md)を使用して外部コードで使用できます。

SQL Server 2019 では、Java、Python、R がサポートされています。

> [!NOTE]
> SQL Server での Python または R の実行については、[SQL 機械学習](../machine-learning/index.yml)のドキュメントを参照してください。 SQL Server 2019 以降では、言語拡張で Python および R のカスタム ランタイムを使用できます。 詳細については、[Python カスタム ランタイム](../machine-learning/install/custom-runtime-python.md) と [R カスタム ランタイム](../machine-learning/install/custom-runtime-r.md)に関する各記事を参照してください。

## <a name="what-you-can-do-with-language-extensions"></a>言語拡張でできること

言語拡張には、外部コードの実行に拡張機能フレームワークが使用されます。 コードの実行はコア エンジン プロセスから分離されていますが、SQL Server のクエリ実行と完全に統合されています。 データのソースでコードを実行できるため、ネットワーク経由でデータをプルする必要はありません。

外部言語は [CREATE EXTERNAL LANGUAGE](../t-sql/statements/create-external-language-transact-sql.md) で定義されます。 システム ストアド プロシージャ [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) は、コードを実行するためのインターフェイスとして使用されます。

言語拡張には、次のような利点があります。

+ データのセキュリティ。 外部言語の実行をデータのソースに近づけることにより、無駄な、または安全でないデータ移動を回避できます。
+ 速さ。 データベースは、セットベースの操作用に最適化されています。 インメモリ テーブルなどのデータベースの最近のイノベーションにより、サマリーと集計が高速になり、データ サイエンスを完全に補完することができます。
+ 展開と統合の容易さ。 [!INCLUDE [ssNoVersion](../includes/ssnoversion-md.md)] は、他の多くのデータ管理タスクおよびアプリケーションの操作の中心となるポイントです。 データベース内のデータを使用することで、言語拡張で使用されるデータの一貫性と最新性を確保できます。

## <a name="next-steps"></a>次のステップ

+ [SQL Server 用の Python カスタム ランタイム](../machine-learning/install/custom-runtime-python.md)をインストールする
+ [SQL Server 用の R カスタム ランタイム](../machine-learning/install/custom-runtime-r.md)をインストールする
+ [Windows](install/install-sql-server-language-extensions-on-windows.md) または [Linux に SQL Server 言語拡張](../linux/sql-server-linux-setup-language-extensions.md)をインストールする
+ [Microsoft 拡張機能 SDK for Java](how-to/extensibility-sdk-java-sql-server.md) をインストールします

---
title: "SQL Server のデータを扱う RevoScaleR 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: R
ms.assetid: 5f3c9864-9c75-4688-947d-0940045b2671
caps.latest.revision: "9"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 08d8d3e6a13066aa79c96ba161e1c9d8f230e60f
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="revoscaler-functions-for-working-with-sql-server-data"></a>SQL Server のデータを扱う RevoScaleR 関数

このトピックでは、SQL Server のデータを操作するために、RevoScaleR で提供されるメインの機能の概要を示します。

ScaleR 関数およびその使用方法の完全な一覧については、 [Microsoft R Server](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler)参照します。

## <a name="create-sql-server-data-sources"></a>SQL Server データ ソースを作成します。

次の関数を使用して、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] データ ソースを定義できます。 データ ソース オブジェクトは、接続文字列と一緒に必要な一連のデータを指定するコンテナーです。テーブル、ビュー、またはクエリとして定義されます。 ストアド プロシージャの呼び出しはサポートされていません。

+ [RxSqlServerData](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsqlserverdata)の定義、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]データ ソース オブジェクト。

+ [RxOdbcData](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxodbcdata) -その他の ODBC データベースのデータ オブジェクトを作成します。 

## <a name="perform-ddl-statements"></a>DDL ステートメントを実行します。

インスタンスおよびデータベースに必要なアクセス許可がある場合は、R から DDL ステートメントを実行できます。 次の関数では、ODBC 呼び出しを使用する DDL ステートメントを実行したり、データベース スキーマを取得します。

+ `rxSqlServerTableExists`および[rxSqlServerDropTable](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsqlserverdroptable)のドロップ、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]テーブル、またはデータベース テーブルまたはオブジェクトの有無を確認

+ [rxExecuteSQLDDL](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxexecutesqlddl) -データ定義言語 (DDL) コマンドを定義またはデータベース オブジェクトの操作を実行します。 この関数は、データを返すことはできませんし、取得またはオブジェクトのスキーマまたはメタデータの変更にのみ使用されます。

## <a name="define-or-manage-compute-contexts"></a>定義または計算コンテキストの管理

次の関数を使用して、新しい計算コンテキストの定義、計算コンテキストの切り替え、現在の計算コンテキストの識別を行います。

+ [RxComputeContext](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxcomputecontext) - 計算コンテキストを作成します。

+ [rxInSqlServer](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxinsqlserver) - SQL Server 計算コンテキストを生成して、**ScaleR** 関数が SQL Server R Services で実行するようにします。 現在、この計算コンテキストは Windows の SQL Server インスタンスのみでサポートされています。

+ `rxGetComputeContext`および[rxSetComputeContext](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxgetcomputecontext) - を取得またはアクティブなコンピューティング コンテキストを設定します。

## <a name="move-data-and-transform-data"></a>データを移動し、データを変換します。

データ ソース オブジェクトを作成した後は、データを読み込む、データを変換、または指定した宛先に新しいデータを書き込み、オブジェクトを使用できます。 ソースのデータのサイズによりますが、データ ソースの一部としてバッチ サイズを定義し、データをチャンク単位で動かすことができます。

+ [rxOpen メソッド](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxopen-methods)- 開くデータ ソースを使用できるかどうかを確認またはデータ ソースを閉じて、ソースからデータを読み取るをターゲットにデータを書き込むおよびデータ ソースを閉じます

+ [rxImport](https://docs.microsoft.com/r-server/r-reference/revoscaler/rximport) -ファイル ストレージ、またはデータ フレームには、データ ソースからデータを移動します。

+ [rxDataStep](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdatastep) -データ ソース間で移動中にデータを変換します。

XDF 形式でローカル データ ストアを作成するのには、次の関数を使用できます。 このファイルが役立つのは、扱うデータ容量がデータベースから 1 回で転送できない場合や、メモリに収まりきらない場合です。

たとえば、ローカル ワークステーションに、データベースから定期的に大量のデータを移動する場合のクエリではなく R 操作ごとに繰り返しデータベースことができます、XDF ファイルとして使用するキャッシュの種類をローカルでデータを保存し、R ワークスペースで作業し、します。

+ [RxXdfData](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxxdfdata) -XDF データ オブジェクトを作成します。

+ [rxReadXdf](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxreadxdf) -XDF ファイルからデータをデータ フレームに読み込みます

これらの関数の使用に関する詳細については、データの使用を含むソース以外の[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]を参照してください[Howto ガイド Microsoft R でのデータ分析](https://docs.microsoft.com/r-server/r/how-to-introduction)です。

---
title: SQL Server R Services での R の相互運用性 | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: da739700cabb6a9d691d5f284cd6f0532898393f
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2018
ms.locfileid: "38979024"
---
# <a name="r-interoperability-in-sql-server"></a>SQL Server での R の相互運用性
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

このトピックでは、SQL Server 内で R を実行するためのメカニズムに重点を置いていて、Microsoft R とオープン ソース R. の違いについて説明します

適用対象: SQL Server 2016 R Services、SQL Server 2017 の Machine Learning サービス

その他のコンポーネントについては、次を参照してください。 [SQL Server の新しいコンポーネント](../../advanced-analytics/r-services/new-components-in-sql-server-to-support-r.md)します。

### <a name="open-source-r-components"></a>オープン ソースの R コンポーネント

[!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] には、基本の R パッケージとツールの完全なディストリビューションが含まれています。 基本のディストリビューションに何が含まれているかの詳細については、セットアップ中に既定の場所 (`C:\Program Files\Microsoft SQL Server\<instance_name>\R_SERVICES\doc\manual`) にインストールされるドキュメントを参照してください。

[!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] のインストールの一環として、GNU Public License の条項に同意する必要があります。 その後、R の他のオープン ソース ディストリビューションと同じように、標準 R パッケージを変更なしで実行できます。

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] が R ランタイムを何らかの方法で変更することはありません。 R ランタイムは [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] プロセスの外部で実行され、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] とは無関係に実行できます。 ただし、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] で R を使用している間は、リソースの競合を避けるために、これらのツールを実行しないことを強くお勧めします。

特定の [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]インスタンスに関連付けられている R 基本パッケージ ディストリビューションは、インスタンスに関連付けられているフォルダーで見つけることができます。 たとえば、既定のインスタンスに R Services をインストールした場合、R ライブラリ内にあるこのフォルダー既定では。

    C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library

同様に、既定のインスタンスに関連付けられている R ツールは、既定では足りないのフォルダーに配置すると。

    C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\bin

Microsoft R の CRAN から発生する可能性のある R の基本分布の違いについての詳細については、次を参照してください[R 言語と Microsoft R 製品の機能との相互運用性。](https://docs.microsoft.com/r-server/what-is-r-server-interoperability)

### <a name="additional-r-packages-from-microsoft-r"></a>Microsoft R から追加の R パッケージ

基本の R ディストリビューションに加え[!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)]もリモート計算コンテキストで R の実行をサポートする R の並列実行するためのフレームワークと同様にいくつか独自の R パッケージが含まれています。

R の基本ディストリビューションと拡張された R の機能とパッケージの組み合わせを **Microsoft R** と呼びます。Microsoft R Server (スタンドアロン) をインストールすると、SQL Server R Services (In-Database) とまったく同じパッケージセットが、別のフォルダーにインストールされます。

Microsoft R には、数的処理を高速化できる場合は常に使用される Intel Math Kernel Library のディストリビューションが含まれています。 たとえば、基本線形代数 (BLAS) は、R 自体だけではなく、多くのアドオン パッケージでも使用されます。 詳細については、次の記事を参照してください。

+ [How the Intel Math Kernel Speeds up R (Intel Math Kernel が R を高速化する方法)](http://blog.revolutionanalytics.com/2014/10/revolution-r-open-mkl.html)
+ [Performance benefits of linking R to multithreaded math libraries (マルチ スレッド数値演算ライブラリに R をリンクすることのパフォーマンス上のメリット)](http://blog.revolutionanalytics.com/2010/06/performance-benefits-of-multithreaded-r.html)

Microsoft R に追加されたものの中で最も重要なのは、**RevoScaleR** パッケージと **RevoPemaR** パッケージです。 これらは、パフォーマンスを向上させるために大部分が C または C++ で記述されている R パッケージです。

+ **RevoScaleR**。 データ操作と分析用のさまざまな API が含まれています。 これらの API は、大きすぎてメモリに収まらないデータ セットの分析と複数のコアまたはプロセッサでの分散計算を実行するように最適化されています。

   RevoScaleR API は、スケーラビリティを向上させるために、データのサブセットの操作もサポートします。 つまり、ほとんどの RevoScaleR 関数はデータのチャンクを操作でき、更新アルゴリズムを使用して結果を集計できます。 したがって、RevoScaleR 関数に基づく R ソリューションは、非常に大きなデータ セットを操作でき、ローカル メモリに制約されません。

  RevoScaleR パッケージは、分析のために使用されるデータの高速移動と格納用の XDF ファイル形式もサポートします。 XDF 形式は、カラム型ストレージを使用する移植可能な形式であり、テキスト、SPSS、ODBC 接続などのさまざまなソースからデータを読み込んで操作するために使用できます。 

+ **RevoPemaR**。 PEMA は、Parallel External Memory Algorithm (並列外部メモリ アルゴリズム) の略です。 **RevoPemaR** パッケージは、独自の並列アルゴリズムを開発するために使用できる API を提供します。 詳細については、[RevoPemaR の使用開始に関するガイド](https://docs.microsoft.com/r-server/r/how-to-developer-pemar)を参照してください。

試してみることをお勧め[MicrosoftML](https://docs.microsoft.com/r-server/r/concept-what-is-the-microsoftml-package)、分散処理、R コードのかつスケーラブルなリモート実行をサポートする Microsoft R から新しいパッケージは、Microsoft Research によって開発強化された機械学習アルゴリズムを使用します。

## <a name="next-steps"></a>次のステップ

[アーキテクチャの概要](../../advanced-analytics/r/architecture-overview-sql-server-r.md)

[R をサポートする SQL Server コンポーネント](../../advanced-analytics/r/new-components-in-sql-server-to-support-r.md)

[セキュリティの概要](../../advanced-analytics/r/security-overview-sql-server-r.md)


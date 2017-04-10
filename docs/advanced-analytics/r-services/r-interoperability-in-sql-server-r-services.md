---
title: "SQL Server の R のサービスでの R の相互運用性 | Microsoft Docs"
ms.custom: ""
ms.date: "05/31/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0506b950-34b3-4f11-8e2f-d067a58015bd
caps.latest.revision: 9
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 8
---
# SQL Server の R のサービスでの R の相互運用性

このトピックのねらいで R を実行するためのメカニズムで [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)], 、Microsoft R とオープン ソース r. の違いについて説明し、その他のコンポーネントについては、次を参照してください。 [SQL Server の新しいコンポーネント](../../advanced-analytics/r-services/new-components-in-sql-server-to-support-r-services.md)します。

### オープン ソース R のコンポーネント

[!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] 基本の R パッケージとツールの完全な分布が含まれます。 基本のディストリビューションに含まれる新機能の詳細については、セットアップ時に次の既定の場所にインストールされるドキュメントを参照してください。
`C:\Program Files\Microsoft SQL Server\<instance_name>\R_SERVICES\doc\manual`

インストールの一部として [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)], 、GNU Public License の条項に同意する必要があります。 R です。 その他のオープン ソース配布の場合と同様に、それ以上変更せずに標準の R パッケージを実行するその後、

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] R ランタイムを任意の方法では変更されません。 外部の R ランタイムが実行される、 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] を処理しとは無関係に実行できる [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]です。 ただし、強くお勧めしながら、これらのツールを実行しない [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] リソースの競合を避けるために、R を使用しています。

R 基本パッケージの配布、固有の仕様に関連付けられている [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] インスタンスがインスタンスに関連付けられているフォルダーにあります。 たとえば、既定のインスタンスにサービスの R をインストールした場合、R ライブラリ内にある `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library`です。

同様に、既定のインスタンスに関連付けられている R ツールに見つかりません `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\bin`,、。

ベースの配布に関する詳細については、次を参照してください [Microsoft R Open とインストールされているパッケージ。](https://mran.revolutionanalytics.com/rro/installed/)

### その他の R パッケージ

基本の R 配布だけでなく [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] R、およびリモート コンピューティングのコンテキストでの R の実行をサポートするライブラリの並列実行するためのフレームワークと同様にいくつかの独自の R パッケージが含まれています。 

この結合された - R ベースの配布と、R の高度な機能とパッケージ - R 機能のセットと呼びます **Microsoft R**します。Microsoft R サーバー (スタンドアロン) をインストールする場合は、まったく同じ一連の SQL Server R Services (データベース) とは別のフォルダーにインストールされているパッケージを取得します。 

Microsoft R には、数学的な処理を高速に可能な場合に使用される Intel Math カーネル ライブラリの分布が含まれています。 たとえば、アドオン パッケージは、R 自体の場合と同様の多くの基本的な線形代数 (BLAS) ライブラリが使用します。 詳細については、次の記事を参照してください。

+ [Intel Math カーネルが R を高速化する方法](http://blog.revolutionanalytics.com/2014/10/revolution-r-open-mkl.html)
+ [マルチ スレッド数値演算ライブラリへの R のリンクのパフォーマンスの利点](http://blog.revolutionanalytics.com/2010/06/performance-benefits-of-multithreaded-r.html)

Microsoft の R の最も重要な追加機能には、 **RevoScaleR** と **RevoPemaR** パッケージです。 これらは、パフォーマンス向上のため、C または C++ で大きく書き込まれている R パッケージです。

+ **RevoScaleR します。** さまざまな Api をデータ操作と分析のために含まれています。 Api は、大きすぎてメモリに収まるように、いくつかのコアまたはプロセッサに分散計算を実行するデータ セットを分析する最適化されています。

   RevoScaleR Api では、拡張性が向上データのサブセットの使用もサポートします。 つまり、ほとんどの RevoScaleR 関数は、使用して結果を集計するアルゴリズムを更新し、データのチャンクを処理できます。 したがって RevoScaleR 関数に基づいて R ソリューションでは、非常に大きなデータ セットを使用できるしはローカル メモリによってバインドされません。

  RevoScaleR パッケージもサポートします。高速の移動および分析のために使用されるデータの格納および XDF ファイル形式です。 および XDF 形式は、列記憶を使用して、移植可能では、および、読み込みし、テキスト、SPSS、ODBC 接続など、さまざまなソースからデータを操作に使用できます。 および XDF 形式を使用する方法の例は、このチュートリアルで説明します [データ サイエンスの詳細情報。](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md)


+ **RevoPemaR します。** PEMA 外部メモリの並列アルゴリズムの略です。  **RevoPemaR** パッケージは、独自の並列アルゴリズムを開発に使用できる Api を提供します。 詳細については、次を参照してください。 [RevoPemaR ファースト ステップ ガイド](https://msdn.microsoft.com/microsoft-r/rserver/rserver-pemar-getting-started)します。

## 参照
[アーキテクチャの概要](../../advanced-analytics/r-services/architecture-overview-sql-server-r-services.md)

[R のサービスをサポートする SQL Server の新しいコンポーネント](../../advanced-analytics/r-services/new-components-in-sql-server-to-support-r-services.md)

[セキュリティの概要](../../advanced-analytics/r-services/security-overview-sql-server-r-services.md)

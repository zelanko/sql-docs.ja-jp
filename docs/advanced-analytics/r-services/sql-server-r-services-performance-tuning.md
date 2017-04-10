---
title: "SQL Server R サービスのパフォーマンス チューニング | Microsoft Docs"
ms.custom: ""
ms.date: "03/10/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cf6f3b7d-f9f9-4e45-b0d1-07850b53e0c5
caps.latest.revision: 20
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 19
---
# SQL Server R サービスのパフォーマンス チューニング
[!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] では、新たな洞察を得るためのインテリジェント アプリケーションの開発用プラットフォームが提供されます。 データ サイエンティストは、R 言語の性能を使用してトレーニングし、内部に格納されているデータを使用して、モデルを作成 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]します。 モデルが運用環境の準備、データ サイエンティストは、実稼働環境で、ソリューションを配置するには、データベース管理者と SQL エンジニアを操作できます。 このセクションの情報は、実稼働環境にモデルを展開するときに作成して、モデルをトレーニングされ、両方のパフォーマンスの調整に関する高レベルのガイダンスを提供します。

このドキュメントの情報は、使用について理解するいると想定しています。 [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] 概念と用語です。 R のサービスの概要については、次を参照してください。 [SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services.md)します。

> [!NOTE]
> このセクションの情報の多くは、一般的なガイダンスの構成について、 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], 、RevoScaleR 分析関数に固有のいくつかの情報です。

## このセクションの内容

* [SQL Server の構成](../../advanced-analytics/r-services/sql-server-configuration-r-services.md): ハードウェアを構成するためのガイダンスを提供する [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] にインストールします。 最も便利に __データベース管理者__します。

* [R とデータの最適化](../../advanced-analytics/r-services/r-and-data-optimization-r-services.md): R サービスでの R スクリプトの使用に関するガイダンスを提供します。 最も便利に __データ サイエンティスト__します。

* [パフォーマンスのケース スタディ](../../advanced-analytics/r-services/performance-case-study-r-services.md): このドキュメントではテスト データと R スクリプトの前のドキュメントに記載されているガイダンスの影響をテストするために使用できます。

## References

このドキュメントの開発に使用される情報へのリンクを次に示します。

* [64 ビット バージョンの Windows 用の適切なページ ファイル サイズを判断する方法](https://support.microsoft.com/kb/2860880)

* [データの圧縮](../../relational-databases/data-compression/data-compression.md)

* [テーブルまたはインデックスの圧縮の有効化](../../relational-databases/data-compression/enable-compression-on-a-table-or-index.md)

* [テーブルまたはインデックスの圧縮の無効化](../../relational-databases/data-compression/disable-compression-on-a-table-or-index.md)

* [DISKSPD ストレージ ロード ジェネレーター/パフォーマンス テスト ツール](https://github.com/microsoft/diskspd)

* [FSUtil ユーティリティ リファレンス](https://technet.microsoft.com/library/cc753059.aspx)

* [インデックスの再編成と再構築](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md)

* [R Services](../../advanced-analytics/r-services/r-services.md)

* [RxDForest および rxDTree のパフォーマンス チューニング オプション](https://support.microsoft.com/kb/3104235)

* [パフォーマンスの監視とチューニング](../../relational-databases/performance/monitor-and-tune-for-performance.md)

* [RevoScaleR ユーザー ガイド](https://packages.revolutionanalytics.com/doc/7.0.0/win/RevoScaleR_Users_Guide.pdf)

* [リソース ガバナー](../../relational-databases/resource-governor/resource-governor.md)

## 参照

 
 [R のサービスの SQL Server の構成](../../advanced-analytics/r-services/sql-server-configuration-r-services.md)
 
 [パフォーマンスのケース スタディ](../../advanced-analytics/r-services/performance-case-study-r-services.md)
 
 [R とデータの最適化](../../advanced-analytics/r-services/r-and-data-optimization-r-services.md)
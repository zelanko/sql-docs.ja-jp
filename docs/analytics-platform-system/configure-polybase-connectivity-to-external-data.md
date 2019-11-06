---
title: PolyBase 接続 - Analytics Platform System の構成 |Microsoft Docs
description: 外部の Hadoop または Microsoft Azure storage blob のデータ ソースに接続するための Parallel Data Warehouse で PolyBase を構成する方法について説明します。 PolyBase を使用して、Hadoop、Azure blob storage、および Parallel Data Warehouse を含む複数のソースからデータを統合するクエリを実行します。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: c218d686951e8855dd0687e35c1b777b0ae29617
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961249"
---
# <a name="what-is-polybase"></a>PolyBase とは
PolyBase は、Analytics Platform System (APS) からデータを読み取るし、外部データ ソースにデータを書き込むことができますを TRANSACT-SQL クエリの処理を使用できます。 外部データにアクセスするのと同じクエリでは、AP にリレーション テーブルを含めることもできます。 これにより、AP データベースで高価値のリレーショナル データを外部ソースからデータを組み合わせることができます。

![PolyBase 論理](media/polybase/polybase-logical.png)

AP 上の PolyBase では、Hadoop (HDFS) ファイル システムと Azure Blob ストレージに対する読み取りと書き込みをサポートします。 PolyBase では、全体的なクエリ パフォーマンスを最適化する mapreduce ジョブとして Hadoop ノードにいくつかの計算をプッシュする機能もあります。 AP 上の PolyBase は、ファイルに、ORC、Parquet の区切り記号付きのテキストを操作できます。 参照してください[PolyBase は](https://docs.microsoft.com/sql/relational-databases/polybase/polybase-guide)の完全な説明とその機能。

> [!NOTE]
> APS 現在のみサポートしている標準の汎用 v1 ローカル冗長 (LRS) Azure Blob Storage。

## <a name="features-and-limitations"></a>機能および制限事項
参照してください[機能と制限](https://docs.microsoft.com/sql/relational-databases/polybase/polybase-versioned-feature-summary)PolyBase の概要機能の AP とその他の SQL Server 製品で使用可能なと既知の制限の。

> [!NOTE] 
> PolyBase の残りの部分は、APS 2016 (AU6) 以降、PolyBase を構成する方法を記事に示しますに関連します。

## <a name="see-also"></a>関連項目
- [Hadoop](polybase-configure-hadoop.md)
- [Azure Blob Storage](polybase-configure-azure-blob-storage.md)
<!-- MISSING LINKS [PolyBase &#40;SQL Server PDW&#41;](../sqlpdw/polybase-sql-server-pdw.md)  -->  
  

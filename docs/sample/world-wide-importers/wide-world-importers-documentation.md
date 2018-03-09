---
title: "Wide World Importers のドキュメント |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: samples
ms.technology:
- samples
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 17cabd9d-cb2f-436c-ad9c-ce02225808b7
caps.latest.revision: 
author: BarbKess
ms.author: barbkess
manager: jhubbard
robots: noindex,nofollow
ms.workload: On Demand
ms.openlocfilehash: a2510ee889f57f7ab51c0f45574a8fa6e86abb47
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="wide-world-importers-documentation"></a>Wide World Importers のドキュメント
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]Wide World importers 社は、SQL Server 2016 の新しいサンプル データベースと Azure SQL データベースです。 SQL Server 2016 と Azure SQL データベースのトランザクション処理 (OLTP)、データ ウェアハウスと分析 (OLAP) ワークロード、だけでなくハイブリッド トランザクションと分析処理 (HTAP) ワークロードのコア機能を示しています。

## <a name="about-this-sample"></a>このサンプルについて

Wide World importers 社は、包括的なデータベース サンプル データベース設計を示していますし、アプリケーションで SQL Server の機能を活用する方法を示しています。

サンプルは一般的なデータベースの代表であることを意図したことに注意してください。 SQL Server のすべての機能は含まれません。 データベースの設計に依存して、標準の 1 つの共通セットが、さまざまな方法で 1 つのデータベースを構築する可能性があります。

**最新のリリース**: [wide world importers 社リリース](http://go.microsoft.com/fwlink/?LinkID=800630)

**サンプルのコードをソース**: [wide world-importers 社](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/wide-world-importers)です。

**フィードバック**: に送信してください[ sqlserversamples@microsoft.com](mailto:sqlserversamples@microsoft.com)です。

サンプルのドキュメントは、次のように構成されています。

## <a name="overview"></a>概要

Wide World Importers では、サンプル ポータルの概要、およびサンプルによってアドレス指定されたワークフローです。

## <a name="main-oltp-database-wideworldimporters"></a>メインの OLTP データベース WideWorldImporters

インストールして、core の構成手順は、WideWorldImporters トランザクション処理 (OLTP - オンライン トランザクション処理) と運用分析 (HTAP - ハイブリッド トランザクション/分析処理) に使用されるデータベースです。

スキーマと、WideWorldImporters データベースで使用されるテーブルの説明です。  

WideWorldImporters が主要な SQL Server 機能を活用する方法について説明します。

WideWorldImporters データベースのサンプル クエリ。

## <a name="data-warehousing-and-analytics-database-wideworldimportersdw"></a>データ ウェアハウスと分析データベース WideWorldImportersDW

インストールと OLAP の構成手順については、WideWorldImportersDW をデータベースです。

スキーマとデータ ウェアハウスと分析処理 (OLAP) のサンプル データベースをある WideWorldImportersDW データベースで使用されるテーブルの説明です。

トランザクション データベース WideWorldImporters からのデータをデータ ウェアハウス WideWorldImportersDW に移行する ETL (抽出、変換、読み込み) プロセスのワークフローです。

WideWorldImportersDW が分析処理に対して SQL Server の機能を活用する方法について説明します。

サンプルの分析クエリが WideWorldImportersDW データベースを活用することです。

## <a name="data-generation"></a>データの生成

どのように追加のデータの説明で sales を挿入するなど、サンプル データベースを作成して、現在の日付までのデータを購入します。

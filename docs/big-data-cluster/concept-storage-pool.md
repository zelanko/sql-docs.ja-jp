---
title: 記憶域プールとは
titleSuffix: SQL Server big data clusters
description: この記事では、SQL Server 2019 ビッグ データ クラスターの記憶域プールについて説明します。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 58e6f16a088d6dc6c1fc6bd32297e7bd698acbbf
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2019
ms.locfileid: "67958656"
---
# <a name="what-is-the-storage-pool-sql-server-big-data-clusters"></a>記憶域プールとは (SQL Server ビッグ データ クラスター)

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

この記事では、SQL Server 2019 ビッグ データ クラスター (プレビュー) での "*SQL Server 記憶域プール*" の役割について説明します。 以下のセクションでは、SQL 記憶域プールのアーキテクチャと機能について説明します。

## <a name="storage-pool-architecture"></a>記憶域プールのアーキテクチャ

記憶域プールは、SQL Server on Linux、Spark、および HDFS で構成される記憶域ノードで構成されます。 SQL ビッグ データ クラスター内のすべての記憶域ノードは、HDFS クラスターのメンバーです。

![記憶域プールのアーキテクチャ](media/concept-storage-pool/scale-big-data-on-demand.png)

## <a name="responsibilities"></a>役割

記憶域ノードの役割は次のとおりです。

- Spark を使用したデータ インジェスト。
- HDFS でのデータ ストレージ (Parquet 形式)。 HDFS では、HDFS データが SQL ビッグ データ クラスター内のすべての記憶域ノードに分散されるため、データの永続性も提供されます。
- HDFS と SQL Server エンドポイントを使用したデータ アクセス。

## <a name="next-steps"></a>次の手順

SQL Server ビッグ データ クラスターの詳細については、次のリソースを参照してください。

- [SQL Server 2019 ビッグ データ クラスターとは](big-data-cluster-overview.md)
- [ワークショップ: Microsoft SQL Server ビッグ データ クラスターのアーキテクチャ](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)

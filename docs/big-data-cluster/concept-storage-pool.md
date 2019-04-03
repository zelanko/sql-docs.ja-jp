---
title: 記憶域プールとは何ですか。
titleSuffix: SQL Server big data clusters
description: この記事では、SQL Server 2019 のビッグ データ クラスターで記憶域プールについて説明します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: b0775ac479b45dcb0fc0df23460b0fda0b783545
ms.sourcegitcommit: 2de5446fbc57787f18a907dd5deb02a7831ec07d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58860573"
---
# <a name="what-is-the-storage-pool-sql-server-big-data-clusters"></a>記憶域プール (SQL Server のビッグ データ クラスター) とは何ですか。

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

この記事では、の役割を説明します、 *SQL Server の記憶域プール*で SQL Server 2019 ビッグ データ クラスター (プレビュー)。 次のセクションでは、アーキテクチャと SQL の記憶域プールの機能について説明します。

## <a name="storage-pool-architecture"></a>記憶域プールのアーキテクチャ

記憶域プールは、記憶域ノードから成る Linux、Spark、および HDFS 上の SQL Server で構成されます。 SQL のビッグ データ クラスター内のすべての記憶域ノードは、HDFS クラスターのメンバーです。

![記憶域プールのアーキテクチャ](media/concept-storage-pool/scale-big-data-on-demand.png)

## <a name="responsibilities"></a>責任

記憶域ノードは責任を負います。

- Spark からデータの取り込み。
- HDFS (Parquet 形式) でデータ ストレージ。 HDFS では、HDFS のデータが SQL のビッグ データ クラスター内のすべての記憶域ノードに分散され、データの永続性も提供します。
- HDFS と SQL Server エンドポイント経由のデータ アクセス。

## <a name="next-steps"></a>次のステップ

SQL Server のビッグ データ クラスターに関する詳細については、次のリソースを参照してください。

- [SQL Server 2019 ビッグ データ クラスターとは](big-data-cluster-overview.md)
- [ワーク ショップ:Microsoft SQL Server のビッグ データ クラスターのアーキテクチャ](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)

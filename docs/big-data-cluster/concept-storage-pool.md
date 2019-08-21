---
title: 記憶域プールとは
titleSuffix: SQL Server big data clusters
description: この記事では、SQL Server 2019 ビッグ データ クラスターの記憶域プールについて説明します。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: ead6c2ceeecbdfb3466bd4475978b139a0d2ddde
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/20/2019
ms.locfileid: "69652249"
---
# <a name="what-is-the-storage-pool-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd"></a>記憶域プール ([!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]) とは

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

この記事では、 [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]の*SQL Server 記憶域プール*の役割について説明します。 以下のセクションでは、SQL 記憶域プールのアーキテクチャと機能について説明します。

## <a name="storage-pool-architecture"></a>記憶域プールのアーキテクチャ

記憶域プールは、SQL Server on Linux、Spark、および HDFS で構成される記憶域ノードで構成されます。 SQL ビッグ データ クラスター内のすべての記憶域ノードは、HDFS クラスターのメンバーです。

![記憶域プールのアーキテクチャ](media/concept-storage-pool/scale-big-data-on-demand.png)

## <a name="responsibilities"></a>役割

記憶域ノードの役割は次のとおりです。

- Spark を使用したデータ インジェスト。
- HDFS でのデータ ストレージ (Parquet 形式)。 HDFS では、HDFS データが SQL ビッグ データ クラスター内のすべての記憶域ノードに分散されるため、データの永続性も提供されます。
- HDFS と SQL Server エンドポイントを使用したデータ アクセス。

## <a name="next-steps"></a>次の手順

の[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]詳細については、次のリソースを参照してください。

- [[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]概要](big-data-cluster-overview.md)
- [ワークショップ: Microsoft [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]のアーキテクチャ](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)

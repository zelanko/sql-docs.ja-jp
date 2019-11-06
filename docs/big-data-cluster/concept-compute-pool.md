---
title: Spark コンピューティング プールとは
titleSuffix: SQL Server big data clusters
description: この記事では、[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]内のコンピューティングプールについて説明します。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 420c4705d86eb55b6b99a6cf432cb95f3b9a6694
ms.sourcegitcommit: f912c101d2939084c4ea2e9881eb98e1afa29dad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2019
ms.locfileid: "72798237"
---
# <a name="what-are-compute-pools-in-a-sql-server-big-data-cluster"></a>SQL Server ビッグ データ クラスターのコンピューティング プールとは

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

この記事では、SQL Server 2019 プレビュー ビッグ データ クラスターでの "*SQL Server コンピューティング プール*" の役割について説明します。 コンピューティング プールにより、ビッグ データ クラスター用のスケールアウト コンピューティング リソースが提供されます。 以下のセクションでは、コンピューティング プールのアーキテクチャと機能について説明します。

## <a name="compute-pool-architecture"></a>コンピューティング プールのアーキテクチャ

コンピューティング プールは、Kubernetes で実行されている 1 つまたは複数のコンピューティング ポッドで構成されます。 これらのポッドの自動化された作成と管理は、[SQL Server マスター インスタンス](concept-master-instance.md)によって調整されます。 各ポッドには、一連の基本サービスと、SQL Server データベース エンジンのインスタンスが含まれています。

## <a name="scale-out-groups"></a>スケール アウト グループ

コンピューティングプールは、HDFS、Oracle、MongoDB、Teradata などのさまざまなデータソースに対する分散クエリの PolyBase スケールアウトグループとして機能できます。 Kubernetes でコンピューティング ポッドを使用することにより、ビッグ データ クラスターで PolyBase スケールアウト グループ用のコンピューティング ポッドの作成と構成を自動化できます。

## <a name="next-steps"></a>次のステップ

[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]の詳細については、次のリソースを参照してください。

- [[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]とは何ですか。](big-data-cluster-overview.md)
- [ワークショップ: Microsoft [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] のアーキテクチャ](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)

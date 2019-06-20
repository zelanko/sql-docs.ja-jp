---
title: コンピューティング プールとは
titleSuffix: SQL Server big data clusters
description: この記事では、SQL Server 2019 ビッグ データ クラスター (プレビュー) のコンピューティング プールについて説明します。
author: rothja
ms.author: jroth
manager: jroth
ms.date: 02/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: ec1223e9255dd4dda40fb26fb9e8306bec57d926
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66800733"
---
# <a name="what-are-compute-pools-in-a-sql-server-big-data-cluster"></a>SQL Server のビッグ データ クラスター内のコンピューティング プールとは

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

この記事では、の役割を説明します。 *SQL のサーバー プールのコンピューティング*で SQL Server 2019 プレビューのビッグ データ クラスター。 コンピューティング プールは、ビッグ データ クラスターのスケール アウトのコンピューティング リソースを提供します。 次のセクションでは、アーキテクチャとコンピューティング プールの機能について説明します。

## <a name="compute-pool-architecture"></a>コンピューティング プール アーキテクチャ

Kubernetes で実行されるポッド コンピューティングまたはいずれかのコンピューティング プールが行われます。 によって調整が自動作成されるとこれらのポッドの管理、 [SQL Server のマスター インスタンス](concept-master-instance.md)します。 それぞれのポッドには、一連の基本サービスと、SQL Server データベース エンジンのインスタンスが含まれています。

## <a name="scale-out-groups"></a>スケール アウト グループ

コンピューティング プールは、HDFS、Oracle、MongoDB、Terradata などのさまざまなデータ ソース - 経由で分散クエリを PolyBase スケール アウト グループとして動作できます。 コンピューティング Kubernetes ポッドを使用して、ビッグ データ クラスターは作成とコンピューティング ポッド PolyBase スケール アウト グループの構成を自動化できます。

## <a name="next-steps"></a>次のステップ

SQL Server のビッグ データ クラスターに関する詳細については、次のリソースを参照してください。

- [SQL Server 2019 ビッグ データ クラスターとは](big-data-cluster-overview.md)
- [ワーク ショップ:Microsoft SQL Server のビッグ データ クラスターのアーキテクチャ](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)

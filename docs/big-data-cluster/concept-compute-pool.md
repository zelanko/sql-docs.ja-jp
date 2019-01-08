---
title: コンピューティング プールとは
titleSuffix: SQL Server 2019 big data clusters
description: この記事では、SQL Server 2019 ビッグ データ クラスター (プレビュー) のコンピューティング プールについて説明します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/07/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: seodec18
ms.openlocfilehash: f1e725580c98585ee86b401c0e8c12ea143cdab1
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2018
ms.locfileid: "53207721"
---
# <a name="what-are-compute-pools-in-a-sql-server-2019-big-data-cluster"></a>SQL Server 2019 のビッグ データ クラスター内のコンピューティング プールとは

この記事では、の役割を説明します。 *SQL のサーバー プールのコンピューティング*で SQL Server 2019 プレビューのビッグ データ クラスター。 コンピューティング プールは、ビッグ データ クラスターのスケール アウトのコンピューティング リソースを提供します。 次のセクションでは、アーキテクチャとコンピューティング プールの機能について説明します。

## <a name="compute-pool-architecture"></a>コンピューティング プール アーキテクチャ

Kubernetes で実行されるポッド コンピューティングまたはいずれかのコンピューティング プールが行われます。 によって調整が自動作成されるとこれらのポッドの管理、 [SQL Server のマスター インスタンス](concept-master-instance.md)します。 それぞれのポッドには、一連の基本サービスと、SQL Server データベース エンジンのインスタンスが含まれています。

> [!NOTE]
> CTP 2.2 は、クラスターあたり 1 つのコンピューティング プールのみをサポートします。

## <a name="scale-out-groups"></a>スケール アウト グループ

コンピューティング プールは、HDFS、Oracle、MongoDB、Terradata などのさまざまなデータ ソース - 経由で分散クエリを PolyBase スケール アウト グループとして動作できます。 コンピューティング Kubernetes ポッドを使用して、ビッグ データ クラスターは作成とコンピューティング ポッド PolyBase スケール アウト グループの構成を自動化できます。

## <a name="next-steps"></a>次の手順

SQL Server のビッグ データ クラスターに関する詳細については、次の概要を参照してください。

- [SQL Server 2019 ビッグ データ クラスターとは](big-data-cluster-overview.md)

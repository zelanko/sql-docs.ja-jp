---
title: コンピューティング プールとは
titleSuffix: SQL Server 2019 big data clusters
description: この記事では、SQL Server 2019 ビッグ データ クラスター (プレビュー) のコンピューティング プールについて説明します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 272f10cfed8f7cd1b07633b81642323a8c74b6d7
ms.sourcegitcommit: 56fb7b648adae2c7b81bd969de067af1a2b54180
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/02/2019
ms.locfileid: "57227134"
---
# <a name="what-are-compute-pools-in-a-sql-server-2019-big-data-cluster"></a>SQL Server 2019 のビッグ データ クラスター内のコンピューティング プールとは

この記事では、の役割を説明します。 *SQL のサーバー プールのコンピューティング*で SQL Server 2019 プレビューのビッグ データ クラスター。 コンピューティング プールは、ビッグ データ クラスターのスケール アウトのコンピューティング リソースを提供します。 次のセクションでは、アーキテクチャとコンピューティング プールの機能について説明します。

## <a name="compute-pool-architecture"></a>コンピューティング プール アーキテクチャ

Kubernetes で実行されるポッド コンピューティングまたはいずれかのコンピューティング プールが行われます。 によって調整が自動作成されるとこれらのポッドの管理、 [SQL Server のマスター インスタンス](concept-master-instance.md)します。 それぞれのポッドには、一連の基本サービスと、SQL Server データベース エンジンのインスタンスが含まれています。

## <a name="scale-out-groups"></a>スケール アウト グループ

コンピューティング プールは、HDFS、Oracle、MongoDB、Terradata などのさまざまなデータ ソース - 経由で分散クエリを PolyBase スケール アウト グループとして動作できます。 コンピューティング Kubernetes ポッドを使用して、ビッグ データ クラスターは作成とコンピューティング ポッド PolyBase スケール アウト グループの構成を自動化できます。

## <a name="next-steps"></a>次のステップ

SQL Server のビッグ データ クラスターに関する詳細については、次の概要を参照してください。

- [SQL Server 2019 ビッグ データ クラスターとは](big-data-cluster-overview.md)

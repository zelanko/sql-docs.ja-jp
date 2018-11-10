---
title: SQL ビッグ データ クラスター コンピューティング プールとは何ですか。 | Microsoft Docs
description: この記事では、SQL Server 2019 ビッグ データ クラスターでコンピューティング プールについて説明します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 11/06/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 6aa73c5881a4b6a17e190c26c15f97b3d8c79c14
ms.sourcegitcommit: cb73d60db8df15bf929ca17c1576cf1c4dca1780
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2018
ms.locfileid: "51221798"
---
# <a name="what-is-a-sql-big-data-clusters-compute-pool"></a>SQL ビッグ データ クラスター コンピューティング プールとは何ですか。

この記事では、の役割を説明します。 *SQL のサーバー プールのコンピューティング*で SQL Server 2019 プレビューのビッグ データ クラスター。 コンピューティング プールは、ビッグ データ クラスターのスケール アウトのコンピューティング リソースを提供します。 次のセクションでは、アーキテクチャとコンピューティング プールの機能について説明します。

## <a name="compute-pool-architecture"></a>コンピューティング プール アーキテクチャ

Kubernetes で実行されるポッド コンピューティングまたはいずれかのコンピューティング プールが行われます。 によって調整が自動作成されるとこれらのポッドの管理、 [SQL Server のマスター インスタンス](concept-master-instance.md)します。 それぞれのポッドには、一連の基本サービスと、SQL Server データベース エンジンのインスタンスが含まれています。

> [!NOTE]
> CTP 2.1 は、クラスターあたり 1 つのコンピューティング プールのみをサポートします。

## <a name="scale-out-groups"></a>スケール アウト グループ

コンピューティング プールは、HDFS、Oracle、MongoDB、Terradata などのさまざまなデータ ソース - 経由で分散クエリを PolyBase スケール アウト グループとして動作できます。 コンピューティング Kubernetes ポッドを使用して、ビッグ データ クラスターは作成とコンピューティング ポッド PolyBase スケール アウト グループの構成を自動化できます。

## <a name="next-steps"></a>次の手順

SQL Server のビッグ データ クラスターに関する詳細については、次の概要を参照してください。

- [SQL Server 2019 ビッグ データ クラスターとは](big-data-cluster-overview.md)

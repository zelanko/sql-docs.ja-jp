---
title: SQL ビッグ データ クラスター コンピューティング プールとは何ですか。 | Microsoft Docs
description: この記事では、SQL Server 2019 ビッグ データ クラスターでコンピューティング プールについて説明します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/01/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 67f13687bf55a9e267582a0749043c51d2e2b3bf
ms.sourcegitcommit: 182d77997133a6e4ee71e7a64b4eed6609da0fba
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2018
ms.locfileid: "50050800"
---
# <a name="what-is-a-sql-big-data-clusters-compute-pool"></a>SQL ビッグ データ クラスター コンピューティング プールとは何ですか。

この記事では、の役割を説明します。 *SQL のサーバー プールのコンピューティング*で SQL Server 2019 プレビューのビッグ データ クラスター。 コンピューティング プールは、ビッグ データ クラスターのスケール アウトのコンピューティング リソースを提供します。 次のセクションでは、アーキテクチャとコンピューティング プールの機能について説明します。

## <a name="compute-pool-architecture"></a>コンピューティング プール アーキテクチャ

Kubernetes で実行されるポッド コンピューティングまたはいずれかのコンピューティング プールが行われます。 によって調整が自動作成されるとこれらのポッドの管理、 [SQL Server のマスター インスタンス](concept-master-instance.md)します。 それぞれのポッドには、一連の基本サービスと、SQL Server データベース エンジンのインスタンスが含まれています。

> [!NOTE]
> CTP 2.0 は、クラスターあたり 1 つのコンピューティング プールのみをサポートします。

## <a name="scale-out-groups"></a>スケール アウト グループ

コンピューティング プールは、HDFS、Oracle、MongoDB、Terradata などのさまざまなデータ ソース - 経由で分散クエリを PolyBase スケール アウト グループとして動作できます。 コンピューティング Kubernetes ポッドを使用して、ビッグ データ クラスターは作成とコンピューティング ポッド PolyBase スケール アウト グループの構成を自動化できます。

## <a name="next-steps"></a>次の手順

SQL Server のビッグ データ クラスターに関する詳細については、次の概要を参照してください。

- [SQL Server 2019 ビッグ データ クラスターとは](big-data-cluster-overview.md)

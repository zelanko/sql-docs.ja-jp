---
title: データのプールとは
titleSuffix: SQL Server big data clusters
description: この記事では、SQL Server 2019 のビッグ データ クラスター内のデータ プールについて説明します。
author: rothja
ms.author: jroth
manager: jroth
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: ba296a504ae4a6656941c408e7b7a0c96a83c97d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66783087"
---
# <a name="what-are-data-pools-in-a-sql-server-big-data-cluster"></a>SQL Server のビッグ データ クラスター内のデータ プールとは

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

この記事では、の役割を説明します。 *SQL Server のデータ プール*で SQL Server 2019 ビッグ データ クラスター (プレビュー)。 次のセクションでは、アーキテクチャと SQL のデータ プールの機能について説明します。

## <a name="data-pool-architecture"></a>プールのデータ アーキテクチャ

データ プールは、1 つまたは複数の SQL Server のデータ プール インスタンスで構成されます。 SQL データ プールのインスタンスは、クラスターの永続的な SQL Server の記憶域を提供します。 データ プールは、SQL クエリまたは Spark ジョブからのデータの取り込みに使用されます。 パフォーマンスを向上させる大規模なデータ セット全体を提供するには、データ プール内のデータは、メンバー SQL データ プール インスタンスをシャードに分散されます。

## <a name="scale-out-data-marts"></a>スケール アウト データ マート

データ プールは、スケール アウト データ マート、データ プールに複数のソースから外部のデータが取り込まれた場所の作成を有効にします。 データはデータ プール インスタンス間で分散型なので、精選されたデータに対する並列クエリはより効率的です。

![スケール アウト データ マート](media/concept-data-pool/data-virtualization-improvements.png)

## <a name="next-steps"></a>次のステップ

SQL Server のビッグ データ クラスターに関する詳細については、次のリソースを参照してください。

- [SQL Server 2019 ビッグ データ クラスターとは](big-data-cluster-overview.md)
- [ワーク ショップ:Microsoft SQL Server のビッグ データ クラスターのアーキテクチャ](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)

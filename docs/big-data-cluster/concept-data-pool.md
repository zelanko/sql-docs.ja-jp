---
title: データのプールとは
titleSuffix: SQL Server 2019 big data clusters
description: この記事では、SQL Server 2019 のビッグ データ クラスター内のデータ プールについて説明します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: c3df07da100bf0bbfc0b2238cb4154b4c3a363e3
ms.sourcegitcommit: 202ef5b24ed6765c7aaada9c2f4443372064bd60
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/12/2019
ms.locfileid: "54241613"
---
# <a name="what-are-data-pools-in-a-sql-server-2019-big-data-cluster"></a>SQL Server 2019 のビッグ データ クラスター内のデータ プールとは

この記事では、の役割を説明します。 *SQL Server のデータ プール*で SQL Server 2019 ビッグ データ クラスター (プレビュー)。 次のセクションでは、アーキテクチャと SQL のデータ プールの機能について説明します。

## <a name="data-pool-architecture"></a>プールのデータ アーキテクチャ

データ プールは、1 つまたは複数の SQL Server のデータ プール インスタンスで構成されます。 SQL データ プールのインスタンスは、クラスターの永続的な SQL Server の記憶域を提供します。 データ プールは、SQL クエリまたは Spark ジョブからのデータの取り込みに使用されます。 パフォーマンスを向上させる大規模なデータ セット全体を提供するには、データ プール内のデータは、メンバー SQL データ プール インスタンスをシャードに分散されます。

## <a name="scale-out-data-marts"></a>スケール アウト データ マート

データ プールは、スケール アウト データ マート、データ プールに複数のソースから外部のデータが取り込まれた場所の作成を有効にします。 データはデータ プール インスタンス間で分散型なので、精選されたデータに対する並列クエリはより効率的です。

![スケール アウト データ マート](media/concept-data-pool/data-virtualization-improvements.png)

## <a name="next-steps"></a>次の手順

SQL Server のビッグ データ クラスターに関する詳細については、次の概要を参照してください。

- [SQL Server 2019 ビッグ データ クラスターとは](big-data-cluster-overview.md)

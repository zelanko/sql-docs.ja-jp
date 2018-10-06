---
title: SQL のビッグ データ クラスターのデータ プールとは何ですか。 | Microsoft Docs
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/01/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 3a75f47148ff59d58d0d0d1397ba445b064c028f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48796301"
---
# <a name="what-is-a-sql-big-data-clusters-data-pool"></a>SQL のビッグ データ クラスターのデータ プールとは何ですか。

この記事では、の役割を説明します。 *SQL Server のデータ プール*SQL Server の 2019 でビッグ データ クラスターをプレビューします。 次のセクションでは、アーキテクチャと SQL のデータ プールの機能について説明します。

## <a name="data-pool-architecture"></a>プールのデータ アーキテクチャ

データ プールは、1 つまたは複数の SQL Server のデータ プール インスタンスで構成されます。 SQL データ プールのインスタンスは、クラスターの永続的な SQL Server の記憶域を提供します。 データ プールは、SQL クエリまたは Spark ジョブからのデータの取り込みに使用されます。 パフォーマンスを向上させる大規模なデータ セット全体を提供するには、データ プール内のデータは、メンバー SQL データ プール インスタンスをシャードに分散されます。

## <a name="scale-out-data-marts"></a>スケール アウト データ マート

データ プールは、スケール アウト データ マート、データ プールに複数のソースから外部のデータが取り込まれた場所の作成を有効にします。 データはデータ プール インスタンス間で分散型なので、精選されたデータに対する並列クエリはより効率的です。

![スケール アウト データ マート](media/concept-data-pool/data-virtualization-improvements.png)

## <a name="next-steps"></a>次の手順

SQL Server のビッグ データ クラスターに関する詳細については、次の概要を参照してください。

- [SQL Server 2019 ビッグ データ クラスターとは何ですか。](big-data-cluster-overview.md)

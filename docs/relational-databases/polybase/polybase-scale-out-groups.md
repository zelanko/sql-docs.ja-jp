---
title: PolyBase スケールアウト グループ | Microsoft Docs
ms.custom: ''
ms.date: 04/23/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: polybase
ms.topic: conceptual
helpviewer_keywords:
- PolyBase
- PolyBase, scale-out groups
- scale-out PolyBase
ms.assetid: c7810135-4d63-4161-93ab-0e75e9d10ab5
author: rothja
ms.author: jroth
manager: craigg
monikerRange: '>= sql-server-2016 || =sqlallproducts-allversions'
ms.openlocfilehash: 6a07e7edf54e4cf83e33a59ae1e3a98d033cce8d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "64774876"
---
# <a name="polybase-scale-out-groups"></a>PolyBase スケールアウト グループ

[!INCLUDE[appliesto-ss-xxxx-asdw-pdw-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

PolyBase を使用するスタンドアロンの SQL Server インスタンスは、Hadoop または Azure BLOB ストレージの大量のデータ セットを処理する場合、パフォーマンス ボトルネックになる可能性があります。 PolyBase グループ機能では、Hadoop や Azure BLOB ストレージなどの外部データ ソースからの大量のデータ セットを、クエリ パフォーマンスの向上のためにスケールアウト形式で処理するために、SQL Server インスタンス クラスターを作成することができます。 これで、ワークロードで要求されるパフォーマンスを満たすように、お使いの SQL Server のコンピューティングをスケーリングできます。 SQL Server インスタンスのグループの PolyBase スケールアウト グループでは、並列処理アーキテクチャで大規模な外部データ セットを処理できます。 このグループに、SQL Server インスタンスを追加するほど、データの読み込みおよびクエリのパフォーマンスは線形に増加します。 
  
「 [PolyBase の概要](../../relational-databases/polybase/get-started-with-polybase.md) 」および「 [PolyBase ガイド](../../relational-databases/polybase/polybase-guide.md)」を参照してください。
  
![PolyBase スケールアウト グループ](../../relational-databases/polybase/media/polybase-scale-out-groups.png "PolyBase スケールアウト グループ")  
  
## <a name="head-node"></a>ヘッド ノード  

ヘッド ノードには、PolyBase クエリの送信先の SQL Server インスタンスが含まれています。 各 PolyBase グループは、ヘッド ノードを 1 つだけ保持できます。 ヘッド ノードは、SQL Server インスタンス上の SQL データベース エンジン、PolyBase エンジン、および PolyBase データ移動サービスの論理グループです。
  
## <a name="compute-node"></a>コンピューティング ノード  

コンピューティング ノードには、外部データに対するスケールアウト クエリ処理を支援する SQL Server インスタンスが含まれています。 コンピューティング ノードは、SQL Server インスタンス上の SQL Server と PolyBase データ移動サービスの論理グループです。 PolyBase グループは、複数のコンピューティング ノードを保持できます。 ヘッド ノードとコンピューティング ノードはすべて、同じバージョンの SQL Server を実行する必要があります。

## <a name="scale-out-reads"></a>スケールアウト読み取り

外部の SQL Server に対してクエリを実行する場合、Oracle インスタンスまたは Teradata インスタンス、パーティション分割されたテーブルには、読み取りスケールアウトのメリットがあります。 PolyBase スケールアウト グループの各ノードは、外部データを読み取るのに、最大 8 つのリーダーにスピンできます。 そして各リーダーには、読み取る外部テーブルのパーティションが 1 つ割り当てられます。 

たとえば、SQL Server の外部テーブルに月ごとに 12 のパーティションがあり、3 つのノードの PolyBase スケールアウト グループがあるとします。各ノードは、12 のそれぞれのパーティションの処理に 4 つの PolyBase リーダーを使用します。 これを次の図で示します。 

> [!NOTE]
>  これは Hadoop を介したスケールアウト読み取りとは異なります。 

![PolyBase スケールアウト グループ](../../relational-databases/polybase/media/polybase-scale-out-groups2.png "PolyBase スケールアウト グループ")
  
## <a name="distributed-query-processing"></a>分散クエリ処理  

PolyBase クエリは、ヘッド ノード上の SQL Server に送信されます。 外部テーブルを参照するクエリの一部は、PolyBase エンジンに渡されます。
  
PolyBase エンジンは、PolyBase クエリの背後にある重要なコンポーネントです。 外部データに対するクエリを解析し、クエリ プランを生成して、作業を実行するためにコンピューティング ノード上のデータ移動サービスに配布します。 作業が完了すると、コンピューティング ノードから結果を受信し、この結果を処理してクライアントに返すために SQL Server に送信します。
  
PolyBase データ移動サービスは、PolyBase エンジンから指示を受信し、HDFS と SQL Server の間、およびヘッド ノードとコンピューティング ノード上の SQL Server インスタンス間でデータを転送します。
  
## <a name="editions-availability"></a>エディションの可用性  

SQL Server をセットアップしたら、インスタンスをヘッド ノードとコンピューティング ノードのどちらかとして指定できます。 指定できるノードは、実行されている SQL Server PolyBase のバージョンによって異なります。 Enterprise Edition インストールでは、インスタンスをヘッド ノードとコンピューティング ノードのどちらかとして指定できます。 Standard Edition では、インスタンスをコンピューティング ノードとしてのみ指定できます。

## <a name="next-steps"></a>次の手順

PolyBase スケールアウト グループを構成するには、次のガイドを参照してください。

[Windows で PolyBase スケールアウト グループを改善する](configure-scale-out-groups-windows.md)

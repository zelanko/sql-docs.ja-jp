---
title: Resource Governor を使用した Python と R のワークロードの管理
description: Resource Governor を使用して、SQL Server Machine Learning Services での Python および R のワークロードに対する CPU、物理 IO、およびメモリリソースの割り当てを管理する方法について説明します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/02/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 9000ab8bb15e8f9910b8b780aa38d134fa984032
ms.sourcegitcommit: af5e1f74a8c1171afe759a4a8ff2fccb5295270a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2019
ms.locfileid: "71823542"
---
# <a name="manage-python-and-r-workloads-with-resource-governor-in-sql-server-machine-learning-services"></a>SQL Server で Resource Governor を使用した Python と R のワークロードの管理 Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

[Resource Governor](../../relational-databases/resource-governor/resource-governor.md)を使用して、SQL Server Machine Learning Services での Python および R のワークロードに対する CPU、物理 IO、およびメモリリソースの割り当てを管理する方法について説明します。

Python および R の機械学習アルゴリズムは、通常、多くのコンピューティング処理を要するものです。 ワークロードの優先度によっては、Machine Learning Services に使用できるリソースを増減することが必要になる場合があります。

一般的な情報については、「 [Resource Governor](../../relational-databases/resource-governor/resource-governor.md)」を参照してください。

> [!NOTE] 
> Resource Governor は Enterprise Edition の機能です。

## <a name="default-allocations"></a>既定の割り当て

既定では、machine learning の外部スクリプトランタイムは、合計マシンメモリの 20% 以下に制限されています。 システムによって異なりますが、一般的に、モデルのトレーニングや多数のデータ行の予測などの本格的な機械学習タスクでは、この制限が不十分である可能性があります。 

## <a name="manage-resources-with-resource-governor"></a>Resource Governor を使用したリソースの管理
 
既定では、外部プロセスでは、ローカルサーバー上の合計ホストメモリの 20% までが使用されます。 既定のリソースプールを変更して、サーバー全体の変更を加えることができます。 R と Python のプロセスでは、外部プロセスで使用できるようにする容量を利用できます。

または、関連するワークロードグループと分類子を使用してカスタム**外部リソースプール**を作成し、特定のプログラム、ホスト、またはその他の条件によって送信された要求のリソース割り当てを決定することもできます。 外部リソースプールは、で導入されたリソースプール[!INCLUDE[sssql15-md](../../includes/sssql15-md.md)]の一種であり、データベースエンジンの外部の R および Python プロセスを管理するのに役立ちます。

1. [リソースガバナンスを有効にする](https://docs.microsoft.com/sql/relational-databases/resource-governor/enable-resource-governor)(既定ではオフになっています)。

2. [[外部リソースプールの作成](https://docs.microsoft.com/sql/t-sql/statements/create-external-resource-pool-transact-sql)] を実行してリソースプールを作成および構成し、その後に[ALTER RESOURCE GOVERNOR](https://docs.microsoft.com/sql/t-sql/statements/alter-resource-governor-transact-sql)を実行して実装します。

3. トレーニングとスコア付けなど、粒度の細かい割り当て用のワークロードグループを作成します。

4. 外部処理の呼び出しをインターセプトする分類器を作成します。

5. 作成したオブジェクトを使用して、クエリとプロシージャを実行します。

チュートリアルについては、「[外部 R および Python スクリプト用のリソースプールを作成する方法](../../advanced-analytics/r/how-to-create-a-resource-pool-for-r.md)」を参照してください。

用語と一般的な概念の概要については、「 [Resource Governor リソースプール](../../relational-databases/resource-governor/resource-governor-resource-pool.md)」を参照してください。

## <a name="processes-under-resource-governance"></a>リソースガバナンスの下にあるプロセス
  
 *外部リソースプール*を使用すると、データベースエンジンインスタンスで次の実行可能ファイルによって使用されるリソースを管理できます。

+ ローカルで SQL Server から、またはリモートの計算コンテキストとして SQL Server を使用してリモートで呼び出された場合、rterm .exe
+ SQL Server からローカルで呼び出された場合、またはリモートの計算コンテキストとして SQL Server を使用してリモートで呼び出された場合
+ BxlServer.exe およびサテライト プロセス
+ Python ランチャーなどのスタートパッドによって起動されるサテライトプロセス
  
> [!NOTE]
> Resource Governor を使用したスタートパッドサービスのダイレクト管理はサポートされていません。 スタートパッドは、Microsoft によって提供されるランチャーのみをホストできる信頼されたサービスです。 信頼できるランチャーは、リソースが過剰に消費されるのを防ぐために明示的に構成されます。
  
## <a name="next-steps"></a>次の手順

+ [Machine Learning 用のリソース プールの作成](create-external-resource-pool.md)
+ [リソースプールの Resource Governor](../../relational-databases/resource-governor/resource-governor-resource-pool.md)

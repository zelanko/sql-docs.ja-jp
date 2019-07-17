---
title: R と Python スクリプトの実行 - SQL Server Machine Learning のリソース ガバナンス
description: SQL Server データベース エンジンのインスタンス上の R と Python のワークロードの RAM メモリ、CPU、および IO を割り当てます。
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/10/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: e6063f8367e5b91e7e935d6f92515a6dd452dc56
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67963135"
---
# <a name="resource-governance-for-machine-learning-in-sql-server"></a>SQL Server での machine learning のリソース ガバナンス
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

データ サイエンスと機械学習アルゴリズムが計算負荷ではありません。 ワークロードの優先度に応じてデータ サイエンス、使用可能なリソースを大きく必要があります。 または減少の場合、R と Python スクリプトの実行をリソースには、同時に実行されているその他のサービスのパフォーマンスが損なわれます。 

複数のワークロード間でシステム リソースの配布を再調整する必要がある、ときに使用できます[リソース ガバナー](../../relational-databases/resource-governor/resource-governor.md) CPU、物理 IO、および R と Python の外部ランタイムで使用されるメモリ リソースを割り当てます。 リソースの割り当てをシフトする場合は、他のワークロードやサービス用に予約するメモリの量を減らすために必要であることに注意してください。 

> [!NOTE] 
> リソース ガバナーは、Enterprise Edition の機能です。

## <a name="default-allocations"></a>既定の割り当て

既定では、machine learning の外部スクリプトのランタイムは、合計マシン メモリの 20% 以下に制限されます。 システムに依存は、一般に、この制限のモデルのトレーニングや多数のデータ行に基づく予測などの深刻な機械学習のタスクが不足します。 

## <a name="use-resource-governor-to-control-resourcing"></a>リソース ガバナーを使用してリソースの割り当てを制御するには
 
既定では、外部プロセスは、ローカル サーバー上のホストのメモリ合計の最大 20% を使用します。 外部プロセスで使用できるようにする Python プロセスがどのような容量を利用して R を使用した、サーバー全体の変更を行う既定のリソース プールを変更できます。

カスタムを構築する代わりに、*外部リソース プール*、特定のプログラム、ホスト、またはその他の条件から送信された要求のリソースの割り当てを判断するには、関連付けられているワークロード グループおよび分類子を使用します。指定します。 外部リソース プールで導入されたリソースの種類は、[!INCLUDE[sssql15-md](../../includes/sssql15-md.md)]データベース エンジンの外部に R と Python のプロセスを管理するためにします。

1. [リソース ガバナンスを有効にする](https://docs.microsoft.com/sql/relational-databases/resource-governor/enable-resource-governor)(既定ではオフ)。

2. 実行[CREATE EXTERNAL RESOURCE POOL](https://docs.microsoft.com/sql/t-sql/statements/create-external-resource-pool-transact-sql)を作成および構成後に、リソース プール[ALTER RESOURCE GOVERNOR](https://docs.microsoft.com/sql/t-sql/statements/alter-resource-governor-transact-sql)それを実装します。

3. たとえば間でトレーニングおよびスコア付けの詳細な割り当てのワークロード グループを作成します。

4. 外部の処理のための呼び出しをインターセプトする分類器を作成します。

5. クエリを実行し、作成したプロシージャは、オブジェクトを使用します。

チュートリアルについては、次を参照してください。[外部の R と Python スクリプト用のリソース プールを作成する方法](../../advanced-analytics/r/how-to-create-a-resource-pool-for-r.md)詳しい手順についてはします。

用語と一般的な概念の概要については、次を参照してください。[リソース ガバナー リソース プール](../../relational-databases/resource-governor/resource-governor-resource-pool.md)します。

## <a name="processes-under-resource-governance"></a>プロセスでリソース ガバナンス
  
 使用することができます、*外部リソース プール*データベース エンジンのインスタンスで次の実行可能ファイルによって使用されるリソースを管理します。

+ SQL Server からローカルで呼び出された、または SQL Server リモート計算コンテキストとして使用してリモートで呼び出されたときに、Rterm.exe
+ SQL Server からローカルで呼び出された、または SQL Server リモート計算コンテキストとして使用してリモートで呼び出されたときに、Python.exe
+ BxlServer.exe およびサテライト プロセス
+ PythonLauncher.dll などのスタート パッドで起動されたサテライト プロセス
  
> [!NOTE]
> リソース ガバナーを使用して、スタート パッド サービスのダイレクト管理がサポートされていません。 スタート パッドは、Microsoft によって提供されるホスト ランチャーのみを信頼できるサービスです。 信頼済みランチャーは、リソースを過剰に消費しないように明示的に構成されます。
  
## <a name="see-also"></a>関連項目

+ [Machine learning の統合を管理します。](../r/managing-and-monitoring-r-solutions.md)
+ [Machine Learning 用のリソース プールの作成](../r/how-to-create-a-resource-pool-for-r.md)
+ [リソース ガバナー リソース プール](../../relational-databases/resource-governor/resource-governor-resource-pool.md)

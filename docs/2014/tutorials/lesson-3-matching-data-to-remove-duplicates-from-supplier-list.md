---
title: 'レッスン 3: 削除するデータを照合して仕入先の一覧から重複 |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 059170b6-d62e-4b28-9451-99a0cc7e1f5f
caps.latest.revision: 6
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f244dc7d62f19967aae7ee3bc32a634008fcc94e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37265792"
---
# <a name="lesson-3-matching-data-to-remove-duplicates-from-supplier-list"></a>レッスン 3: データを照合して仕入先の一覧から重複を削除する
  照合アクティビティを実行するためにナレッジ ベースを準備するには、ナレッジ ベースで照合ポリシーを作成します。 ナレッジ ベースで作成できる照合ポリシーは 1 つだけですが、 そのポリシーは 1 つ以上の照合ルールで構成されます。 ルールは、照合プロセスに関連するドメインを特定し、一致率を割り当てるときの各ドメイン値の重みを指定します。 このルールでは、完全に一致するドメイン値だけを一致と見なすか、類似性のレベルが指定した値を超えるドメイン値も一致と見なすかを指定します。 また、ドメインが照合プロセスで一致する必要があるかどうかも指定します。 各ルールを個別にテストし、サンプル データに対してポリシー全体をテストできます。 テストのプロセスには、照合スコアがより大きいレコードが表示されます、**最小レコード スコア**クラスター (グループ) の DQS 構成で指定されたしきい値。 プレビュー後も、満足できるまでポリシーのルールを調整できます。  
  
 ポリシーを定義した後、データ品質プロジェクトを作成して照合アクティビティを実行します。 照合プロジェクトでは、評価するデータ ソースに対して照合ポリシーの照合ルールを適用し、 任意の 2 つの行が一致する確率を評価します。 DQS で照合分析を実行すると、一致と見なされたレコードのクラスターが作成され、 DQS では、いずれかのレコードがピボット レコードとしてランダムに識別されます。 クラスターに対する適切な一致ではないレコードを確認および拒否できます。 参照してください[照合ポリシーの作成](http://msdn.microsoft.com/library/hh270290.aspx)詳細についてはトピック。  
  
 このレッスンでは、照合アクティビティを実行して、仕入先の一覧から重複するものを削除します。 まず、1 つのルールを含む照合ポリシーを作成し、仕入先の一覧の重複部分を識別して、ポリシーをナレッジ ベースにパブリッシュします。 次に、照合するデータ品質プロジェクトを作成および実行します。 最後に、照合アクティビティから、後でマスター データ サービス (MDS) にデータをアップロードする場合に使用する Excel ファイルに結果をエクスポートします。  
  
## <a name="next-step"></a>次の手順  
 [タスク 1: 照合ポリシーを定義する](../../2014/tutorials/task-1-defining-a-matching-policy.md)  
  
  

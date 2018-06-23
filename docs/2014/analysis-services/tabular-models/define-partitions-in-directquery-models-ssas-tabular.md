---
title: パーティションと DirectQuery モード (SSAS テーブル) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5f179ba9-6efb-46ae-90e5-945bbfddb719
caps.latest.revision: 10
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 6153a5975dd342bfabb00b7f964ee04d6941a363
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36173790"
---
# <a name="partitions-and-directquery-mode-ssas-tabular"></a>パーティションと DirectQuery モード (SSAS テーブル)
  ここでは、DirectQuery モデルでのパーティションの使用方法について説明します。 テーブル モデルでのパーティションに関する一般的な情報については、「[パーティション (SSAS テーブル)](partitions-ssas-tabular.md)」を参照してください。  
  
 パーティションに関する情報の表示や、使用されるパーティションを変更する方法に関する手順については、次を参照してください。 [DirectQuery パーティションの変更&#40;SSAS 表形式&#41;](../change-the-directquery-partition-ssas-tabular.md)です。  
  
## <a name="using-partitions-in-directquery-mode"></a>DirectQuery モードでのパーティションの使用  
 テーブルごとに、DirectQuery データ ソースとして使用する 1 つのパーティションを指定する必要があります。  複数のパーティションがある場合は、モデルを切り替えて DirectQuery モードを有効にすると、テーブル内に作成された最初のパーティションに DirectQuery パーティションのフラグが既定で設定されます。 この設定は、後で [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]のパーティション マネージャーを使用して変更できます。  
  
 DirectQuery モードで 1 つのパーティションのみ許可するのはなぜでしょうか。  
  
 テーブル モデルでは、OLAP モデルの場合と同様に、テーブルのパーティションが SQL クエリによって定義されます。 パーティションの定義を作成する開発者は、パーティションが重ならないようにする必要があります。 Analysis Services では、レコードが 1 つのパーティションに属しているか、複数のパーティションに属しているかはチェックされません。  
  
 キャッシュされたテーブル モデル内のパーティションは同じように動作します。 インメモリ モデルを使用する場合は、キャッシュがアクセスされるときに、DAX 数式がパーティションごとに評価され、結果が結合されます。 一方、テーブル モデルが DirectQuery モードを使用する場合は、複数のパーティションを評価して結果を結合し、リレーショナル データ ストアに送信する SQL ステートメントに変換することは不可能です。 この操作を行うと、パフォーマンスが許容できないほど低下し、集計される結果が不正確になる可能性があります。  
  
 したがって、DirectQuery モードで応答されたクエリに対して、サーバーは DirectQuery アクセスのプライマリ パーティションとしてマークされた単一のパーティション ( *DirectQuery パーティション*) を使用します。  このパーティションの定義で指定された SQL クエリは、DirectQuery モードでのクエリの応答に使用できるデータの完全なセットを定義します。  
  
 パーティションを明示的に定義していない場合、エンジンは単純にリレーショナル データ ソース全体に SQL クエリを発行し、DAX 数式で指定されたセットベース操作を実行してクエリ結果を返します。  
  
 テーブルに複数のパーティションがあり、1 つのパーティションを DirectQuery パーティションとして選択した場合、既定では他のすべてのパーティションはメモリ内でのみ使用されるように自動的にマークされます。  
  
## <a name="partitions-in-cached-models-and-in-directquery-models"></a>キャッシュ モデルと DirectQuery モデルのパーティション  
 DirectQuery パーティションを構成するときは、パーティションの処理オプションを指定する必要があります。  
  
 DirectQuery パーティションには 2 つの処理オプションがあります。 このプロパティを設定するには、 **の** [パーティション マネージャー] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用して、 **[処理オプション]** プロパティを選択します。 次の表にこのプロパティの値を示し、接続文字列の [DirectQueryUsage] プロパティと組み合わせた場合の各値の影響について説明します。  
  
|**DirectQueryUsage**プロパティ|**[処理オプション]** プロパティ|注|  
|-----------------------------------|------------------------------------|-----------|  
|DirectQuery|[このパーティションを処理しない]|モデルが DirectQuery のみを使用している場合、処理は必要ありません。<br /><br /> ハイブリッド モデルでは、DirectQuery パーティションが処理されないように構成できます。 たとえば、非常に大きなデータ セットを操作する場合に、キャッシュに結果のすべてを追加する必要がなければ、DirectQuery パーティションにテーブル内の他のパーティションに対する結果の和集合を含めて、和集合を処理しないことを指定できます。 リレーショナル ソースに対するクエリは影響を受けず、キャッシュ データに対するクエリは他のパーティションからのデータを結合します。|  
|InMemory (DirectQuery あり)|[パーティションを処理できる]|モデルがハイブリッド モードを使用している場合は、メモリ内に対するクエリと DirectQuery データ ソースに対するクエリで同じパーティションを使用する必要があります。|  
  
## <a name="see-also"></a>参照  
 [パーティション&#40;SSAS 表形式&#41;](partitions-ssas-tabular.md)  
  
  
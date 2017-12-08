---
title: "パーティションと DirectQuery モデル (SSAS テーブル) での定義 |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5f179ba9-6efb-46ae-90e5-945bbfddb719
caps.latest.revision: "15"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 0b680877b5ac907e143222b029d5d717145d3c2a
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="define-partitions-in-directquery-models"></a>パーティションと DirectQuery モデルの定義

[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  ここでは、DirectQuery モデルでのパーティションの使用方法について説明します。 テーブル モデルでのパーティションに関する一般的な情報については、「 [パーティション (SSAS テーブル)](../../analysis-services/tabular-models/partitions-ssas-tabular.md)」を参照してください。  
  
> [!NOTE]  
>  1 つのテーブルに対して複数のパーティションを設定することができますが、DirectQuery モードでは、クエリの実行に使用できるのはそのうちの 1 つのみです。 この単一のパーティションの要件は、すべての互換性レベルの DirectQuery モデルに適用されます。  
  
## <a name="using-partitions-in-directquery-mode"></a>DirectQuery モードでのパーティションの使用  
 テーブルごとに、DirectQuery データ ソースとして使用する 1 つのパーティションを指定する必要があります。  複数のパーティションがある場合は、モデルを切り替えて DirectQuery モードを有効にすると、テーブル内に作成された最初のパーティションに DirectQuery パーティションのフラグが既定で設定されます。 この設定は、後で [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]のパーティション マネージャーを使用して変更できます。  
  
 DirectQuery モードで 1 つのパーティションのみ許可するのはなぜでしょうか。  
  
 テーブル モデルでは、OLAP モデルの場合と同様に、テーブルのパーティションが SQL クエリによって定義されます。 パーティションの定義を作成する開発者は、パーティションが重ならないようにする必要があります。 Analysis Services では、レコードが 1 つのパーティションに属しているか、複数のパーティションに属しているかはチェックされません。  
  
 キャッシュされたテーブル モデル内のパーティションは同じように動作します。 インメモリ モデルを使用する場合は、キャッシュがアクセスされるときに、DAX 数式がパーティションごとに評価され、結果が結合されます。 一方、テーブル モデルが DirectQuery モードを使用する場合は、複数のパーティションを評価して結果を結合し、リレーショナル データ ストアに送信する SQL ステートメントに変換することは不可能です。 この操作を行うと、パフォーマンスが許容できないほど低下し、集計される結果が不正確になる可能性があります。  
  
 したがって、DirectQuery モードで応答されたクエリに対して、サーバーは DirectQuery アクセスのプライマリ パーティションとしてマークされた単一のパーティション ( *DirectQuery パーティション*) を使用します。  このパーティションの定義で指定された SQL クエリは、DirectQuery モードでのクエリの応答に使用できるデータの完全なセットを定義します。  
  
 パーティションを明示的に定義していない場合、エンジンは単純にリレーショナル データ ソース全体に SQL クエリを発行し、DAX 数式で指定されたセットベース操作を実行してクエリ結果を返します。  
  
  
## <a name="change-a-directquery-partition"></a>DirectQuery パーティションの変更  
 テーブル内で DirectQuery パーティションとして指定できるパーティションは 1 つだけであるため、Analysis Services ではテーブルに作成された最初のパーティションが既定で使用されます。 モデル プロジェクトの作成時に、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]の [パーティション マネージャー] ダイアログ ボックスを使用して DirectQuery パーティションを変更できます。 配置済みのモデルでは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用して DirectQuery パーティションを変更できます  
  
#### <a name="change-the-directquery-partition-for-a-tabular-model-project"></a>テーブル モデル プロジェクトの DirectQuery パーティションの変更  
  
1.  [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]のモデル デザイナーで、パーティション テーブルが含まれているテーブル (タブ) をクリックします。  
  
2.  **[テーブル]** メニューをクリックし、 **[パーティション]**をクリックします。  
  
3.  **[パーティション マネージャー]**で、現在の直接クエリ パーティションであるパーティションはパーティション名に **(DirectQuery)** というプレフィックスで示されます。  
  
     **[パーティション]** ボックスの一覧で別のパーティションを選択し、 **[DirectQuery として設定]**をクリックします。 **[DirectQuery として設定]** ボタンは、現在の DirectQuery パーティションが選択されている場合は無効になり、モデルが直接 Direct Query モードに対して有効になっていない場合は表示されません。  
  
4.  必要に応じて、処理オプションを変更し、 **[OK]**をクリックします。  
  
#### <a name="change-the-directquery-partition-for-a-deployed-tabular-model"></a>配置済みテーブル モデルの DirectQuery パーティションの変更  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、オブジェクト エクスプローラーにモデル データベースを開きます。  
  
2.  **[テーブル]** ノードを展開し、パーティション分割されたテーブルを右クリックして **[パーティション]**を選択します。  
  
     DirectQuery モードで使用するように指定されたパーティションには、パーティション名にプレフィックス (DirectQuery) があります。  
  
3.  別のパーティションに変更するには、 **[直接クエリ]** ツール バー アイコンをクリックして **[DirectQuery パーティションの設定]** ダイアログ ボックスを開きます。 [直接クエリ] ツール バー アイコンは、直接クエリに対して有効になっていないモデルでは使用できません。  
  
4.  **[パーティション名]** ボックスの一覧から別のパーティションを選択し、必要に応じてパーティションの処理オプションを変更します。  
  
## <a name="partitions-in-cached-models-and-in-directquery-models"></a>キャッシュ モデルと DirectQuery モデルのパーティション  
 DirectQuery パーティションを構成するときは、パーティションの処理オプションを指定する必要があります。  
  
 DirectQuery パーティションには 2 つの処理オプションがあります。 このプロパティを設定するには、 **の** [パーティション マネージャー] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用して、 **[処理オプション]** プロパティを選択します。 次の表にこのプロパティの値を示し、接続文字列の [DirectQueryUsage] プロパティと組み合わせた場合の各値の影響について説明します。  
  
|**接続文字列** プロパティ|**[処理オプション]** プロパティ|注|  
|------------------------------------|------------------------------------|-----------|  
|DirectQuery|[このパーティションを処理しない]|モデルが DirectQuery のみを使用している場合、処理は必要ありません。<br /><br /> ハイブリッド モデルでは、DirectQuery パーティションが処理されないように構成できます。 たとえば、非常に大きなデータ セットを操作する場合に、キャッシュに結果のすべてを追加する必要がなければ、DirectQuery パーティションにテーブル内の他のパーティションに対する結果の和集合を含めて、和集合を処理しないことを指定できます。 リレーショナル ソースに対するクエリは影響を受けず、キャッシュ データに対するクエリは他のパーティションからのデータを結合します。|  
|DataView = サンプル<br /><br /> サンプル データ ビューを使用して表形式モデルに適用されます。|[パーティションを処理できる]|データ モデルがサンプルを使用している場合は、モデルの設計時に視覚的な手掛かりを提供するフィルター選択されたデータセットを返すようにテーブルを処理できます。|  
|DirectQueryUsage = InMemory With DirectQuery (インメモリ (DirectQuery あり))<br /><br /> インメモリと DirectQuery モードの組み合わせで実行される 1100 または 1103 表形式モデルに適用されます。|[パーティションを処理できる]|モデルがハイブリッド モードを使用している場合は、インメモリと DirectQuery データ ソースに対するクエリで同じパーティションを使用する必要があります。|  
  
## <a name="see-also"></a>参照  
 [パーティション (SSAS テーブル)](../../analysis-services/tabular-models/partitions-ssas-tabular.md)  
  
  

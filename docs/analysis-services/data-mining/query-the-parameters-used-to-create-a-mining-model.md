---
title: マイニング モデルを作成するために使用されたパラメーターのクエリ |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: df2eb8317f90a96b35fc886e2158000e0f57d09d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62469499"
---
# <a name="query-the-parameters-used-to-create-a-mining-model"></a>マイニング モデルの作成に使用されたパラメーターのクエリ
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  マイニング モデルの構成は、トレーニング ケースだけでなく、モデルの作成時に設定されたパラメーターの影響も受けます。 したがって、既存のモデルのパラメーター設定を取得すると、モデルの動作をよりよく理解できる可能性があります。 そのモデルの特定のバージョンのドキュメントを作成する場合にも便利です。  
  
 モデルの作成時に使用されたパラメーターを確認するには、いずれかのマイニング モデル スキーマ行セットに対するクエリを作成します。 これらのスキーマ行セットは、一連の TRANSACT-SQL 構文を使用して簡単にクエリできるシステム ビューとして公開されます。 この手順では、指定したマイニング モデルの作成に使用されたパラメーターを返すクエリを作成する方法について説明します。  
  
### <a name="to-open-a-query-window-for-a-schema-rowset-query"></a>スキーマ行セットのクエリのためのクエリ ウィンドウを開くには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、クエリするモデルが含まれている [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスを開きます。  
  
2.  インスタンス名を右クリックし、 **[新しいクエリ]** をポイントして **[DMX]** をクリックします。  
  
    > [!NOTE]  
    >  データ マイニング モデルに対するクエリは、 **MDX** テンプレートを使用して作成することもできます。  
  
3.  インスタンスに複数のデータベースが含まれている場合は、クエリするモデルが含まれているデータベースをツール バーの **[使用できるデータベース]** の一覧から選択します。  
  
### <a name="to-return-model-parameters-for-an-existing-mining-model"></a>既存のマイニング モデルのモデル パラメーターを取得するには  
  
1.  DMX クエリ ペインで、次のテキストを入力するか、コピーして貼り付けます。  
  
    ```  
    SELECT MINING_PARAMETERS  
    FROM $system.DMSCHEMA_MINING_MODELS  
    WHERE MODEL_NAME = ''  
    ```  
  
2.  オブジェクト エクスプローラーで目的のマイニング モデルをクリックし、DMX クエリ ペインの単一引用符の間にドラッグします。  
  
3.  F5&lt;/localizedText&gt; キーを押すか、 **[実行]** をクリックします。  
  
## <a name="example"></a>例  
 次のコードは、「 [Basic Data Mining Tutorial](http://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c)」のマイニング モデルの作成に使用されたパラメーターのリストを返します。 返されるパラメーターには、サーバー上のプロバイダーで利用可能なマイニング サービスによって使用される既定値の明示的な値も含まれます。  
  
```  
SELECT MINING_PARAMETERS   
FROM $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'TM Clustering'  
```  
  
 このコード例では、クラスター モデルについて次のパラメーターが返されます。  
  
 例の結果を次に示します。  
  
 MINING_PARAMETERS  
  
 CLUSTER_COUNT=10,CLUSTER_SEED=0,CLUSTERING_METHOD=1,MAXIMUM_INPUT_ATTRIBUTES=255,MAXIMUM_STATES=100,MINIMUM_SUPPORT=1,MODELLING_CARDINALITY=10,SAMPLE_SIZE=50000,STOPPING_TOLERANCE=10  
  
## <a name="see-also"></a>参照  
 [データ マイニングのクエリ タスクと操作方法](../../analysis-services/data-mining/data-mining-query-tasks-and-how-tos.md)   
 [データ マイニング クエリ](../../analysis-services/data-mining/data-mining-queries.md)  
  
  

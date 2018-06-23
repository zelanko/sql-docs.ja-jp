---
title: マイニング モデルを作成するために使用するパラメーターのクエリ |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- content queries [DMX]
ms.assetid: ce7719e0-6127-4d9c-a753-0e0a3db065e1
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: de91c7f924fbd6d83d3a7b74cbc5bd5e5b8f880d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36163975"
---
# <a name="query-the-parameters-used-to-create-a-mining-model"></a>マイニング モデルの作成に使用されたパラメーターのクエリ
  マイニング モデルの構成は、トレーニング ケースだけでなく、モデルの作成時に設定されたパラメーターの影響も受けます。 したがって、既存のモデルのパラメーター設定を取得すると、モデルの動作をよりよく理解できる可能性があります。 そのモデルの特定のバージョンのドキュメントを作成する場合にも便利です。  
  
 モデルの作成時に使用されたパラメーターを確認するには、いずれかのマイニング モデル スキーマ行セットに対するクエリを作成します。 [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)]では、それらのスキーマ行セットが、Transact-SQL 構文を使用して簡単にクエリできる一連のシステム ビューとして公開されます。 この手順では、指定したマイニング モデルの作成に使用されたパラメーターを返すクエリを作成する方法について説明します。  
  
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
 次のコードは、「 [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md)」のマイニング モデルの作成に使用されたパラメーターのリストを返します。 返されるパラメーターには、サーバー上のプロバイダーで利用可能なマイニング サービスによって使用される既定値の明示的な値も含まれます。  
  
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
 [データ マイニング クエリ タスクと操作方法](data-mining-query-tasks-and-how-tos.md)   
 [データ マイニング クエリ](data-mining-queries.md)  
  
  
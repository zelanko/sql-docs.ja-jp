---
title: "Select ステートメントを DMX を理解する |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: DMX
helpviewer_keywords:
- browsing mining model [Analysis Services]
- Data Mining Extensions [Analysis Services], statements
- DMX [Analysis Services], statements
- predictions [DMX]
- queries [DMX], Select statement
- SELECT statement [DMX]
- statements [DMX], SELECT statement
- copying mining models
ms.assetid: 61e97285-4a06-4434-9a40-38cde5af7c3f
caps.latest.revision: "40"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 063b94b4229221c998c42691a1c8832ac42be819
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="understanding-the-dmx-select-statement"></a>DMX 選択ステートメントについて
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  [選択](../dmx/select-dmx.md)ステートメントでデータ マイニング拡張機能 (DMX) で作成するほとんどのクエリの基礎となる[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]です。 このステートメントでは、データ マイニング モデルの参照や予測などのさまざまなタスクを実行することができます。  
  
 使用して実行できるタスクは次のとおり、**選択**ステートメント。  
  
-   データ マイニング モデルの参照。 スキーマ行セットによってモデルの構造が定義されます。  
  
-   マイニング モデル列が取り得る値の検出。  
  
-   マイニング モデル内のノードに割り当てられたケースの参照、または代表のケースの取得。  
  
-   さまざまな入力を使用した予測の作成。  
  
-   マイニング モデルのコピー。  
  
 呼び出すことがデータの異なるセットを使用してこれらの各タスク、*データ ドメイン*です。 データ ドメインを定義する、 **FROM**ステートメントの句。  
  
-   データ セットを定義するルール、予測に使用する式など、データ マイニング モデル オブジェクト自体でオブジェクトを検索する必要があるとします。  
  
     この場合は、モデル自体に格納されているメタデータを確認します。 したがって、データ ドメインは、データ マイニング スキーマ行セットの列です。  
  
-   モデルの作成に使用されたケースから詳細情報を取得する必要があるとします。  
  
     この場合は、データ ドメインであるマイニング構造にドリルスルーして、Gender、Bike Buyer などの列の各行を確認します。  
  
 **重要:**または式の一覧に含まれているもの、**場所**句がで定義されているデータ ドメインから取得する必要があります、 **FROM**句。 データ ドメインを混在させることはできません。  
  
##  <a name="Select_Types"></a>種類を選択します。  
 構文**選択**ステートメントは、さまざまなタスクをサポートしています。 このようなタスクを実行するには、次のパターンを使用します。  
  
-   [予測します。](#Predicting)  
  
-   [参照](#Browsing)  
  
-   [コピー](#Copying)  
  
-   [ドリル スルー](#Drillthrough)  
  
###  <a name="Predicting"></a>予測します。  
 マイニング モデルに基づいた予測を実行するには、次のクエリの型を使用します。  
  
 参照または予測のいずれかを含めることができます**選択**内のステートメント、 **FROM**と**場所**予測結合の句**選択**ステートメントです。  
  
|クエリの型|Description|  
|----------------|-----------------|  
|SELECT FROM [NATURAL] PREDICTION JOIN します。|マイニング モデル内の列を内部データ ソースの列に結合させることで作成される予測を返します。<br /><br /> このクエリの型のドメインは、モデルからの予測可能列および入力データ ソースからの列となります。<br /><br /> [SELECT FROM &#60; モデル &#62;。予測結合 &#40;DMX&#41;](../dmx/select-from-model-prediction-join-dmx.md)<br /><br /> [予測クエリ &#40;データ マイニング&#41;](../analysis-services/data-mining/prediction-queries-data-mining.md)|  
|SELECT FROM *\<モデル >*|マイニング モデルにのみ基づいた、予測可能な列の最も可能性の高い状態を返します。 このクエリの型は、空の予測結合で予測を作成するための近道となります。<br /><br /> このクエリの型のドメインは、モデルからの予測可能列です。<br /><br /> [SELECT FROM &#60; モデル &#62;。& # #40; DMX &#41;](../dmx/select-from-model-dmx.md)<br /><br /> [予測クエリ &#40;データ マイニング&#41;](../analysis-services/data-mining/prediction-queries-data-mining.md)|  
  
 [Select の型に戻る](#Select_Types)  
  
###  <a name="Browsing"></a>参照  
 マイニング モデルの内容を参照するには、次のクエリの型を使用します。  
  
|クエリの型|Description|  
|----------------|-----------------|  
|SELECT DISTINCT FROM *\<モデル >*|指定された列に対して、マイニング モデルからすべての状態値を返します。<br /><br /> このクエリの型のデータ ドメインはデータ マイニング モデルです。<br /><br /> [SELECT DISTINCT FROM &#60; モデル &#62;。& # #40; DMX &#41;](../dmx/select-distinct-from-model-dmx.md)<br /><br /> [コンテンツ クエリ (&) #40 です。 データ マイニング &#41;](../analysis-services/data-mining/content-queries-data-mining.md)|  
|SELECT FROM *\<モデル >*です。コンテンツ|マイニング モデルを説明する内容を返します。<br /><br /> このクエリの型のデータ ドメインはコンテンツ スキーマ行セットです。<br /><br /> [SELECT FROM &#60; モデル &#62;。コンテンツ &#40;DMX&#41;](../dmx/select-from-model-content-dmx.md)<br /><br /> [コンテンツ クエリ (&) #40 です。 データ マイニング &#41;](../analysis-services/data-mining/content-queries-data-mining.md)|  
|SELECT FROM *\<モデル >*です。DIMENSION_CONTENT|マイニング モデルを説明する内容を返します。<br /><br /> このクエリの型のデータ ドメインはコンテンツ スキーマ行セットです。<br /><br /> [SELECT FROM &#60; モデル &#62;。DIMENSION_CONTENT &#40;DMX&#41;](../dmx/select-from-model-dimension-content-dmx.md)|  
|SELECT FROM *\<モデル >*です。PMML|この機能をサポートするアルゴリズムに対して、マイニング モデルの Predictive Model Markup Language (PMML) 表記法を返します。<br /><br /> このクエリの型のドメインは PMML スキーマ行セットです。<br /><br /> [DMSCHEMA_MINING_MODEL_CONTENT_PMML 行セット](../analysis-services/schema-rowsets/data-mining/dmschema-mining-model-content-pmml-rowset.md)|  
  
 [Select の型に戻る](#Select_Types)  
  
###  <a name="Copying"></a>コピー  
 マイニング モデルおよび関連するマイニング構造を新しいモデルにコピーし、ステートメント内でそのモデルの名前を変更できます。  
  
|クエリの型|Description|  
|----------------|-----------------|  
|SELECT INTO *\<新しいモデル >*|マイニング モデルのコピーを作成します。<br /><br /> このクエリの型のドメインはデータ マイニング モデルです。<br /><br /> [SELECT INTO &#40;DMX&#41;](../dmx/select-into-dmx.md)|  
  
 [Select の型に戻る](#Select_Types)  
  
###  <a name="Drillthrough"></a>ドリル スルー  
 モデルの学習に使用されたケース、またはケースの表記を参照するには、次のクエリの型を使用します。  
  
|クエリの型|Description|  
|----------------|-----------------|  
|SELECT FROM *\<モデル >*です。場合|マイニング モデルのトレーニングに使用されたケースを返します。<br /><br /> このクエリの型のドメインはデータ マイニング モデルです。<br /><br /> [SELECT FROM &#60; モデル &#62;。場合 &#40;DMX&#41;](../dmx/select-from-model-cases-dmx.md)<br /><br /> [DMX を使用したドリルスルー クエリの作成](../analysis-services/data-mining/create-drillthrough-queries-using-dmx.md)|  
|SELECT FROM *\<モデル >*です。SAMPLE_CASES|マイニング モデルのトレーニングに使用されたケースを表すサンプル ケースを返します。<br /><br /> このクエリの型のドメインはデータ マイニング モデルです。<br /><br /> [SELECT FROM &#60; モデル &#62;。SAMPLE_CASES &#40;DMX&#41;](../dmx/select-from-model-sample-cases-dmx.md)|  
|SELECT FROM *\<構造 >*です。 場合|基になるマイニング構造から詳細なデータ行を返します。この詳細情報は、マイニング モデルのトレーニングで使用されなかった場合にも返されます。<br /><br /> [SELECT FROM &#60; 構造 &#62;。場合](../dmx/select-from-structure-cases.md)<br /><br /> [ドリルスルー クエリ &#40;データ マイニング&#41;](../analysis-services/data-mining/drillthrough-queries-data-mining.md)|  
  
 [Select の型に戻る](#Select_Types)  
  
## <a name="see-also"></a>参照  
 [データ マイニング拡張機能 &#40;DMX&#41;参照](../dmx/data-mining-extensions-dmx-reference.md)   
 [データ マイニング拡張機能 &#40;DMX&#41;ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)   
 [データ マイニング拡張機能 &#40;DMX&#41;構文表記規則](../dmx/data-mining-extensions-dmx-syntax-conventions.md)  
  
  

---
title: Select ステートメントを DMX を理解する |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 114f1d52db15cd98298d855714c482d959e86a7f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68065342"
---
# <a name="understanding-the-dmx-select-statement"></a>DMX SELECTステートメントについて
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  [SELECT](../dmx/select-dmx.md)ステートメントは、[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] のデータ マイニング拡張機能 (DMX) で作成するほとんどのクエリの基礎になります。 このステートメントでは、データ マイニング モデルの参照や予測などのさまざまなタスクを実行することができます。  
  
 **SELECT**ステートメントを使用して実行できるタスクは次のとおりです:  
  
-   データ マイニング モデルを参照します。 スキーマ行セットは、モデルの構造を定義します。  
  
-   マイニング モデル列の値を検出します。  
  
-   マイニング モデル内のノードに割り当てられているまたは代表のケースを取得するケースを参照します。  
  
-   さまざまな入力を使用した予測の作成。  
  
-   マイニング モデルをコピーします。  
  
 ここには、データのさまざまなセットを使用してこれらの各タスク、*データ ドメイン*します。 データ ドメインを定義する、 **FROM**ステートメントの句。  
  
-   一連のデータ、または予測に使用する式を定義する規則など、データ マイニング モデルにオブジェクトを検索するには。  
  
     その場合は、モデル自体に格納されているメタデータを確認する必要があります。 したがって、データ ドメインは、データ マイニング スキーマ行セット内の列です。  
  
-   モデルの作成に使用されたケースから詳細情報を取得する必要があるとします。  
  
     この場合は、データ ドメインであるマイニング構造にドリルスルーして、Gender、Bike Buyer などの列の各行を確認します。  
  
 **重要:** または、式の一覧に含まれているもの、**場所**句で定義されているデータ ドメインから取得する必要があります、 **FROM**句。 データ ドメインを混在させることはできません。  
  
##  <a name="Select_Types"></a> 型を選択します。  
 **SELECT**ステートメントの構文は、さまざまなタスクをサポートしています。 これらのタスクを実行するには、以下のパターンを使用します。  
  
-   [予測](#Predicting)  
  
-   [参照](#Browsing)  
  
-   [コピー](#Copying)  
  
-   [ドリル スルー](#Drillthrough)  
  
###  <a name="Predicting"></a> 予測します。  
 次のクエリの種類を使用してマイニング モデルに基づく予測を行うことができます。  
  
 予測結合**SELECT**ステートメントの**FROM**句と**WHERE**句の中に、ブラウズまたは予測**SELECT**ステートメントのいずれかを含めることができます。  
  
|クエリの型|説明|  
|----------------|-----------------|  
|SELECT FROM [NATURAL] PREDICTION JOIN します。|マイニング モデル内の列を内部データ ソースの列に結合させることで作成される予測を返します。<br /><br /> このクエリの種類のドメイン モデルから予測可能列が入力データ ソースからの列です。<br /><br /> [SELECT FROM&#60;モデル&#62;PREDICTION JOIN &#40;DMX&#41;](../dmx/select-from-model-prediction-join-dmx.md)<br /><br /> [予測クエリ &#40;データ マイニング&#41;](../analysis-services/data-mining/prediction-queries-data-mining.md)|  
|SELECT FROM *\<モデル >*|マイニング モデルにのみ基づいた、予測可能な列の最も可能性の高い状態を返します。 このクエリの型は、空の予測結合で予測を作成するための近道となります。<br /><br /> このクエリの型のドメインは、モデルからの予測可能列です。<br /><br /> [SELECT FROM&#60;モデル&#62; &#40;DMX&#41;](../dmx/select-from-model-dmx.md)<br /><br /> [予測クエリ &#40;データ マイニング&#41;](../analysis-services/data-mining/prediction-queries-data-mining.md)|  
  
 [Select の型に戻る](#Select_Types)  
  
###  <a name="Browsing"></a> 参照  
 マイニング モデルの内容を参照するには、次のクエリの型を使用します。  
  
|クエリの型|説明|  
|----------------|-----------------|  
|SELECT DISTINCT FROM *\<モデル >*|指定した列のマイニング モデルからすべての状態値を返します。<br /><br /> このクエリの種類用のデータ ドメインは、データ マイニング モデルです。<br /><br /> [SELECT DISTINCT FROM&#60;モデル&#62; &#40;DMX&#41;](../dmx/select-distinct-from-model-dmx.md)<br /><br /> [コンテンツ クエリ &#40;データ マイニング&#41;](../analysis-services/data-mining/content-queries-data-mining.md)|  
|SELECT FROM *\<モデル >* します。コンテンツ|マイニング モデルを説明する内容を返します。<br /><br /> このクエリの種類用のデータ ドメインは、コンテンツ スキーマ行セットです。<br /><br /> [SELECT FROM&#60;モデル&#62;します。コンテンツ&#40;DMX&#41;](../dmx/select-from-model-content-dmx.md)<br /><br /> [コンテンツ クエリ &#40;データ マイニング&#41;](../analysis-services/data-mining/content-queries-data-mining.md)|  
|SELECT FROM *\<モデル >* します。DIMENSION_CONTENT|マイニング モデルを説明する内容を返します。<br /><br /> このクエリの種類用のデータ ドメインは、コンテンツ スキーマ行セットです。<br /><br /> [SELECT FROM&#60;モデル&#62;します。DIMENSION_CONTENT &#40;DMX&#41;](../dmx/select-from-model-dimension-content-dmx.md)|  
|SELECT FROM *\<モデル >* します。PMML|この機能をサポートするアルゴリズムに対して、マイニング モデルの Predictive Model Markup Language (PMML) 表記法を返します。<br /><br /> このクエリの型のドメインは PMML スキーマ行セットです。<br /><br /> [DMSCHEMA_MINING_MODEL_CONTENT_PMML 行セット](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-pmml-rowset)|  
  
 [Select の型に戻る](#Select_Types)  
  
###  <a name="Copying"></a> コピー  
 新しいモデルでは、マイニング モデルとその関連するマイニング構造にコピーし、ステートメント内でモデルの名前を変更できます。  
  
|クエリの型|説明|  
|----------------|-----------------|  
|SELECT INTO *\<新しいモデル >*|マイニング モデルのコピーを作成します。<br /><br /> このクエリの種類のドメインは、データ マイニング モデルです。<br /><br /> [SELECT &#40;DMX&#41;](../dmx/select-into-dmx.md)|  
  
 [Select の型に戻る](#Select_Types)  
  
###  <a name="Drillthrough"></a> ドリル スルー  
 モデルの学習に使用されたケース、またはケースの表記を参照するには、次のクエリの型を使用します。  
  
|クエリの型|説明|  
|----------------|-----------------|  
|SELECT FROM *\<モデル >* します。場合|マイニング モデルのトレーニングに使用されたケースを返します。<br /><br /> このクエリの種類のドメインは、データ マイニング モデルです。<br /><br /> [SELECT FROM&#60;モデル&#62;します。ケース&#40;DMX&#41;](../dmx/select-from-model-cases-dmx.md)<br /><br /> [DMX を使用したドリルスルー クエリの作成](../analysis-services/data-mining/create-drillthrough-queries-using-dmx.md)|  
|SELECT FROM *\<モデル >* します。SAMPLE_CASES|マイニング モデルのトレーニングに使用されたケースを表すサンプル ケースを返します。<br /><br /> このクエリの種類のドメインは、データ マイニング モデルです。<br /><br /> [SELECT FROM&#60;モデル&#62;します。SAMPLE_CASES &#40;DMX&#41;](../dmx/select-from-model-sample-cases-dmx.md)|  
|SELECT FROM *\<構造 >* します。 場合|いくつかの詳細については、マイニング モデルのトレーニングで使用されていない場合でも、基になるマイニング構造から詳細なデータ行を返します。<br /><br /> [SELECT FROM&#60;構造&#62;します。場合](../dmx/select-from-structure-cases.md)<br /><br /> [ドリルスルー クエリ &#40;データ マイニング&#41;](../analysis-services/data-mining/drillthrough-queries-data-mining.md)|  
  
 [Select の型に戻る](#Select_Types)  
  
## <a name="see-also"></a>関連項目  
 [データ マイニング拡張機能 &#40;DMX&#41; リファレンス](../dmx/data-mining-extensions-dmx-reference.md)   
 [データ マイニング拡張機能&#40;DMX&#41;ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)   
 [データ マイニング拡張機能&#40;DMX&#41;構文表記規則](../dmx/data-mining-extensions-dmx-syntax-conventions.md)  
  
  

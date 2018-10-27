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
manager: kfile
ms.openlocfilehash: 720956a936127cf3fec82fabc4e140782fe2e0da
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/26/2018
ms.locfileid: "50144837"
---
# <a name="understanding-the-dmx-select-statement"></a>DMX 選択ステートメントについて
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  [選択](../dmx/select-dmx.md)ステートメントでデータ マイニング拡張機能 (DMX) で作成するほとんどのクエリの基礎となる[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]します。 このステートメントでは、データ マイニング モデルの参照や予測などのさまざまなタスクを実行することができます。  
  
 使用して実行できるタスクを次に、**選択**ステートメント。  
  
-   データ マイニング モデルの参照。 スキーマ行セットによってモデルの構造が定義されます。  
  
-   マイニング モデル列が取り得る値の検出。  
  
-   マイニング モデル内のノードに割り当てられたケースの参照、または代表のケースの取得。  
  
-   さまざまな入力を使用した予測の作成。  
  
-   マイニング モデルのコピー。  
  
 ここには、データのさまざまなセットを使用してこれらの各タスク、*データ ドメイン*します。 データ ドメインを定義する、 **FROM**ステートメントの句。  
  
-   データ セットを定義するルール、予測に使用する式など、データ マイニング モデル オブジェクト自体でオブジェクトを検索する必要があるとします。  
  
     この場合は、モデル自体に格納されているメタデータを確認します。 したがって、データ ドメインは、データ マイニング スキーマ行セットの列です。  
  
-   モデルの作成に使用されたケースから詳細情報を取得する必要があるとします。  
  
     この場合は、データ ドメインであるマイニング構造にドリルスルーして、Gender、Bike Buyer などの列の各行を確認します。  
  
 **重要:** または式の一覧に含まれているもの、**場所**句で定義されているデータ ドメインから取得する必要があります、 **FROM**句。 データ ドメインを混在させることはできません。  
  
##  <a name="Select_Types"></a> 型を選択します。  
 構文**選択**ステートメントは、さまざまなタスクをサポートしています。 このようなタスクを実行するには、次のパターンを使用します。  
  
-   [予測します。](#Predicting)  
  
-   [参照](#Browsing)  
  
-   [コピー](#Copying)  
  
-   [ドリル スルー](#Drillthrough)  
  
###  <a name="Predicting"></a> 予測します。  
 マイニング モデルに基づいた予測を実行するには、次のクエリの型を使用します。  
  
 参照または予測のいずれかを含めることができます**選択**内のステートメント、 **FROM**と**場所**句では、予測結合**を選択します**ステートメント。  
  
|クエリの型|説明|  
|----------------|-----------------|  
|SELECT FROM [NATURAL] PREDICTION JOIN します。|マイニング モデル内の列を内部データ ソースの列に結合させることで作成される予測を返します。<br /><br /> このクエリの型のドメインは、モデルからの予測可能列および入力データ ソースからの列となります。<br /><br /> [SELECT FROM&#60;モデル&#62;PREDICTION JOIN &#40;DMX&#41;](../dmx/select-from-model-prediction-join-dmx.md)<br /><br /> [予測クエリ &#40;データ マイニング&#41;](../analysis-services/data-mining/prediction-queries-data-mining.md)|  
|SELECT FROM *\<モデル >*|マイニング モデルにのみ基づいた、予測可能な列の最も可能性の高い状態を返します。 このクエリの型は、空の予測結合で予測を作成するための近道となります。<br /><br /> このクエリの型のドメインは、モデルからの予測可能列です。<br /><br /> [SELECT FROM&#60;モデル&#62; &#40;DMX&#41;](../dmx/select-from-model-dmx.md)<br /><br /> [予測クエリ &#40;データ マイニング&#41;](../analysis-services/data-mining/prediction-queries-data-mining.md)|  
  
 [Select の型に戻る](#Select_Types)  
  
###  <a name="Browsing"></a> 参照  
 マイニング モデルの内容を参照するには、次のクエリの型を使用します。  
  
|クエリの型|説明|  
|----------------|-----------------|  
|SELECT DISTINCT FROM *\<モデル >*|指定された列に対して、マイニング モデルからすべての状態値を返します。<br /><br /> このクエリの型のデータ ドメインはデータ マイニング モデルです。<br /><br /> [SELECT DISTINCT FROM&#60;モデル&#62; &#40;DMX&#41;](../dmx/select-distinct-from-model-dmx.md)<br /><br /> [コンテンツ クエリ &#40;データ マイニング&#41;](../analysis-services/data-mining/content-queries-data-mining.md)|  
|SELECT FROM *\<モデル >* します。コンテンツ|マイニング モデルを説明する内容を返します。<br /><br /> このクエリの型のデータ ドメインはコンテンツ スキーマ行セットです。<br /><br /> [SELECT FROM&#60;モデル&#62;します。コンテンツ&#40;DMX&#41;](../dmx/select-from-model-content-dmx.md)<br /><br /> [コンテンツ クエリ &#40;データ マイニング&#41;](../analysis-services/data-mining/content-queries-data-mining.md)|  
|SELECT FROM *\<モデル >* します。DIMENSION_CONTENT|マイニング モデルを説明する内容を返します。<br /><br /> このクエリの型のデータ ドメインはコンテンツ スキーマ行セットです。<br /><br /> [SELECT FROM&#60;モデル&#62;します。DIMENSION_CONTENT &#40;DMX&#41;](../dmx/select-from-model-dimension-content-dmx.md)|  
|SELECT FROM *\<モデル >* します。PMML|この機能をサポートするアルゴリズムに対して、マイニング モデルの Predictive Model Markup Language (PMML) 表記法を返します。<br /><br /> このクエリの型のドメインは PMML スキーマ行セットです。<br /><br /> [DMSCHEMA_MINING_MODEL_CONTENT_PMML 行セット](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-pmml-rowset)|  
  
 [Select の型に戻る](#Select_Types)  
  
###  <a name="Copying"></a> コピー  
 マイニング モデルおよび関連するマイニング構造を新しいモデルにコピーし、ステートメント内でそのモデルの名前を変更できます。  
  
|クエリの型|説明|  
|----------------|-----------------|  
|SELECT INTO *\<新しいモデル >*|マイニング モデルのコピーを作成します。<br /><br /> このクエリの型のドメインはデータ マイニング モデルです。<br /><br /> [SELECT &AMP;#40;DMX&AMP;#41;](../dmx/select-into-dmx.md)|  
  
 [Select の型に戻る](#Select_Types)  
  
###  <a name="Drillthrough"></a> ドリル スルー  
 モデルの学習に使用されたケース、またはケースの表記を参照するには、次のクエリの型を使用します。  
  
|クエリの型|説明|  
|----------------|-----------------|  
|SELECT FROM *\<モデル >* します。場合|マイニング モデルのトレーニングに使用されたケースを返します。<br /><br /> このクエリの型のドメインはデータ マイニング モデルです。<br /><br /> [SELECT FROM&#60;モデル&#62;します。ケース&#40;DMX&#41;](../dmx/select-from-model-cases-dmx.md)<br /><br /> [DMX を使用したドリルスルー クエリの作成](../analysis-services/data-mining/create-drillthrough-queries-using-dmx.md)|  
|SELECT FROM *\<モデル >* します。SAMPLE_CASES|マイニング モデルのトレーニングに使用されたケースを表すサンプル ケースを返します。<br /><br /> このクエリの型のドメインはデータ マイニング モデルです。<br /><br /> [SELECT FROM&#60;モデル&#62;します。SAMPLE_CASES &#40;DMX&#41;](../dmx/select-from-model-sample-cases-dmx.md)|  
|SELECT FROM *\<構造 >* します。 場合|基になるマイニング構造から詳細なデータ行を返します。この詳細情報は、マイニング モデルのトレーニングで使用されなかった場合にも返されます。<br /><br /> [SELECT FROM&#60;構造&#62;します。場合](../dmx/select-from-structure-cases.md)<br /><br /> [ドリルスルー クエリ &#40;データ マイニング&#41;](../analysis-services/data-mining/drillthrough-queries-data-mining.md)|  
  
 [Select の型に戻る](#Select_Types)  
  
## <a name="see-also"></a>参照  
 [データ マイニング拡張機能 &#40;DMX&#41; リファレンス](../dmx/data-mining-extensions-dmx-reference.md)   
 [データ マイニング拡張機能&#40;DMX&#41;ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)   
 [データ マイニング拡張機能&#40;DMX&#41;構文表記規則](../dmx/data-mining-extensions-dmx-syntax-conventions.md)  
  
  

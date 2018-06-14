---
title: データ マイニング拡張機能 (DMX) ステートメント リファレンス |Microsoft ドキュメント
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1baab80455cc5267686bf26251629a1d47065344
ms.sourcegitcommit: 8f0faa342df0476884c3238e36ae3d9634151f87
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2018
ms.locfileid: "34841495"
---
# <a name="data-mining-extensions-dmx-statements"></a>データ マイニング拡張機能 (DMX) ステートメント
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  作業してデータ マイニング モデル[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]次の主なタスクが含まれます。  
  
-   マイニング構造とマイニング モデルの作成  
  
-   マイニング構造とマイニング モデルの処理  
  
-   マイニング構造またはマイニング モデルの削除あるいはドロップ  
  
-   マイニング モデルのコピー  
  
-   マイニング モデルの参照  
  
-   マイニング モデルに対する予測  
  
 データ マイニング拡張機能 (DMX) ステートメントを使用して、これらの各タスクをプログラムから実行できます。  
  
 マイニング構造とマイニング モデルの作成  
 使用して、 [CREATE MINING STRUCTURE &#40;DMX&#41; ](../dmx/create-mining-structure-dmx.md)ステートメントに、データベースに新しいマイニング構造を追加します。 使用してできます、 [ALTER MINING STRUCTURE &#40;DMX&#41; ](../dmx/alter-mining-structure-dmx.md)ステートメントに、マイニング構造にマイニング モデルを追加します。  
  
 使用して、 [CREATE MINING MODEL &#40;DMX&#41; ](../dmx/create-mining-model-dmx.md)ステートメントを新しいマイニング モデルと関連付けられているマイニング構造を構築します。  
  
 マイニング構造とマイニング モデルの処理  
 使用して、 [INSERT INTO &#40;DMX&#41; ](../dmx/insert-into-dmx.md) 、マイニング構造とマイニング モデルを処理するステートメント。  
  
 マイニング構造またはマイニング モデルの削除あるいはドロップ  
 使用して、[削除&#40;DMX&#41; ](../dmx/delete-dmx.md)マイニング モデルまたはマイニング構造からトレーニング済みのすべてのデータを削除するステートメント。 使用して、 [DROP MINING STRUCTURE &#40;DMX&#41; ](../dmx/drop-mining-structure-dmx.md)または[DROP MINING MODEL &#40;DMX&#41; ](../dmx/drop-mining-model-dmx.md)ステートメント、マイニング構造またはマイニング モデルをデータベースから完全に削除します。  
  
 マイニング モデルのコピー  
 使用して、 [SELECT INTO &#40;DMX&#41; ](../dmx/select-into-dmx.md)ステートメント、新しいマイニング モデルに既存のマイニング モデルの構造をコピーして、同じデータを持つ新しいモデルのトレーニングにします。  
  
 マイニング モデルの参照  
 使用して、[選択&#40;DMX&#41; ](../dmx/select-dmx.md)データ マイニング アルゴリズムを計算し、モデルのトレーニング中に、データ マイニング モデルに格納される情報を参照するステートメント。 同様に[!INCLUDE[tsql](../includes/tsql-md.md)]、その機能を拡張、SELECT ステートメントでは、いくつかの句を使用することができます。 これらの句を含める[DISTINCT FROM\<モデル >](../dmx/select-distinct-from-model-dmx.md)、 [FROM\<モデル >。ケース](../dmx/select-from-model-cases-dmx.md)、 [FROM\<モデル >。SAMPLE_CASES](../dmx/select-from-model-sample-cases-dmx.md)、 [FROM\<モデル >。コンテンツ](../dmx/select-from-model-content-dmx.md)と[FROM\<モデル >。DIMENSION_CONTENT](../dmx/select-from-model-dimension-content-dmx.md)です。  
  
 マイニング モデルに対する予測  
 使用して、 [PREDICTION JOIN](../dmx/select-from-model-prediction-join-dmx.md)既存のマイニング モデルに基づく予測を作成する SELECT ステートメントの句。  
  
 インポートおよびを使用してモデルをエクスポートすることも、[インポート&#40;DMX&#41; ](../dmx/import-dmx.md)と[エクスポート&#40;DMX&#41; ](../dmx/export-dmx.md)ステートメントです。  
  
 これらのタスクは、次の表に示す、データ定義ステートメントとデータ操作ステートメントの 2 つのカテゴリに分類されます。  
  
|トピック|説明|  
|-----------|-----------------|  
|[データ マイニング拡張機能&#40;DMX&#41;データ定義ステートメント](../dmx/dmx-statements-data-definition.md)|データ定義言語 (DDL) の一部です。 新しいマイニング モデルの定義 (学習を含む)、またはデータベースからの既存のマイニング モデルのドロップに使用されます。|  
|[データ マイニング拡張機能&#40;DMX&#41;データ操作ステートメント](../dmx/dmx-statements-data-manipulation.md)|データ操作言語 (DML) の一部です。 モデルの参照または予測の作成を含む、既存のマイニング モデルでの作業に使用されます。|  
  
## <a name="see-also"></a>参照  
 [データ マイニング拡張機能&#40;DMX&#41;関数リファレンス](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [データ マイニング拡張機能&#40;DMX&#41;演算子リファレンス](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [データ マイニング拡張機能&#40;DMX&#41;構文表記規則](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [データ マイニング拡張機能&#40;DMX&#41;構文要素](../dmx/data-mining-extensions-dmx-syntax-elements.md)  
  
  

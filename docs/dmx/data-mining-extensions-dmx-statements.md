---
title: "データ マイニング拡張機能 (DMX) ステートメント リファレンス |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- DMX
helpviewer_keywords:
- Data Mining Extensions [Analysis Services], statements
- DMX [Analysis Services], statements
- statements [DMX], reference
- mining models [Analysis Services], training
- mining structures [DMX]
- mining models [Analysis Services], options
- mining structures [DMX], options
ms.assetid: 9cfa1db4-0f21-4fa3-8158-f94c48987e1b
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: e7c9740eebec925bc2b25c6437f488f898288a1e
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="data-mining-extensions-dmx-statements"></a>データ マイニング拡張機能 (DMX) ステートメント
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  作業してデータ マイニング モデル[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]次の主なタスクが含まれます。  
  
-   マイニング構造とマイニング モデルの作成  
  
-   マイニング構造とマイニング モデルの処理  
  
-   マイニング構造またはマイニング モデルの削除あるいはドロップ  
  
-   マイニング モデルのコピー  
  
-   マイニング モデルの参照  
  
-   マイニング モデルに対する予測  
  
 データ マイニング拡張機能 (DMX) ステートメントを使用して、これらの各タスクをプログラムから実行できます。  
  
 マイニング構造とマイニング モデルの作成  
 使用して、[マイニング構造の作成 &#40;DMX&#41;](../dmx/create-mining-structure-dmx.md)ステートメントに、データベースに新しいマイニング構造を追加します。 使用してできます、 [ALTER MINING STRUCTURE &#40;DMX&#41;](../dmx/alter-mining-structure-dmx.md)ステートメントに、マイニング構造にマイニング モデルを追加します。  
  
 使用して、[マイニング モデルの作成 &#40;DMX&#41;](../dmx/create-mining-model-dmx.md)ステートメントを新しいマイニング モデルと関連付けられているマイニング構造を構築します。  
  
 マイニング構造とマイニング モデルの処理  
 使用して、 [INSERT INTO &#40;DMX&#41;](../dmx/insert-into-dmx.md)マイニング構造とマイニング モデルを処理するステートメント。  
  
 マイニング構造またはマイニング モデルの削除あるいはドロップ  
 使用して、[削除 &#40;DMX&#41;](../dmx/delete-dmx.md)マイニング モデルまたはマイニング構造からトレーニング済みのすべてのデータを削除するステートメント。 使用して、 [DROP MINING STRUCTURE &#40;DMX&#41;](../dmx/drop-mining-structure-dmx.md)または[DROP MINING MODEL &#40;DMX&#41;](../dmx/drop-mining-model-dmx.md)ステートメント、マイニング構造またはマイニング モデルをデータベースから完全に削除します。  
  
 マイニング モデルのコピー  
 使用して、 [SELECT INTO &#40;DMX&#41;](../dmx/select-into-dmx.md)ステートメント、新しいマイニング モデルに既存のマイニング モデルの構造をコピーして、同じデータを持つ新しいモデルのトレーニングにします。  
  
 マイニング モデルの参照  
 使用して、[選択 &#40;DMX&#41;](../dmx/select-dmx.md)データ マイニング アルゴリズムを計算し、モデルのトレーニング中に、データ マイニング モデルに格納される情報を参照するステートメント。 同様に[!INCLUDE[tsql](../includes/tsql-md.md)]、その機能を拡張、SELECT ステートメントでは、いくつかの句を使用することができます。 これらの句を含める[DISTINCT FROM\<モデル >](../dmx/select-distinct-from-model-dmx.md)、 [FROM\<モデル >。ケース](../dmx/select-from-model-cases-dmx.md)、 [FROM\<モデル >。SAMPLE_CASES](../dmx/select-from-model-sample-cases-dmx.md)、 [FROM\<モデル >。コンテンツ](../dmx/select-from-model-content-dmx.md)と[FROM\<モデル >。DIMENSION_CONTENT](../dmx/select-from-model-dimension-content-dmx.md)です。  
  
 マイニング モデルに対する予測  
 使用して、 [PREDICTION JOIN](../dmx/select-from-model-prediction-join-dmx.md)既存のマイニング モデルに基づく予測を作成する SELECT ステートメントの句。  
  
 インポートおよびを使用してモデルをエクスポートすることも、[インポート &#40;DMX&#41;](../dmx/import-dmx.md)と[エクスポート &#40;DMX&#41;](../dmx/export-dmx.md)ステートメントです。  
  
 これらのタスクは、次の表に示す、データ定義ステートメントとデータ操作ステートメントの 2 つのカテゴリに分類されます。  
  
|トピック|Description|  
|-----------|-----------------|  
|[データ マイニング拡張機能 &#40;DMX&#41;データ定義ステートメント](../dmx/dmx-statements-data-definition.md)|データ定義言語 (DDL) の一部です。 新しいマイニング モデルの定義 (学習を含む)、またはデータベースからの既存のマイニング モデルのドロップに使用されます。|  
|[データ マイニング拡張機能 &#40;DMX&#41;データ操作ステートメント](../dmx/dmx-statements-data-manipulation.md)|データ操作言語 (DML) の一部です。 モデルの参照または予測の作成を含む、既存のマイニング モデルでの作業に使用されます。|  
  
## <a name="see-also"></a>参照  
 [データ マイニング拡張機能 &#40;DMX&#41;関数リファレンス](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [データ マイニング拡張機能 &#40;DMX&#41;演算子リファレンス](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [データ マイニング拡張機能 &#40;DMX&#41;構文表記規則](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [データ マイニング拡張機能 &#40;DMX&#41;構文要素](../dmx/data-mining-extensions-dmx-syntax-elements.md)  
  
  


---
title: SELECT FROM&lt;モデル&gt;です。SAMPLE_CASES (DMX) |Microsoft ドキュメント
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f4443f05fbee790f5f1d266f451e1105b9c00197
ms.sourcegitcommit: 8f0faa342df0476884c3238e36ae3d9634151f87
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2018
ms.locfileid: "34841525"
---
# <a name="select-from-ltmodelgtsamplecases-dmx"></a>SELECT FROM&lt;モデル&gt;です。SAMPLE_CASES (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  データ マイニング モデルの学習に使用されるケースを表すサンプル ケースを返します。  
  
 このステートメントを使用するには、マイニング モデルの作成時にドリルスルーを使用可能にする必要があります。 ドリルスルーを有効にする方法の詳細については、次を参照してください[CREATE MINING MODEL &#40;DMX&#41;](../dmx/create-mining-model-dmx.md)、 [SELECT INTO &#40;DMX&#41;](../dmx/select-into-dmx.md)、および[ALTER MINING STRUCTURE &#40;DMX&#41;](../dmx/alter-mining-structure-dmx.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
SELECT [FLATTENED] [TOP <n>] <expression list> FROM <model>.SAMPLE_CASES  
[WHERE <condition list>] ORDER BY <expression> [DESC|ASC]]  
```  
  
## <a name="arguments"></a>引数  
 *n*  
 任意。 返す行数を指定する整数値です。  
  
 *式の一覧*  
 関連付けられた列識別子のコンマ区切りのリストです。  
  
 *model*  
 モデル識別子です。  
  
 *条件の一覧*  
 任意。 列の一覧から返される値を制限する条件です。  
  
 *式 (expression)*  
 任意。 スカラー値を返す式。  
  
## <a name="remarks"></a>コメント  
 サンプル ケースは生成されたものである場合や実際には学習データに存在しない場合があります。 返されたケースは、指定されたコンテンツ ノードを表します。  
  
 ただし、[!INCLUDE[msCoName](../includes/msconame-md.md)]シーケンス クラスター アルゴリズムでは、唯一[!INCLUDE[msCoName](../includes/msconame-md.md)]選択から使用をサポートするアルゴリズム\<モデル >。SAMPLE_CASES、サード パーティのアルゴリズムもこれをサポートします。  
  
## <a name="examples"></a>使用例  
 次の例では、Target Mail マイニング モデルの学習に使用されるサンプル ケースを返しています。 使用して、 [IsInNode &#40;DMX&#41; ](../dmx/isinnode-dmx.md)で機能、**場所**句 000000003」ノードに関連付けられたケースのみが返されます。 ノード文字列は、スキーマ行セットの NODE_UNIQUE_NAME 列にあります。  
  
```  
Select * from [Sequence Clustering].SAMPLE_Cases  
WHERE IsInNode('000000003')  
```  
  
## <a name="see-also"></a>参照  
 [選択&AMP;#40;DMX&AMP;#41;](../dmx/select-dmx.md)   
 [データ マイニング拡張機能&#40;DMX&#41;データ定義ステートメント](../dmx/dmx-statements-data-definition.md)   
 [データ マイニング拡張機能&#40;DMX&#41;データ操作ステートメント](../dmx/dmx-statements-data-manipulation.md)   
 [データ マイニング拡張機能 &#40;DMX&#41; ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)  
  
  

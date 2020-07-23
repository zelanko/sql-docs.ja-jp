---
title: '[モデルから] を選択し &lt; &gt; ます。DIMENSION_CONTENT (DMX) |Microsoft Docs'
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: d16b8b01251be6703350a1a64bb9cdd2bdc5cadb
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2020
ms.locfileid: "86970590"
---
# <a name="select-from-ltmodelgtdimension_content-dmx"></a>[モデルから] を選択し &lt; &gt; ます。DIMENSION_CONTENT (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  マイニング モデルは、OLAP キューブのディメンションとして使用できます。このとき、モデルの各ノードは、ディメンションのメンバーとして表されます。 **SELECT FROM \<model> です。Dimension_CONTENT**ステートメントは、ディメンションとしての使用に関連するモデルのコンテンツを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SELECT [FLATTENED] [TOP <n>] <expression list> FROM <model>.Dimension_CONTENT   
[WHERE <condition expression>]  
[ORDER BY <expression> [DESC|ASC]]  
```  
  
## <a name="arguments"></a>引数  
 *n*  
 省略可能。 返す行数を指定する整数値です。  
  
 *式の一覧*  
 コンテンツ スキーマ行セットから派生する、関連する列識別子のコンマ区切りのリストです。  
  
 *model*  
 モデル識別子。  
  
 *条件式*  
 省略可能。 列リストから返される値を制限する条件。  
  
 *式 (expression)*  
 省略可能。 スカラー値を返す式。  
  
## <a name="remarks"></a>注釈  
 アルゴリズムプロバイダーは、返されるコンテンツとその編成方法を定義します。 たとえば、プロバイダーはディメンション コンテンツに示されるノード数を制限する場合があります。  
  
 次の表は、ディメンション コンテンツのためにクエリできる列と、各列がデータ マイニング ディメンションとして実行する関数について示しています。  
  
|コンテンツ行セット列|データ マイニング ディメンションの関数|  
|---------------------------|---------------------------------------|  
|ATTRIBUTE_NAME|メンバープロパティ。|  
|NODE_NAME|メンバープロパティ。|  
|NODE_UNIQUE_NAME|キー属性。|  
|NODE_TYPE|メンバープロパティ。|  
|NODE_CAPTION|**キー**属性の CaptionColumn。|  
|CHILDREN_CARDINALITY|メンバープロパティ。|  
|PARENT_UNIQUE_NAME|**キー**属性の RelatedAttribute (親子階層の parentattribute)。|  
|NODE_DESCRIPTION|メンバープロパティ。|  
|NODE_RULE|メンバープロパティ。|  
|MARGINAL_RULE|メンバープロパティ。|  
|NODE_PROBABILITY|メンバープロパティ。|  
|MARGINAL_PROBABILITY|メンバープロパティ。|  
|NODE_SUPPORT|メンバープロパティ。|  
  
## <a name="examples"></a>例  
  
### <a name="description"></a>説明  
 次の例は、ディメンションとしてのモデルの使用に関する、`[TM Decision Tree]` モデル コンテンツのすべての列を選択します。  
  
### <a name="code"></a>コード  
  
```  
SELECT *   
FROM [TM Decision Tree].Dimension_Content  
```  
  
## <a name="see-also"></a>参照  
 [DMX&#41;を選択 &#40;](../dmx/select-dmx.md)   
 [DMX&#41; データ定義ステートメント &#40;のデータマイニング拡張機能](../dmx/dmx-statements-data-definition.md)   
 [DMX&#41; データ操作ステートメントを &#40;データマイニング拡張機能](../dmx/dmx-statements-data-manipulation.md)   
 [データ マイニング拡張機能 &#40;DMX&#41; ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)  
  
  

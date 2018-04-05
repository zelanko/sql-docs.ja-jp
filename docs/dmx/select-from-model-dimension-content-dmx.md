---
title: SELECT FROM&lt;モデル&gt;です。DIMENSION_CONTENT (DMX) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- SELECT
- FROM
- DIMENSION_CONTENT
dev_langs:
- DMX
helpviewer_keywords:
- mining models [Analysis Services], dimension content
- SELECT FROM <model>.DIMENSION_CONTENT statement
ms.assetid: 907fb3fb-2131-4a10-8635-2a39b9a805aa
caps.latest.revision: 42
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: eea37242444142b217e7a792465553cfc316321d
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="select-from-ltmodelgtdimensioncontent-dmx"></a>SELECT FROM&lt;モデル&gt;です。DIMENSION_CONTENT (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  マイニング モデルは、OLAP キューブのディメンションとして使用できます。このとき、モデルの各ノードは、ディメンションのメンバーとして表されます。 **SELECT FROM\<モデル >。Dimension_CONTENT**ステートメントは、ディメンションとしての使用に関連するモデルの内容を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SELECT [FLATTENED] [TOP <n>] <expression list> FROM <model>.Dimension_CONTENT   
[WHERE <condition expression>]  
[ORDER BY <expression> [DESC|ASC]]  
```  
  
## <a name="arguments"></a>引数  
 *n*  
 省略可。 返す行数を指定する整数値です。  
  
 *式の一覧*  
 コンテンツ スキーマ行セットから派生する、関連する列識別子のコンマ区切りのリストです。  
  
 *model*  
 モデル識別子です。  
  
 *条件式*  
 省略可。 列のリストから返される値を制限する条件です。  
  
 *式 (expression)*  
 省略可。 スカラー値を返す式。  
  
## <a name="remarks"></a>解説  
 アルゴリズム プロバイダーは、返されるコンテンツとその構成方法を定義します。 たとえば、プロバイダーはディメンション コンテンツに示されるノード数を制限する場合があります。  
  
 次の表は、ディメンション コンテンツのためにクエリできる列と、各列がデータ マイニング ディメンションとして実行する関数について示しています。  
  
|CONTENT 行セット列|データ マイニング ディメンションの関数|  
|---------------------------|---------------------------------------|  
|ATTRIBUTE_NAME|メンバー プロパティです。|  
|NODE_NAME|メンバー プロパティです。|  
|NODE_UNIQUE_NAME|キー属性です。|  
|NODE_TYPE|メンバー プロパティです。|  
|NODE_CAPTION|CaptionColumn**キー**属性。|  
|CHILDREN_CARDINALITY|メンバー プロパティです。|  
|PARENT_UNIQUE_NAME|RelatedAttribute**キー**属性 (親子階層の ParentAttribute)。|  
|NODE_DESCRIPTION|メンバー プロパティです。|  
|NODE_RULE|メンバー プロパティです。|  
|MARGINAL_RULE|メンバー プロパティです。|  
|NODE_PROBABILITY|メンバー プロパティです。|  
|MARGINAL_PROBABILITY|メンバー プロパティです。|  
|NODE_SUPPORT|メンバー プロパティです。|  
  
## <a name="examples"></a>使用例  
  
### <a name="description"></a>Description  
 次の例は、ディメンションとしてのモデルの使用に関する、`[TM Decision Tree]` モデル コンテンツのすべての列を選択します。  
  
### <a name="code"></a>コード  
  
```  
SELECT *   
FROM [TM Decision Tree].Dimension_Content  
```  
  
## <a name="see-also"></a>参照  
 [選択 &#40;DMX&#41;](../dmx/select-dmx.md)   
 [データ マイニング拡張機能 &#40;DMX&#41;データ定義ステートメント](../dmx/dmx-statements-data-definition.md)   
 [データ マイニング拡張機能 &#40;DMX&#41;データ操作ステートメント](../dmx/dmx-statements-data-manipulation.md)   
 [データ マイニング拡張機能 &#40;DMX&#41; ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)  
  
  

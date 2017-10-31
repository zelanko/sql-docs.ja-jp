---
title: "削除 (DMX) |Microsoft ドキュメント"
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
f1_keywords:
- DELETE
dev_langs:
- DMX
helpviewer_keywords:
- DELETE statement [DMX]
- mining structures [DMX], clearing
- clearing mining models
- deleting mining models
- mining models [Analysis Services], clearing
- deleting mining structures
ms.assetid: 5a8204c3-a3df-4d97-9c1d-d997d24c70e3
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 00be9b52e652e2a2456cdbcd589f048d8a971d47
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="delete-dmx"></a>DELETE (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  使用するデータ マイニング拡張機能 (DMX) 句に従って、マイニング モデル、マイニング構造、またはマイニング構造とそれに関連するすべてのマイニング モデルが削除されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
DELETE FROM [MINING MODEL] <model>[.CONTENT]  
DELETE FROM [MINING STRUCTURE] <structure>[.CONTENT]|[.CASES]  
```  
  
## <a name="arguments"></a>引数  
 *model*  
 モデル識別子です。  
  
 *構造体*  
 構造識別子です。  
  
## <a name="remarks"></a>解説  
 指定しない場合**マイニング モデルの**または**マイニング構造の**、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]名前に基づいてオブジェクトの種類を検索し、適切なオブジェクトを処理します。 サーバーが同じ名前のマイニング構造とマイニング モデルを持つ場合、エラーが返されます。  
  
 次の表は、異なる形式の構文を使用した場合の結果について示しています。  
  
|ステートメントから削除してください。|結果|  
|---------------|------------|  
|DELETE FROM MINING STRUCTURE*\<構造体 >*<br /><br /> または<br /><br /> DELETE FROM MINING STRUCTURE*\<構造 >*です。コンテンツ|マイニング構造を ProcessClear を実行します。 すべての内容がマイニング構造および関連するマイニング モデルから削除されます。|  
|DELETE FROM MINING STRUCTURE*\<構造 >*です。場合|マイニング構造を ProcessClearStructureOnly を実行します。 関連するマイニング モデルは保存したまま、すべての内容がマイニング構造から削除されます。 マイニング構造が削除された後では、関連するマイニング モデルでのドリルスルーは失敗します。|  
|マイニング モデルから削除*\<モデル >*<br /><br /> または<br /><br /> マイニング モデルから削除*\<モデル >*です。コンテンツ|ProcessClear をマイニング モデルを実行しますが、状態の値をそのまま残ります。 状態値は、その列で使用できる状態を表します。 たとえば、性別の列の状態値は、男性と女性です。|  
  
 処理の種類の詳細については、次を参照してください。[型要素 &#40;です。XMLA &#41;](../analysis-services/xmla/xml-elements-properties/type-element-xmla.md).  
  
## <a name="examples"></a>使用例  
 次の例では、すべての内容が NB_Sample モデルから削除されます。  
  
```  
DELETE FROM NB_Sample.CONTENT  
```  
  
## <a name="see-also"></a>参照  
 [データ マイニング拡張機能 &#40;DMX"&"#41;データ定義ステートメント](../dmx/dmx-statements-data-definition.md)   
 [データ マイニング拡張機能 &#40;DMX"&"#41;データ操作ステートメント](../dmx/dmx-statements-data-manipulation.md)   
 [データ マイニング拡張機能 &#40;DMX"&"#41;ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)  
  
  


---
title: AffectEnum |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- AffectEnum
helpviewer_keywords:
- AffectEnum enumeration [ADO]
ms.assetid: 1ab921a0-6c57-43b4-9291-701b2599f3e8
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a936eb39583afff34dd317b85bc4198022b15e7f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67920757"
---
# <a name="affectenum"></a>AffectEnum
操作の影響を受けるレコードを指定します。  
  
|常時|値|[説明]|  
|--------------|-----------|-----------------|  
|**adAffectAll**|3|**レコードセット**に[フィルター](../../../ado/reference/ado-api/filter-property.md)が適用されていない場合、はすべてのレコードに影響します。<br /><br /> **Filter**プロパティが文字列条件 ("Author = ' Smith '" など) に設定されている場合、操作は現在のチャプターの表示レコードに影響します。<br /><br /> **Filter**プロパティが[filtergroupenum](../../../ado/reference/ado-api/filtergroupenum.md)またはブックマークの配列のメンバーに設定されている場合、操作は**レコードセット**のすべての行に影響します。 **注: adAffectAll**は Visual Basic オブジェクトブラウザーでは非表示になっています。|  
|**adAffectAllChapters**|4|現在適用されている**フィルター**によって表示されていないものも含め、**レコードセット**のすべての兄弟チャプター内のすべてのレコードに影響します。|  
|**現在のもの**|1 で保護されたプロセスとして起動されました|現在のレコードのみに影響します。|  
|**Adています。**|2|現在の[フィルター](../../../ado/reference/ado-api/filter-property.md)プロパティの設定に適合するレコードのみに影響します。 このオプションを使用するには、 **filter**プロパティを**filtergroupenum**値または**ブックマーク**の配列に設定する必要があります。|  
  
## <a name="adowfc-equivalent"></a>同等の ADO/WFC  
 パッケージ: **com. ms. wfc. データ**  
  
|常時|  
|--------------|  
|AdoEnums|  
|AdoEnums. ALLCHAPTERS|  
|AdoEnums. CURRENT|  
|AdoEnums|  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[CancelBatch メソッド (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)|[Delete メソッド (ADO Recordset)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)|  
|[Resync メソッド](../../../ado/reference/ado-api/resync-method.md)|[UpdateBatch メソッド](../../../ado/reference/ado-api/updatebatch-method.md)|

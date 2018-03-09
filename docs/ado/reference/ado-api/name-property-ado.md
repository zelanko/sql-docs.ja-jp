---
title: "Name プロパティ (ADO) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Parameter::Name
- Field20::Name
helpviewer_keywords:
- Name property [ADO]
ms.assetid: cfd0e29c-8310-44ab-85c3-5761184b865d
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: eac3504e262f52700351c9d4313ed39d9723c844
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="name-property-ado"></a>Name プロパティ (ADO)
オブジェクトの名前を示します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 取得または設定、**文字列**オブジェクトの名前を示す値。  
  
## <a name="remarks"></a>解説  
 使用して、**名前**に名前を割り当てるまたはの名前を取得するプロパティ、**コマンド**、**プロパティ**、**フィールド**、または**パラメーター**オブジェクト。  
  
 読み取り/書き込みするには、値、**コマンド**オブジェクトおよび読み取り専用で、**プロパティ**オブジェクト。  
  
 **フィールド**オブジェクト、**名前**は通常読み取り専用です。 ただし、新規の**フィールド**に追加されたオブジェクト、[フィールド](../../../ado/reference/ado-api/fields-collection-ado.md)のコレクション、[レコード](../../../ado/reference/ado-api/record-object-ado.md)、**名前**は読み取り/書き込みにした場合のみ[値](../../../ado/reference/ado-api/value-property-ado.md)プロパティを**フィールド**が指定されているデータ プロバイダーが追加、新しいおよび**フィールド**を呼び出して、 [更新](../../../ado/reference/ado-api/update-method.md)のメソッド、**フィールド**コレクション。  
  
 **パラメーター**にオブジェクトが追加されていない、[パラメーター](../../../ado/reference/ado-api/parameters-collection-ado.md) 、コレクション、**名前**読み取り/書き込みプロパティです。 追加する**パラメーター**オブジェクトと他のすべてのオブジェクト、**名前**プロパティは読み取り専用です。 名前をコレクション内で一意である必要はありません。  
  
 取得することができます、**名前**名で直接するまで、オブジェクトを参照できます、序数参照オブジェクトのプロパティです。 たとえば場合、`rstMain.Properties(20).Name`が生成されます`Updatability`、としては、このプロパティを参照して、後で`rstMain.Properties("Updatability")`です。  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[Command オブジェクト (ADO)](../../../ado/reference/ado-api/command-object-ado.md)|[Field オブジェクト](../../../ado/reference/ado-api/field-object.md)|  
|[Parameter オブジェクト](../../../ado/reference/ado-api/parameter-object.md)|[Property オブジェクト (ADO)](../../../ado/reference/ado-api/property-object-ado.md)|  
  
## <a name="see-also"></a>参照  
 [属性と名前のプロパティの例 (VB)](../../../ado/reference/ado-api/attributes-and-name-properties-example-vb.md)   
 [属性と名前のプロパティの例 (vc++)](../../../ado/reference/ado-api/attributes-and-name-properties-example-vc.md)   

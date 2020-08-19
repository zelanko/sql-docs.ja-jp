---
description: DateModified プロパティ (ADOX)
title: DateModified プロパティ (ADOX) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Table::get_DateModified
- _Table::DateModified
- _Table::GetDateModified
helpviewer_keywords:
- DateModified property [ADOX]
ms.assetid: fed09266-1547-4bda-9088-c254d81cc738
author: rothja
ms.author: jroth
ms.openlocfilehash: 7ee921e1865530356e1fd88c97489b63a81a02ec
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88440154"
---
# <a name="datemodified-property-adox"></a>DateModified プロパティ (ADOX)
オブジェクトが最後に変更された日付を示します。  
  
## <a name="return-values"></a>戻り値  
 変更された日付を指定する **バリアント** 値を返します。 **DateModified**がプロバイダーでサポートされていない場合、値は null になります。  
  
## <a name="remarks"></a>解説  
 新しく追加されたオブジェクトの場合、 **DateModified** プロパティは null になります。 新しい[ビュー](../../../ado/reference/adox-api/view-object-adox.md)または[プロシージャ](../../../ado/reference/adox-api/procedure-object-adox.md)を追加した後、 [Views](../../../ado/reference/adox-api/views-collection-adox.md)または[Procedures](../../../ado/reference/adox-api/procedures-collection-adox.md)コレクションの[Refresh](../../../ado/reference/ado-api/refresh-method-ado.md)メソッドを呼び出して、 **DateModified**プロパティの値を取得する必要があります。  
  
## <a name="applies-to"></a>適用対象  

:::row:::
    :::column:::
        [Procedure オブジェクト (ADOX)](../../../ado/reference/adox-api/procedure-object-adox.md)  
    :::column-end:::
    :::column:::
        [Table オブジェクト (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)  
    :::column-end:::
    :::column:::
        [View オブジェクト (ADOX)](../../../ado/reference/adox-api/view-object-adox.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>参照  
 [DateCreated プロパティと DateModified プロパティの例 (VB)](../../../ado/reference/adox-api/datecreated-and-datemodified-properties-example-vb.md)   
 [DateCreated プロパティ (ADOX)](../../../ado/reference/adox-api/datecreated-property-adox.md)

---
title: DateCreated プロパティ (ADOX) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Table::get_DateCreated
- _Table::DateCreated
- _Table::GetDateCreated
helpviewer_keywords:
- DateCreated property [ADOX]
ms.assetid: 2bf4b00d-045c-444e-8af7-8af6297ed418
author: rothja
ms.author: jroth
ms.openlocfilehash: 2a94ea4d86d727bc2258b853285eaa7ebc1e48bc
ms.sourcegitcommit: 591bbf4c7e4e2092f8abda6a2ffed263cb61c585
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "86942435"
---
# <a name="datecreated-property-adox"></a>DateCreated プロパティ (ADOX)
オブジェクトが作成された日付を示します。  
  
## <a name="return-values"></a>戻り値  
 作成された日付を指定する**Variant**値を返します。 **DateCreated**がプロバイダーでサポートされていない場合、値は null になります。  
  
## <a name="remarks"></a>注釈  
 新しく追加されたオブジェクトの場合、 **DateCreated**プロパティは null になります。 新しい[ビュー](../../../ado/reference/adox-api/view-object-adox.md)または[プロシージャ](../../../ado/reference/adox-api/procedure-object-adox.md)を追加した後、 [Views](../../../ado/reference/adox-api/views-collection-adox.md)または[Procedures](../../../ado/reference/adox-api/procedures-collection-adox.md)コレクションの[Refresh](../../../ado/reference/ado-api/refresh-method-ado.md)メソッドを呼び出して、 **DateCreated**プロパティの値を取得する必要があります。  
  
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
 [DateModified プロパティ (ADOX)](../../../ado/reference/adox-api/datemodified-property-adox.md)

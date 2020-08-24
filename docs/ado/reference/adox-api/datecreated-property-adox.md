---
description: DateCreated プロパティ (ADOX)
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
ms.openlocfilehash: 7ae2c0fcfdc164906f0216abb45f98f705de9cd4
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2020
ms.locfileid: "88770741"
---
# <a name="datecreated-property-adox"></a>DateCreated プロパティ (ADOX)
オブジェクトが作成された日付を示します。  
  
## <a name="return-values"></a>戻り値  
 作成された日付を指定する **Variant** 値を返します。 **DateCreated**がプロバイダーでサポートされていない場合、値は null になります。  
  
## <a name="remarks"></a>解説  
 新しく追加されたオブジェクトの場合、 **DateCreated** プロパティは null になります。 新しい[ビュー](./view-object-adox.md)または[プロシージャ](./procedure-object-adox.md)を追加した後、 [Views](./views-collection-adox.md)または[Procedures](./procedures-collection-adox.md)コレクションの[Refresh](../ado-api/refresh-method-ado.md)メソッドを呼び出して、 **DateCreated**プロパティの値を取得する必要があります。  
  
## <a name="applies-to"></a>適用対象  

:::row:::
    :::column:::
        [Procedure オブジェクト (ADOX)](./procedure-object-adox.md)  
    :::column-end:::
    :::column:::
        [Table オブジェクト (ADOX)](./table-object-adox.md)  
    :::column-end:::
    :::column:::
        [View オブジェクト (ADOX)](./view-object-adox.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>参照  
 [DateCreated プロパティと DateModified プロパティの例 (VB)](./datecreated-and-datemodified-properties-example-vb.md)   
 [DateModified プロパティ (ADOX)](./datemodified-property-adox.md)
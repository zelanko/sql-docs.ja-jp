---
title: 順序のプロパティ (ADOX) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Column::SortOrder
- _Column::PutSortOrder
- _Column::put_SortOrder
- _Column::get_SortOrder
- _Column::GetSortOrder
helpviewer_keywords:
- SortOrder property [ADOX]
ms.assetid: 04510b19-9cb2-4895-b23b-f7790123eb04
author: rothja
ms.author: jroth
ms.openlocfilehash: 2026bcae8e0923159f6fb1044ab379d439993400
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82762793"
---
# <a name="sortorder-property-adox"></a>SortOrder プロパティ (ADOX)
列の並べ替え順序を示します (インデックス列のみ)。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 は、 [Sortorderenum](../../../ado/reference/adox-api/sortorderenum.md)定数のいずれかを指定できる**Long 型**の値を設定して返します。 既定値は**adSortAscending**です。  
  
## <a name="remarks"></a>解説  
 このプロパティは、[インデックス](../../../ado/reference/adox-api/index-object-adox.md)の[Columns](../../../ado/reference/adox-api/columns-collection-adox.md)コレクション内の[Column](../../../ado/reference/adox-api/column-object-adox.md)オブジェクトにのみ適用されます。  
  
## <a name="applies-to"></a>適用対象  
 [Column オブジェクト (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)  
  
## <a name="see-also"></a>参照  
 [順序のプロパティの例 (VB)](../../../ado/reference/adox-api/sortorder-property-example-vb.md)   
 [Columns コレクション (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [Index オブジェクト (ADOX)](../../../ado/reference/adox-api/index-object-adox.md)

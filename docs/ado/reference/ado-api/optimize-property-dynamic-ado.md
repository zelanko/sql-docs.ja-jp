---
title: Optimize プロパティ-動的 (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Optimize property [ADO]
ms.assetid: a491c4ce-2b04-4c84-be83-3846bde8d16b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3e8bb3c3787effe8418db735a72425a793b73e35
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67931851"
---
# <a name="optimize-property-dynamic-ado"></a>Optimize プロパティ - 動的 (ADO)
[フィールド](../../../ado/reference/ado-api/field-object.md)にインデックスを作成するかどうかを指定します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 インデックスを作成する必要があるかどうかを示す**ブール**値を設定または返します。  
  
## <a name="remarks"></a>解説  
 インデックスを使用すると、[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)内の値を検索したり並べ替えたりする操作のパフォーマンスを向上させることができます。 インデックスは ADO の内部にあります。アプリケーションで明示的にアクセスしたり、使用したりすることはできません。  
  
 フィールドにインデックスを作成するには、 **Optimize**プロパティを**True**に設定します。 インデックスを削除するには、このプロパティを**False**に設定します。  
  
 **[最適化**] は、[[カーソルの場所](../../../ado/reference/ado-api/cursorlocation-property-ado.md)] プロパティが**adUseClient**に設定されている場合に、[フィールド](../../../ado/reference/ado-api/field-object.md)オブジェクトの[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)のコレクションに追加される動的プロパティです。  
  
## <a name="usage"></a>使用法  
  
```  
Dim rs As New Recordset  
Dim fld As Field  
rs.CursorLocation = adUseClient      'Enable index creation  
rs.Fields.Append "Field1", adChar, 35, adFldIsNullable  
rs.Open  
Set fld = rs.Fields(0)  
fld.Properties("Optimize") = True    'Create an index  
fld.Properties("Optimize") = False   'Delete an index  
```  
  
## <a name="applies-to"></a>適用対象  
 [Field オブジェクト](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>参照  
 [Optimize プロパティの例 (VB)](../../../ado/reference/ado-api/optimize-property-example-vb.md)   
 [Optimize プロパティの例 (VC + +)](../../../ado/reference/ado-api/optimize-property-example-vc.md)   
 [Filter プロパティ](../../../ado/reference/ado-api/filter-property.md)   
 [Find メソッド (ADO)](../../../ado/reference/ado-api/find-method-ado.md)   
 [Sort プロパティ](../../../ado/reference/ado-api/sort-property.md)

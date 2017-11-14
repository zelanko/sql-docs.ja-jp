---
title: "(ADO) のプロパティ-動的な最適化 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords:
- Optimize property [ADO]
ms.assetid: a491c4ce-2b04-4c84-be83-3846bde8d16b
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 4aeae41d865e585c4c8b93c86bd6f8e9753eaea1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="optimize-property-dynamic-ado"></a>動的プロパティ (ADO) を最適化します。
インデックスを作成する必要があるかどうかを指定します、[フィールド](../../../ado/reference/ado-api/field-object.md)です。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 取得または設定、**ブール**インデックスを作成するかどうかを示す値。  
  
## <a name="remarks"></a>解説  
 インデックスは、検索や内の値を並べ替え操作のパフォーマンスを向上させることができます、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)です。 インデックスが ADO; 内部明示的にアクセスできない、または、アプリケーションで使用します。  
  
 フィールドにインデックスを作成するには設定、**最適化**プロパティを**True**です。 インデックスを削除するには、このプロパティを設定**False**です。  
  
 **最適化**に動的なプロパティが追加、[フィールド](../../../ado/reference/ado-api/field-object.md)オブジェクト[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)コレクションと、 [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) にプロパティが設定されている**adUseClient**です。  
  
## <a name="usage"></a>使用方法  
  
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
 [プロパティの例 (VB) の最適化します。](../../../ado/reference/ado-api/optimize-property-example-vb.md)   
 [プロパティの例 (vc++) を最適化します。](../../../ado/reference/ado-api/optimize-property-example-vc.md)   
 [プロパティをフィルター処理します。](../../../ado/reference/ado-api/filter-property.md)   
 [Find メソッド (ADO)](../../../ado/reference/ado-api/find-method-ado.md)   
 [並べ替えのプロパティ](../../../ado/reference/ado-api/sort-property.md)


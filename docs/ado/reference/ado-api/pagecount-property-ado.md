---
title: PageCount プロパティ (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::PageCount
helpviewer_keywords:
- PageCount property [ADO]
ms.assetid: b601b56c-0ac4-44ee-bc91-c3d2d104f00a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ea893a019ab6d1333cecc5da5f1f66928467adfc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67931784"
---
# <a name="pagecount-property-ado"></a>PageCount プロパティ (ADO)
[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトに格納されているデータのページ数を示します。  
  
## <a name="return-value"></a>戻り値  
 **レコードセット**内のページ数を示す**Long 型**の値を返します。  
  
## <a name="remarks"></a>解説  
 **PageCount**プロパティを使用して、**レコードセット**オブジェクトに含まれるデータのページ数を確認します。 *ページ*は、サイズが[PageSize](../../../ado/reference/ado-api/pagesize-property-ado.md)プロパティ設定と等しいレコードのグループです。 **PageSize**値よりも少数のレコードがあるため、最後のページが不完全な場合でも、 **PageCount**値の追加ページとしてカウントされます。 **Recordset**オブジェクトがこのプロパティをサポートしていない場合、 **PageCount**がわからないであることを示すために、値は-1 になります。  
  
 ページ機能の詳細については、「 **PageSize**プロパティと[AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md)プロパティ」を参照してください。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [AbsolutePage、PageCount、および PageSize プロパティの例 (VB)](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vb.md)   
 [AbsolutePage、PageCount、および PageSize プロパティの例 (VC + +)](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vc.md)   
 [AbsolutePage プロパティ (ADO)](../../../ado/reference/ado-api/absolutepage-property-ado.md)   
 [PageSize プロパティ (ADO)](../../../ado/reference/ado-api/pagesize-property-ado.md)   
 [RecordCount プロパティ (ADO)](../../../ado/reference/ado-api/recordcount-property-ado.md)

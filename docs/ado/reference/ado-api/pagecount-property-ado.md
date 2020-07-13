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
author: rothja
ms.author: jroth
ms.openlocfilehash: 7ebb85eee8ea976f1ef078ebfe22eca195081bba
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82762006"
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

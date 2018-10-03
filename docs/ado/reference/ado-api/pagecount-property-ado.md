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
manager: craigg
ms.openlocfilehash: d7785ad6c1ad97af1517a01888816c76ade42e0f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47602480"
---
# <a name="pagecount-property-ado"></a>PageCount プロパティ (ADO)
データのページの数を示します、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトが含まれています。  
  
## <a name="return-value"></a>戻り値  
 返します、**長い**内のページの数を示す値、**レコード セット**します。  
  
## <a name="remarks"></a>コメント  
 使用して、 **PageCount**プロパティのデータの数ページには、**レコード セット**オブジェクト。 *ページ*レコードと同じサイズのグループ、 [PageSize](../../../ado/reference/ado-api/pagesize-property-ado.md)プロパティの設定。 少ないレコードがあるため、最後のページが完了しない場合でも、 **PageSize**で追加のページとしてカウントされますが、値、 **PageCount**値。 場合、 **Recordset**オブジェクトがこのプロパティをサポートしていません、いることを示す-1 になります、 **PageCount**決められていません。  
  
 参照してください、 **PageSize**と[AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md)詳細のページの機能のプロパティ。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [AbsolutePage、PageCount、PageSize プロパティの例 (VB)](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vb.md)   
 [AbsolutePage、PageCount、PageSize プロパティの例 (vc++)](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vc.md)   
 [AbsolutePage プロパティ (ADO)](../../../ado/reference/ado-api/absolutepage-property-ado.md)   
 [PageSize プロパティ (ADO)](../../../ado/reference/ado-api/pagesize-property-ado.md)   
 [RecordCount プロパティ (ADO)](../../../ado/reference/ado-api/recordcount-property-ado.md)

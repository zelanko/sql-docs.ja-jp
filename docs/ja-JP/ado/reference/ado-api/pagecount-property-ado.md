---
title: PageCount プロパティ (ADO) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::PageCount
helpviewer_keywords:
- PageCount property [ADO]
ms.assetid: b601b56c-0ac4-44ee-bc91-c3d2d104f00a
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0de2e6f7d1865821ec3ff29f0b7d0b8a47ad0856
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="pagecount-property-ado"></a>PageCount プロパティ (ADO)
データのページ数を示す、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトが含まれます。  
  
## <a name="return-value"></a>戻り値  
 返します、**長い**内のページの数を示す値、 **Recordset**です。  
  
## <a name="remarks"></a>解説  
 使用して、 **PageCount**プロパティ内のデータのページ数を調べること、 **Recordset**オブジェクト。 *ページ*レコードと同じサイズのグループ、 [PageSize](../../../ado/reference/ado-api/pagesize-property-ado.md)プロパティの設定。 も少ないレコードがあるため、最後のページが完了していない場合でも、 **PageSize**値で追加のページとして数えられます、 **PageCount**値。 場合、 **Recordset**オブジェクトでは、このプロパティはサポートされません、値があることを示す-1 になります、 **PageCount**決められていません。  
  
 参照してください、 **PageSize**と[と、AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md)詳細のページの機能のプロパティです。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [AbsolutePage、PageCount、および PageSize のプロパティの例 (VB)](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vb.md)   
 [AbsolutePage、PageCount、および PageSize のプロパティの例 (vc++)](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vc.md)   
 [AbsolutePage プロパティ (ADO)](../../../ado/reference/ado-api/absolutepage-property-ado.md)   
 [PageSize プロパティ (ADO)](../../../ado/reference/ado-api/pagesize-property-ado.md)   
 [RecordCount プロパティ (ADO)](../../../ado/reference/ado-api/recordcount-property-ado.md)

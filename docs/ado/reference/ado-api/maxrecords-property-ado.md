---
title: MaxRecords プロパティ (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::MaxRecords
helpviewer_keywords:
- MaxRecords property [ADO]
ms.assetid: 20c76571-8c9a-482c-a99e-726ab1d93f8b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5acd8997af6993a49ac4cbcca6e3b4c8bd26acfd
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67932232"
---
# <a name="maxrecords-property-ado"></a>MaxRecords プロパティ (ADO)
クエリから[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)に返されるレコードの最大数を示します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 返されるレコードの最大数を示す**Long 型**の値を設定または返します。 既定値はゼロ (**0**) です。これは制限がないことを意味します。  
  
## <a name="remarks"></a>Remarks  
 データソースからプロバイダーが返すレコードの数を制限するには、 **MaxRecords**プロパティを使用します。 このプロパティの既定の設定は0です。これは、プロバイダーが要求されたすべてのレコードを返すことを意味します。  
  
 レコードセットが開いている場合は、**レコードセット**が閉じられ、読み取り専用になっている場合、 **MaxRecords**プロパティは読み取り/書き込み可能です。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [MaxRecords プロパティの例 (VB)](../../../ado/reference/ado-api/maxrecords-property-example-vb.md)   
 [MaxRecords プロパティの例 (VC++)](../../../ado/reference/ado-api/maxrecords-property-example-vc.md)   

---
title: "MaxRecords プロパティ (ADO) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Recordset15::MaxRecords
helpviewer_keywords:
- MaxRecords property [ADO]
ms.assetid: 20c76571-8c9a-482c-a99e-726ab1d93f8b
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7d6991928fdf3c284f7039b75f96a95fd93e0be3
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="maxrecords-property-ado"></a>MaxRecords プロパティ (ADO)
返されるレコードの最大数を示す、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)クエリからです。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 取得または設定、**長い**返されるレコードの最大数を示す値。 既定値は 0 (**0**)、これは無制限を意味します。  
  
## <a name="remarks"></a>解説  
 使用して、 **MaxRecords**プロバイダー データ ソースから返すレコードの数を制限するプロパティです。 このプロパティの既定値は 0 で、プロバイダーが要求されたすべてのレコードを返すことを意味します。  
  
 **MaxRecords**プロパティが読み取り/書き込み時に、 **Recordset**が開いているときに閉じており、読み取り専用です。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [MaxRecords プロパティの例 (VB)](../../../ado/reference/ado-api/maxrecords-property-example-vb.md)   
 [MaxRecords プロパティの例 (VC++)](../../../ado/reference/ado-api/maxrecords-property-example-vc.md)   

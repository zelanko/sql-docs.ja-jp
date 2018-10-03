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
manager: craigg
ms.openlocfilehash: ac5097a8692ed7a9e6566707354112547c5a619c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47789400"
---
# <a name="maxrecords-property-ado"></a>MaxRecords プロパティ (ADO)
返されるレコードの最大数を示す、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)クエリから。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 設定または取得を**長い**返されるレコードの最大数を示す値。 既定値は 0 (**0**)、これは無制限を意味します。  
  
## <a name="remarks"></a>コメント  
 使用して、 **MaxRecords**プロパティをデータ ソースから、プロバイダーが返すレコードの数を制限します。 このプロパティの既定値は 0 で、プロバイダーが要求されたすべてのレコードを返します。  
  
 **MaxRecords**プロパティが読み取り/書き込み時に、**レコード セット**が開いているときに閉じており、読み取り専用です。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [MaxRecords プロパティの例 (VB)](../../../ado/reference/ado-api/maxrecords-property-example-vb.md)   
 [MaxRecords プロパティの例 (VC++)](../../../ado/reference/ado-api/maxrecords-property-example-vc.md)   

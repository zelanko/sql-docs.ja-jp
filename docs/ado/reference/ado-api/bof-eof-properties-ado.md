---
description: BOF、EOF プロパティ (ADO)
title: BOF、EOF プロパティ (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::BOF
- Recordset15::EOF
helpviewer_keywords:
- EOF property [ADO]
- BOF property [ADO]
ms.assetid: 36c31ab2-f3b6-4281-89b6-db7e04e38fd2
author: rothja
ms.author: jroth
ms.openlocfilehash: a10ef4731db0e469743d09d9e3b35463d03e7020
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88451132"
---
# <a name="bof-eof-properties-ado"></a>BOF、EOF プロパティ (ADO)
-   **BOF** 現在のレコード位置が、 [レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md) オブジェクトの最初のレコードの前にあることを示します。  
  
-   **EOF** 現在のレコード位置が、 **レコードセット** オブジェクトの最後のレコードの後であることを示します。  
  
## <a name="return-value"></a>戻り値  
 **BOF**プロパティと**EOF**プロパティは、**ブール**値を返します。  
  
## <a name="remarks"></a>解説  
 **Recordset**オブジェクトにレコードが含まれているかどうか、またはレコード間の移動時にレコード**セット**オブジェクトの制限を超えていないかどうかを判断するには、 **BOF**プロパティと**EOF**プロパティを使用します。  
  
 **BOF**プロパティは、現在のレコード位置が最初のレコードの前にある場合は**True** (-1) を返し、現在のレコード位置が最初のレコードの前後にある場合は**False** (0) を返します。  
  
 **EOF**プロパティは、現在のレコード位置が最後のレコードの後にある場合は**True**を返し、現在のレコード位置が最後のレコードの前または最後のレコードの前にある場合は**False**を返します。  
  
 **BOF**プロパティまたは**EOF**プロパティのいずれかが**True**の場合、現在のレコードは存在しません。  
  
 レコードを含まない**レコードセット**オブジェクトを開くと、 **BOF**プロパティと**EOF**プロパティが**True**に設定されます (**レコードセット**のこの状態の詳細については、「 [RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md) 」プロパティを参照してください)。 少なくとも1つのレコードを含むレコード **セット** オブジェクトを開くと、最初のレコードが現在のレコードになり、 **BOF** プロパティと **EOF** プロパティは **False**になります。  
  
 **Recordset**オブジェクト内の最後のレコードを削除すると、現在のレコードの位置を変更しようとしたときに、 **BOF**プロパティと**EOF**プロパティが**False**のままになる場合があります。  
  
 次の表は、 **BOF**プロパティと**EOF**プロパティのさまざまな組み合わせで許可される**移動**方法を示しています。  
  
||MoveFirst<br /><br /> MoveLast|MovePrevious<br /><br /> < 0 に移動|0の移動|MoveNext<br /><br /> > 0 に移動|  
|------|-----------------------------|---------------------------------|------------|-----------------------------|  
|**BOF** =**True**、 **EOF** = **False**|許可|エラー|エラー|許可|  
|**BOF** =**False**、 **EOF** = **True**|許可|許可|エラー|エラー|  
|両方 **True**|エラー|エラー|エラー|エラー|  
|両方 **False**|許可|許可|許可|許可|  
  
 **Move**メソッドを許可しても、メソッドがレコードを正常に見つけることは保証されません。これは、指定された**Move**メソッドを呼び出すことによってエラーが生成されないことを意味します。  
  
 次の表は、さまざまな**Move**メソッドを呼び出してもレコードを正常に見つけることができない場合に、 **BOF**プロパティと**EOF**プロパティの設定がどのように行われるかを示しています。  
  
||BOF|EOF|  
|------|---------|---------|  
|**MoveFirst**、 **MoveLast**|**True**に設定|**True**に設定|  
|0の**移動**|変更なし|変更なし|  
|**MovePrevious**、 **移動** < 0|**True**に設定|変更なし|  
|**MoveNext**、 **移動** > 0|変更なし|**True**に設定|  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [BOF、EOF、および Bookmark プロパティの例 (VB)](../../../ado/reference/ado-api/bof-eof-and-bookmark-properties-example-vb.md)   
 [BOF、EOF、および Bookmark プロパティの例 (VC + +)](../../../ado/reference/ado-api/bof-eof-and-bookmark-properties-example-vc.md)   

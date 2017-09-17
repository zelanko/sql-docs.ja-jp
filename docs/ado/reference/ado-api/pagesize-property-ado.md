---
title: "PageSize プロパティ (ADO) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Recordset15::PageSize
helpviewer_keywords:
- PageSize property [ADO]
ms.assetid: e57930a6-46c4-4a17-a3b6-f79e94d5c9c7
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: fde7e53b844ece01f85b7ecba7e309a71107029d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="pagesize-property-ado"></a>PageSize プロパティ (ADO)
レコードの数を構成することを示します。 1 つのページで、[レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md)です。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 取得または設定、**長い**をページ上のレコードの数を示す値。 既定値は**10**です。  
  
## <a name="remarks"></a>解説  
 使用して、 **PageSize**データの論理ページを構成するレコード数を決定するプロパティです。 使用するページ サイズを確立することができます、[と、AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md)プロパティを特定のページの最初のレコードに移動します。 これは、一度にレコード数を表示する、データのページにユーザーを許可するときに Web サーバーのシナリオで役に立ちます。  
  
 このプロパティは、いつでも設定でき、特定のページの最初のレコードの場所を計算するための値が使用されます。  
  
## <a name="applies-to"></a>適用対象  
 [レコード セット オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [AbsolutePage、PageCount、および PageSize のプロパティの例 (VB)](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vb.md)   
 [AbsolutePage、PageCount、および PageSize のプロパティの例 (vc++)](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vc.md)   
 [AbsolutePage プロパティ (ADO)](../../../ado/reference/ado-api/absolutepage-property-ado.md)   
 [PageCount プロパティ (ADO)](../../../ado/reference/ado-api/pagecount-property-ado.md)


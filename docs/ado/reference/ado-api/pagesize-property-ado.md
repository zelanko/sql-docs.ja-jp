---
title: "PageSize プロパティ (ADO) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: Recordset15::PageSize
helpviewer_keywords: PageSize property [ADO]
ms.assetid: e57930a6-46c4-4a17-a3b6-f79e94d5c9c7
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9c0417012a1c68d0a3e3951a11f3a9ec84d8e89e
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="pagesize-property-ado"></a>PageSize プロパティ (ADO)
レコードの数を構成することを示します。 1 つのページで、[レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md)です。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 取得または設定、**長い**をページ上のレコードの数を示す値。 既定値は**10**です。  
  
## <a name="remarks"></a>解説  
 使用して、 **PageSize**データの論理ページを構成するレコード数を決定するプロパティです。 使用するページ サイズを確立することができます、[と、AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md)プロパティを特定のページの最初のレコードに移動します。 これは、一度にレコード数を表示する、データのページにユーザーを許可するときに Web サーバーのシナリオで役に立ちます。  
  
 このプロパティは、いつでも設定でき、特定のページの最初のレコードの場所を計算するための値が使用されます。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [AbsolutePage、PageCount、および PageSize のプロパティの例 (VB)](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vb.md)   
 [AbsolutePage、PageCount、および PageSize のプロパティの例 (vc++)](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vc.md)   
 [AbsolutePage プロパティ (ADO)](../../../ado/reference/ado-api/absolutepage-property-ado.md)   
 [PageCount プロパティ (ADO)](../../../ado/reference/ado-api/pagecount-property-ado.md)

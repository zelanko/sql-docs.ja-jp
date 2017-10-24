---
title: "AbsolutePage プロパティ (ADO) |Microsoft ドキュメント"
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
- Recordset15::AbsolutePage
helpviewer_keywords:
- AbsolutePage property [ADO]
ms.assetid: ddb58a35-ec3a-423c-a504-3c65e62c23d4
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 54d429f0920da7f68bcea54b72077b96d6d198f7
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="absolutepage-property-ado"></a>AbsolutePage プロパティ (ADO)
現在のレコードがどのページが存在することを示します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 32 ビット コードの場合は、設定または取得、**長い**値を 1 ~ 内のページの数、[レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト ([PageCount](../../../ado/reference/ado-api/pagecount-property-ado.md)) のいずれかを返しますまたは、 [PositionEnum](../../../ado/reference/ado-api/positionenum.md)値。  
  
 64 ビット コードでは、64 ビット値の記憶域を提供するデータ型を使用します。 いずれかを使用するなど、**長い**または別の値は 64 ビット長 DBORDINAL などを使用できます。 使用しないでください**PositionEnum**値は 32 ビットの長さに制限されるためです。  
  
## <a name="remarks"></a>解説  
 このプロパティは、現在のレコードが配置されているページ数を指定を使用できます。 使用して、 [PageSize](../../../ado/reference/ado-api/pagesize-property-ado.md)の行セットの合計数を論理的に分割するプロパティ、 **Recordset**オブジェクトを一連のページ、それぞれと等しいレコードの数を持つ**PageSize**(を除く、最後のページ、少数のレコードを持つ場合もあります)。 プロバイダーは、このプロパティを使用するための適切な機能をサポートする必要があります。  
  
-   取得または設定するときに、**と、AbsolutePage**プロパティ、ADO の使用、 [AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md)プロパティおよび[PageSize](../../../ado/reference/ado-api/pagesize-property-ado.md)次のようにまとめてプロパティ。  
  
-   取得する、**と、AbsolutePage**、ADO をまず取得、 **AbsolutePosition**、によってこれを分割し、 **PageSize**です。  
  
-   設定する、**と、AbsolutePage**、ADO 移動、 **AbsolutePosition**次のように: これを乗算し、 **PageSize**によって新しい**と、AbsolutePage**値し、値に 1 を追加します。 内の現在の位置が結果として、 **Recordset**が正常に設定した後**と、AbsolutePage**は、そのページの最初のレコードです。  
  
 同様に、 **AbsolutePosition**プロパティ、**と、AbsolutePage**は 1 に基づいており、現在のレコードが最初のレコードが 1 と等しい、 **Recordset**です。 特定のページの最初のレコードに移動するには、このプロパティを設定します。 ページの合計数を取得、 **PageCount**プロパティです。  
  
## <a name="applies-to"></a>適用対象  
 [レコード セット オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [AbsolutePage、PageCount、および PageSize のプロパティの例 (VB)](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vb.md)   
 [AbsolutePage、PageCount、および PageSize のプロパティの例 (vc++)](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vc.md)   
 [AbsolutePosition プロパティ (ADO)](../../../ado/reference/ado-api/absoluteposition-property-ado.md)   
 [PageCount プロパティ (ADO)](../../../ado/reference/ado-api/pagecount-property-ado.md)   
 [PageSize プロパティ (ADO)](../../../ado/reference/ado-api/pagesize-property-ado.md)


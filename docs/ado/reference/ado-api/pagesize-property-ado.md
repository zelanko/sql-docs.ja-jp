---
description: PageSize プロパティ (ADO)
title: PageSize プロパティ (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::PageSize
helpviewer_keywords:
- PageSize property [ADO]
ms.assetid: e57930a6-46c4-4a17-a3b6-f79e94d5c9c7
author: rothja
ms.author: jroth
ms.openlocfilehash: 2c073d0ef7cceb74864b7f526ef9a5283ca946a7
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2020
ms.locfileid: "88773531"
---
# <a name="pagesize-property-ado"></a>PageSize プロパティ (ADO)
レコード [セット](./recordset-object-ado.md)内の1つのページを構成するレコードの数を示します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 ページ上のレコード数を示す **Long 型** の値を設定または返します。 既定値は **10**です。  
  
## <a name="remarks"></a>解説  
 データの論理ページを構成するレコードの数を確認するには、 **PageSize** プロパティを使用します。 ページサイズを設定すると、 [AbsolutePage](./absolutepage-property-ado.md) プロパティを使用して、特定のページの最初のレコードに移動できます。 これは、ユーザーがデータをページごとに表示し、一度に特定の数のレコードを表示できるようにする場合に、Web サーバーのシナリオで役立ちます。  
  
 このプロパティはいつでも設定でき、その値は特定のページの最初のレコードの位置を計算するために使用されます。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](./recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [AbsolutePage、PageCount、および PageSize プロパティの例 (VB)](./absolutepage-pagecount-and-pagesize-properties-example-vb.md)   
 [AbsolutePage、PageCount、および PageSize プロパティの例 (VC + +)](./absolutepage-pagecount-and-pagesize-properties-example-vc.md)   
 [AbsolutePage プロパティ (ADO)](./absolutepage-property-ado.md)   
 [PageCount プロパティ (ADO)](./pagecount-property-ado.md)
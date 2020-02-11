---
title: MarshalOptions プロパティ (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::MarshalOptions
helpviewer_keywords:
- MarshalOptions property [ADO]
ms.assetid: 390c8abf-133e-40da-8b99-8f748a983e4f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0212f3b4cb663bd56adaa1bdbc3ab6675c3ce888
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67932268"
---
# <a name="marshaloptions-property-ado"></a>MarshalOptions プロパティ (ADO)
サーバーにマーシャリングされるレコード[セット](../../../ado/reference/ado-api/recordset-object-ado.md)のレコードを示します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 [Marshaloptionsenum](../../../ado/reference/ado-api/marshaloptionsenum.md)値を設定または返します。 既定値は**Admarshalall**です。  
  
## <a name="remarks"></a>解説  
 クライアント側の[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)を使用すると、クライアントで変更されたレコードが、スレッドまたはプロセスの境界を越えてパッケージ化および送信するプロセスであるマーシャリングと呼ばれる手法によって、中間層または Web サーバーに書き戻されます。 変更したリモートデータを中間層または Web サーバーに戻すためにマーシャリングする場合、 **Marshaloptions**プロパティを設定するとパフォーマンスが向上します。  
  
> [!NOTE]
>  **リモートデータサービスの使用状況**このプロパティは、クライアント側の**レコードセット**でのみ使用されます。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [MarshalOptions プロパティの例 (VB)](../../../ado/reference/ado-api/marshaloptions-property-example-vb.md)   
 [MarshalOptions プロパティの例 (VC++)](../../../ado/reference/ado-api/marshaloptions-property-example-vc.md)   

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
manager: craigg
ms.openlocfilehash: 35646314a5c52e86284326ee91776b5afe2a0d17
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47625080"
---
# <a name="marshaloptions-property-ado"></a>MarshalOptions プロパティ (ADO)
レコードのことを示します、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)サーバーにマーシャ リングされます。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 設定または取得を[MarshalOptionsEnum](../../../ado/reference/ado-api/marshaloptionsenum.md)値。 既定値は**adMarshalAll**します。  
  
## <a name="remarks"></a>コメント  
 クライアント側を使用する場合[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)クライアントで変更されたレコードは、パッケージ化し、インターフェイス メソッドを送信するプロセスのマーシャ リングと呼ばれる手法を使って Web サーバー、中間層に書き戻されますスレッドまたはプロセスの境界を越えてパラメーター。 設定、 **MarshalOptions**プロパティが変更されたリモート データが中間層または Web サーバーに更新するためにマーシャ リングするときにパフォーマンスを向上できます。  
  
> [!NOTE]
>  **リモート データ サービスの使用状況**このプロパティはクライアント側でのみ使用**Recordset**します。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [MarshalOptions プロパティの例 (VB)](../../../ado/reference/ado-api/marshaloptions-property-example-vb.md)   
 [MarshalOptions プロパティの例 (VC++)](../../../ado/reference/ado-api/marshaloptions-property-example-vc.md)   

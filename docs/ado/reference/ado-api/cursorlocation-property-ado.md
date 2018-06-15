---
title: CursorLocation プロパティ (ADO) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::CursorLocation
- Recordset15::CursorLocation
helpviewer_keywords:
- CursorLocation property [ADO]
ms.assetid: 39c8d86e-7ee9-4182-be5e-aad5ce952f84
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a720586cc2ee6f866565fe9e43382395bcb44e65
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35277281"
---
# <a name="cursorlocation-property-ado"></a>CursorLocation プロパティ (ADO)
カーソル サービスの場所を示します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 取得または設定、**長い**値のいずれかに設定できる、 [CursorLocationEnum](../../../ado/reference/ado-api/cursorlocationenum.md)値。  
  
## <a name="remarks"></a>コメント  
 このプロパティでは、プロバイダーにアクセス可能な各種のカーソル ライブラリを選択することができます。 通常、間、サーバーでクライアント側カーソル ライブラリまたは配置されているいずれかを使用することができます。  
  
 このプロパティの設定では、プロパティが設定された後にのみ確立された接続に影響します。 変更、 **CursorLocation**プロパティが既存の接続に影響を与えません。  
  
 カーソルによって返される、 [Execute](../../../ado/reference/ado-api/execute-method-ado-connection.md)メソッドは、この設定を継承します。 **レコード セット**オブジェクトではこの設定を関連付けられた接続を自動的に継承されます。  
  
 このプロパティが読み取り/書き込み、[接続](../../../ado/reference/ado-api/connection-object-ado.md)、閉じられたか[レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md)、読み取り専用で、開いていると**レコード セット**です。  
  
> [!NOTE]
>  **リモートのデータ サービスの使用状況**クライアント側で使用すると**Recordset**または**接続**オブジェクト、 **CursorLocation**プロパティは、にのみ設定できます**adUseClient**です。  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[Connection オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|[Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|  
  
## <a name="see-also"></a>参照  
 [付録 A: プロバイダー](../../../ado/guide/appendixes/appendix-a-providers.md)

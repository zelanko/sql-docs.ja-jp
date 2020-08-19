---
description: CursorLocation プロパティ (ADO)
title: カーソル位置プロパティ (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::CursorLocation
- Recordset15::CursorLocation
helpviewer_keywords:
- CursorLocation property [ADO]
ms.assetid: 39c8d86e-7ee9-4182-be5e-aad5ce952f84
author: rothja
ms.author: jroth
ms.openlocfilehash: 92567057acad1edb0a0571a0057a11a47a3c65d6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88444304"
---
# <a name="cursorlocation-property-ado"></a>CursorLocation プロパティ (ADO)
カーソルサービスの場所を示します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 カーソルのいずれかの[列挙](../../../ado/reference/ado-api/cursorlocationenum.md)値に設定できる**Long 型**の値を設定または返します。  
  
## <a name="remarks"></a>解説  
 このプロパティを使用すると、プロバイダーにアクセスできるさまざまなカーソルライブラリを選択できます。 通常は、クライアント側のカーソルライブラリを使用するか、サーバー上に配置するかを選択できます。  
  
 このプロパティ設定は、プロパティが設定された後にのみ確立される接続に影響します。 **カーソル位置**プロパティを変更しても、既存の接続には影響しません。  
  
 [Execute](../../../ado/reference/ado-api/execute-method-ado-connection.md)メソッドによって返されたカーソルは、この設定を継承します。 **レコードセット** オブジェクトは、関連付けられている接続からこの設定を自動的に継承します。  
  
 このプロパティは、 [接続](../../../ado/reference/ado-api/connection-object-ado.md) または閉じた [レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)に対して読み取り/書き込みを行い、開いている **レコードセット**に対して読み取り専用にします。  
  
> [!NOTE]
>  **リモートデータサービスの使用状況** クライアント側の **レコードセット** または **接続** オブジェクトで使用する場合、[ **カーソルの場所** ] プロパティは **adUseClient**にのみ設定できます。  
  
## <a name="applies-to"></a>適用対象  

:::row:::
    :::column:::
        [Connection オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
    :::column-end:::
    :::column:::
        [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>参照  
 [付録 A: プロバイダー](../../../ado/guide/appendixes/appendix-a-providers.md)

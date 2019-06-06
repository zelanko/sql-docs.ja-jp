---
title: Prompt プロパティ-動的 (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Prompt property [ADO]
ms.assetid: c4f001b5-8d16-4d39-a42e-c0e2faaaceaf
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 4f2c778a6e922477cd8b21251a638d430ce15480
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "66703159"
---
# <a name="prompt-property-dynamic-ado"></a>Prompt プロパティ - 動的 (ADO)
OLE DB プロバイダーが初期化情報をユーザーのメッセージを表示するかどうかを指定します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 設定し、返します、 [ConnectPromptEnum](../../../ado/reference/ado-api/connectpromptenum.md)値。  
  
## <a name="remarks"></a>コメント  
 **プロンプト**、動的なプロパティを追加することは、[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクトの[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)OLE DB プロバイダーでのコレクション。 初期化情報を要求するには、OLE DB プロバイダーは、ダイアログ ボックスをユーザーに通常表示されます。  
  
 動的なプロパティ、[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクトが失われたときに、**接続**が閉じられました。 **プロンプト**再を開く前にプロパティをリセットする必要があります、**接続**既定以外の値を使用します。  
  
> [!NOTE]
>  プロバイダーが、ユーザーをユーザーはできません ダイアログ ボックスに応答するシナリオでのメッセージを表示することを指定しません。 たとえば、ユーザーは、アプリケーションがユーザーのクライアントではなく、サーバー システムで実行されている場合、またはユーザーがログオンしていないシステムで、アプリケーションが実行されている場合に応答できません。 このような場合は、アプリケーションは応答を無期限に待機しをロックしているようです。  
  
## <a name="usage"></a>使用方法  
  
```  
Set cn = New Connection  
cn.Provider = "SQLOLEDB"  
cn.Properties("Prompt") = adPromptNever    ' do not prompt the user  
```  
  
## <a name="applies-to"></a>適用対象  
 [Connection オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)

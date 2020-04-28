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
ms.openlocfilehash: cde7a5ad0324bc7d5cde5e1a794eeb9e2cb3381a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67931570"
---
# <a name="prompt-property-dynamic-ado"></a>Prompt プロパティ - 動的 (ADO)
OLE DB プロバイダーがユーザーに初期化情報の入力を求めるかどうかを指定します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 [ConnectPromptEnum](../../../ado/reference/ado-api/connectpromptenum.md)値を設定して返します。  
  
## <a name="remarks"></a>Remarks  
 **Prompt**は動的プロパティであり、OLE DB プロバイダーによって[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクトの[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)コレクションに追加される場合があります。 初期化情報を要求するために、OLE DB プロバイダーは通常、ユーザーにダイアログボックスを表示します。  
  
 **接続が閉じ**られると、[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクトの動的プロパティは失われます。 既定以外の値を使用するには、**接続**を再度開く前に、 **Prompt**プロパティをリセットする必要があります。  
  
> [!NOTE]
>  ユーザーがダイアログボックスに応答できないシナリオで、プロバイダーがユーザーにメッセージを表示するように指定しないでください。 たとえば、アプリケーションがユーザーのクライアントではなくサーバーシステム上で実行されている場合や、ユーザーがログオンしていないシステムでアプリケーションが実行されている場合は、ユーザーは応答できません。 このような場合、アプリケーションは応答を無期限に待機し、ロックアップしているように見えます。  
  
## <a name="usage"></a>使用方法  
  
```  
Set cn = New Connection  
cn.Provider = "SQLOLEDB"  
cn.Properties("Prompt") = adPromptNever    ' do not prompt the user  
```  
  
## <a name="applies-to"></a>適用対象  
 [Connection オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)

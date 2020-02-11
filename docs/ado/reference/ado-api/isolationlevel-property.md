---
title: IsolationLevel Property |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::IsolationLevel
helpviewer_keywords:
- IsolationLevel property
ms.assetid: ea84e4b2-fbf2-4eef-b9ce-796b22e21800
author: MightyPen
ms.author: genemi
ms.openlocfilehash: dc360bc91e977228a6f9139089a7bfa87d912e1f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67918441"
---
# <a name="isolationlevel-property"></a>IsolationLevel プロパティ
[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクトの分離レベルを示します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 [IsolationLevelEnum](../../../ado/reference/ado-api/isolationlevelenum.md)値を設定または返します。 既定値は**adXactReadCommitted**です。  
  
## <a name="remarks"></a>解説  
 **接続**オブジェクトの分離レベルを設定するには、 **IsolationLevel**プロパティを使用します。 この設定は、次に[BeginTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md)メソッドを呼び出したときまで有効になりません。 要求した分離レベルが使用できない場合、プロバイダーは、 **IsolationLevel**プロパティを更新せずに、次に高い分離レベルを返すことができます。  
  
 **IsolationLevel**プロパティは読み取り/書き込み可能です。  
  
> [!NOTE]
>  **リモートデータサービスの使用状況**クライアント側の**接続**オブジェクトで使用する場合、 **IsolationLevel**プロパティは**adXactUnspecified**にのみ設定できます。 ユーザーはクライアント側キャッシュで切断された**レコードセット**オブジェクトを操作しているため、マルチユーザーの問題が発生する可能性があります。 たとえば、2人のユーザーが同じレコードを更新しようとした場合、リモートデータサービスは、最初にレコードを更新するユーザーに "win" を許可します。 2番目のユーザーの更新要求は、エラーで失敗します。  
  
## <a name="applies-to"></a>適用対象  
 [Connection オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [IsolationLevel と Mode プロパティの例 (VB)](../../../ado/reference/ado-api/isolationlevel-and-mode-properties-example-vb.md)   
 [IsolationLevel と Mode プロパティの例 (VC + +)](../../../ado/reference/ado-api/isolationlevel-and-mode-properties-example-vc.md)   

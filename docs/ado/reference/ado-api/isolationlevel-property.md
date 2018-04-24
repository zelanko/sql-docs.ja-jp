---
title: IsolationLevel プロパティ |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::IsolationLevel
helpviewer_keywords:
- IsolationLevel property
ms.assetid: ea84e4b2-fbf2-4eef-b9ce-796b22e21800
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 667838efdae694c5884552179ad366721ebd4807
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="isolationlevel-property"></a>IsolationLevel プロパティ
分離のレベルを示す、[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクト。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 取得または設定、 [IsolationLevelEnum](../../../ado/reference/ado-api/isolationlevelenum.md)値。 既定値は**adXactReadCommitted**です。  
  
## <a name="remarks"></a>解説  
 使用して、 **IsolationLevel**分離のレベルを設定するプロパティ、**接続**オブジェクト。 この設定は反映されません次回を呼び出すまで、 [BeginTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md)メソッドです。 プロバイダーが更新することがなく、次に高い分離レベルを返す可能性がありますを要求する分離レベルが使用できない場合、 **IsolationLevel**プロパティです。  
  
 **IsolationLevel**読み取り/書き込みプロパティです。  
  
> [!NOTE]
>  **リモートのデータ サービスの使用法**クライアント側で使用すると**接続**オブジェクト、 **IsolationLevel**プロパティにのみ設定できます**adXactUnspecified**です。 ユーザーは切断されているで作業するため**Recordset**でオブジェクトをクライアント側のキャッシュ、マルチ ユーザーの問題がある可能性があります。 たとえば、2 人のユーザーが同じレコードを更新しようとすると、リモートのデータ サービスを使用すると"win"に最初のレコードを更新したユーザー 2 番目のユーザーの更新要求はエラーで失敗します。  
  
## <a name="applies-to"></a>適用対象  
 [Connection オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [IsolationLevel とモードのプロパティの例 (VB)](../../../ado/reference/ado-api/isolationlevel-and-mode-properties-example-vb.md)   
 [IsolationLevel とモードのプロパティの例 (vc++)](../../../ado/reference/ado-api/isolationlevel-and-mode-properties-example-vc.md)   

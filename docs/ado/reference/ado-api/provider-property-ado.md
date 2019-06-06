---
title: プロバイダーのプロパティ (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::get_Provider
- Connection15::PutProvider
- Connection15::put_Provider
- Connection15::GetProvider
- Connection15::Provider
helpviewer_keywords:
- Provider property [ADO]
ms.assetid: 0ff70e72-0061-4ffc-90fb-e3ea23129bb2
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: a8c571bf143d4aa68fc5785b91929635864e9ce8
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "66702877"
---
# <a name="provider-property-ado"></a>Provider プロパティ (ADO)
プロバイダーの名前を示します、[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクト。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 設定または取得を**文字列**プロバイダー名を示す値。  
  
## <a name="remarks"></a>コメント  
 使用して、**プロバイダー**プロパティを設定または接続プロバイダーの名前を取得します。 内容でこのプロパティを設定することできますも、 [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md)プロパティまたは*ConnectionString*の引数、[開く](../../../ado/reference/ado-api/open-method-ado-connection.md)メソッドですただし、プロバイダーを指定します。呼び出し中に複数の場所で、**開く**メソッドは、予期しない結果を持つことができます。 Msdasql プロパティが既定プロバイダーが指定されていない場合 ([Microsoft OLE DB Provider for ODBC](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-odbc.md))。  
  
 **プロバイダー**プロパティは、開いているときに、接続が閉じており、読み取り専用と読み取り/書き込みです。 設定が反映されませんするまで開くか、**接続**オブジェクトまたはアクセス、[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)のコレクション、**接続**オブジェクト。 設定が有効でない場合は、エラーが発生します。  
  
## <a name="applies-to"></a>適用対象  
 [Connection オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [Provider および DefaultDatabase プロパティの例 (VB)](../../../ado/reference/ado-api/provider-and-defaultdatabase-properties-example-vb.md)   
 [Provider および DefaultDatabase プロパティの例 (VB)](../../../ado/reference/ado-api/provider-and-defaultdatabase-properties-example-vb.md)   
 [Microsoft OLE DB Provider for ODBC](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-odbc.md)   
 [付録 A: プロバイダー](../../../ado/guide/appendixes/appendix-a-providers.md)

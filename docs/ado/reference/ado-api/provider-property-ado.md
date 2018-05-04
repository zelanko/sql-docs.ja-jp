---
title: プロバイダーのプロパティ (ADO) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
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
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cc92c70e7f2e995bb828ec7f9b3fcdf1dd16daf3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="provider-property-ado"></a>プロバイダーのプロパティ (ADO)
プロバイダーの名前を示す、[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクト。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 取得または設定、**文字列**プロバイダー名を示す値。  
  
## <a name="remarks"></a>解説  
 使用して、**プロバイダー**プロパティを設定または接続のプロバイダーの名前を取得します。 内容でこのプロパティを設定することできますも、 [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md)プロパティまたは*ConnectionString*の引数、[開く](../../../ado/reference/ado-api/open-method-ado-connection.md)メソッドですただし、プロバイダーを指定します。呼び出し中に複数の場所で、**開く**メソッドは、予期しない結果を持つことができます。 プロパティは既定 MSDASQL にプロバイダーが指定されていない場合 ([Microsoft OLE DB Provider for ODBC](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-odbc.md))。  
  
 **プロバイダー**プロパティが読み取り/書き込みが開いているとき、接続が閉じていて、読み取り専用です。 設定は有効になりませんまで開くか、**接続**オブジェクトまたはアクセス、[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)のコレクション、**接続**オブジェクト。 設定が有効でない場合は、エラーが発生します。  
  
## <a name="applies-to"></a>適用対象  
 [Connection オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [プロバイダーと DefaultDatabase プロパティの例 (VB)](../../../ado/reference/ado-api/provider-and-defaultdatabase-properties-example-vb.md)   
 [プロバイダーと DefaultDatabase プロパティの例 (VB)](../../../ado/reference/ado-api/provider-and-defaultdatabase-properties-example-vb.md)   
 [Microsoft OLE DB Provider for ODBC](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-odbc.md)   
 [付録 A: プロバイダー](../../../ado/guide/appendixes/appendix-a-providers.md)

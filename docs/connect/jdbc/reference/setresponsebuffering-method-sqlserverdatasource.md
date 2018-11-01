---
title: setResponseBuffering メソッド (SQLServerDataSource) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setResponseBuffering(String responseBufferingValue)
apilocation:
- SQLServerDataSource.setResponseBuffering(String responseBufferingValue)
apitype: Assembly
ms.assetid: c9e43ff2-8117-4dca-982d-83c863d0c8e1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b56a2382759825fd296ea70ad2e52cfc858c7166
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47781900"
---
# <a name="setresponsebuffering-method-sqlserverdatasource"></a>setResponseBuffering メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) オブジェクトを使用して作成された接続の応答バッファリング モードを設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void setResponseBuffering(java.lang.String value)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *value*  
  
 バッファリングとストリーミングのモードを含む**文字列**です。 有効なモードは **full** または **adaptive** のいずれかです。モードを表すこれらの文字列では、大文字と小文字のどちらも使用できます。  
  
## <a name="remarks"></a>Remarks  
 **full** 値は、実行時にサーバーから結果全体を読み取ることを示します。  
  
 **adaptive** 値は、必要に応じて最小限のデータをバッファリングすることを示します。 既定のバッファリング モードは **adaptive** 値です。  
  
 詳細については、応答バッファリング モードを使用して、次を参照してください。[アダプティブ バッファリングを使用して](../../../connect/jdbc/using-adaptive-buffering.md)します。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  

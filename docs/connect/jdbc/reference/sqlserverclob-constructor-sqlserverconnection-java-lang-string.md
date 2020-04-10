---
title: SQLServerClob コンストラクター (SQLServerConnection, java.lang.String) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.SQLServerClob (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7058f4f7-ef3e-4d62-90d1-79299708b1eb
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cb6b459f8193daebb69ad67ffaab5beab526f710
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80920389"
---
# <a name="sqlserverclob-constructor-sqlserverconnection-javalangstring"></a>SQLServerClob (SQLServerConnection, java.lang.String) コンストラクター
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  [SQLServerConnection](../../../connect/jdbc/reference/sqlserverclob-class.md) オブジェクトとデータの文字列が渡されたときに、[SQLServerClob](../../../connect/jdbc/reference/sqlserverconnection-class.md) クラスの新しいインスタンスを初期化します。  
  
> [!NOTE]  
>  このメソッドは、JDBC Driver Version 2.0 では非推奨とされました。 代わりに、[SQLServerConnection](../../../connect/jdbc/reference/createclob-method-sqlserverconnection.md) クラスの [createClob](../../../connect/jdbc/reference/sqlserverconnection-class.md) メソッドを使用してください。  
  
## <a name="syntax"></a>構文  
  
```  
  
public SQLServerClob(SQLServerConnection connection,  
                     java.lang.String data)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *connection*  
  
 SQLServerConnection オブジェクト。  
  
 *data*  
  
 CLOB データです。  
  
## <a name="see-also"></a>参照  
 [SQLServerClob のコンストラクター](../../../connect/jdbc/reference/sqlserverclob-constructors.md)   
 [SQLServerClob メンバー](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [SQLServerClob クラス](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  

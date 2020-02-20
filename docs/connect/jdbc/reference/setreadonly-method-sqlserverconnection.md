---
title: setReadOnly メソッド (SQLServerConnection) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.setReadOnly
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: bd11fd50-f092-43a0-a6bc-c63e70cff8da
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bda879ceba5c6f1193ecdfa09995e851c2bcd6e0
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "67973149"
---
# <a name="setreadonly-method-sqlserverconnection"></a>setReadOnly メソッド (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) オブジェクトを読み取り専用モードにして、データベースの最適化を有効にするヒントを JDBC ドライバーに提供します。  
  
> [!NOTE]  
>  このメソッドは、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] ではサポートされていません。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void setReadOnly(boolean readOnly)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *readOnly*  
  
 接続を読み取り専用にする場合は **true** です。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この setReadOnly メソッドは、java.sql.Connection インターフェイスの setReadOnly メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  

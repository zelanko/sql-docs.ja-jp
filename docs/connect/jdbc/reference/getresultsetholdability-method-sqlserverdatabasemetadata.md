---
title: getResultSetHoldability メソッド (SQLServerDatabaseMetaData) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData,getResultSetHoldability
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f0bd6283-83ab-4a0a-b825-ec4cdccf03e1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fd044a5ea530a1b932561fcd1fe60d52b108ad09
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47793751"
---
# <a name="getresultsetholdability-method-sqlserverdatabasemetadata"></a>getResultSetHoldability メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  データベースに対する結果セットの既定の保持機能を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int getResultSetHoldability()  
```  
  
## <a name="return-value"></a>戻り値  
 既定の保持機能を示す **int** です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この getResultSetHoldability メソッドは、java.sql.DatabaseMetaData インターフェイスで getResultSetHoldability メソッドによって指定されます。  
  
 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] を [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースと共に使用している場合、このメソッドは 1 が返されます。これは、定数 ResultSet.HOLD_CURSORS_OVER_COMMIT と等価です。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

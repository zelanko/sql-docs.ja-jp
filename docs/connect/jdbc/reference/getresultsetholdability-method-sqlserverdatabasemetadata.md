---
title: getResultSetHoldability メソッド (SQLServerDatabaseMetaData) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData,getResultSetHoldability
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f0bd6283-83ab-4a0a-b825-ec4cdccf03e1
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 17b464323d950477ed5d2f66fc2b55822258d501
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32837247"
---
# <a name="getresultsetholdability-method-sqlserverdatabasemetadata"></a>getResultSetHoldability メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  データベースに対する結果セットの既定の保持機能を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int getResultSetHoldability()  
```  
  
## <a name="return-value"></a>戻り値  
 **Int**既定の保持機能を示すです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getResultSetHoldability メソッドは、java.sql.DatabaseMetaData インターフェイスの getResultSetHoldability メソッドによって指定されます。  
  
 使用する場合、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]で、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]データベースでは、このメソッドは 1 を返します、これは、ResultSet.HOLD_CURSORS_OVER_COMMIT 定数と等価です。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

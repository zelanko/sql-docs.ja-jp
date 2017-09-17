---
title: "othersDeletesAreVisible メソッド (SQLServerDatabaseMetaData) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerDatabaseMetaData.othersDeletesAreVisible
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c4692a8c-e6b7-4edc-9dad-7af816988de5
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6a25f8ed48aa924601ce0cf0f603cb0bf18c8af4
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="othersdeletesarevisible-method-sqlserverdatabasemetadata"></a>othersDeletesAreVisible メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  他で行われた削除が可視かどうかを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean othersDeletesAreVisible(int type)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *型*  
  
 **Int**を示す結果セットの種類で、java.sql.ResultSet または SQLServerResultSet で定義されている、次の値のいずれかを指定することができます。  
  
## <a name="javasqlresultset-types"></a>java.sql.ResultSet の種類  
 TYPE_FORWARD_ONLY  
  
 TYPE_SCROLL_SENSITIVE  
  
 TYPE_SCROLL_INSENSITIVE  
  
## <a name="sqlserverresultset-types"></a>SQLServerResultSet の種類  
 TYPE_SS_SCROLL_STATIC  
  
 TYPE_SS_SCROLL_KEYSET  
  
 TYPE_SS_DIRECT_FORWARD_ONLY  
  
 TYPE_SS_SERVER_CURSOR_FORWARD_ONLY  
  
 TYPE_SS_SCROLL_DYNAMIC  
  
## <a name="return-value"></a>戻り値  
 **true**削除が可視の場合。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この othersDeletesAreVisible メソッドは、java.sql.DatabaseMetaData インターフェイスの othersDeletesAreVisible メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

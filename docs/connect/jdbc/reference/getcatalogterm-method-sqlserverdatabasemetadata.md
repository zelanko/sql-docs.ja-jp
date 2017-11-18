---
title: "getCatalogTerm メソッド (SQLServerDatabaseMetaData) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerDatabaseMetaData.getCatalogTerm
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 0aa5d372-16aa-4790-a8f6-f8b742798f8f
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2195081eb25174092c195ac8bcfd1878c545cd8b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="getcatalogterm-method-sqlserverdatabasemetadata"></a>getCatalogTerm メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  データベース ベンダーが "カタログ" の代わりに使用している用語を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.lang.String getCatalogTerm()  
```  
  
## <a name="return-value"></a>戻り値  
 A**文字列**カタログの用語を含むです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getCatalogTerm メソッドは、java.sql.DatabaseMetaData インターフェイスの getCatalogTerm メソッドによって指定されます。  
  
 使用する場合、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]で、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]データベースでは、このメソッドは用語「データベース」です。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  


---
title: "getUDTs メソッド (SQLServerDatabaseMetaData) |Microsoft ドキュメント"
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
- SQLServerDatabaseMetaData.getUDTs
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c4396453-dcb0-4132-8325-06b3c7896b3b
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a5d15d63bbb6d39696664331d6eb29b225ac74d2
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="getudts-method-sqlserverdatabasemetadata"></a>getUDTs メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  特定のスキーマで定義されているユーザー定義型の記述を取得します。  
  
> [!NOTE]  
>  このメソッドは、現在ではサポートされません[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]です。 このメソッドを使用すると、常に空の結果セットが返されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.sql.ResultSet getUDTs(java.lang.String catalog,  
                                  java.lang.String schemaPattern,  
                                  java.lang.String typeNamePattern,  
                                  int[] types)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *カタログ*  
  
 A**文字列**カタログ名を格納しています。  
  
 *schemaPattern*  
  
 A**文字列**スキーマ名のパターンを格納しています。  
  
 *typeNamePattern*  
  
 A**文字列**型名のパターンを格納しています。  
  
 *型*  
  
 対象となるデータ型が含まれている int 配列です。 null は、すべての型が対象となることを示します。  
  
## <a name="return-value"></a>戻り値  
 A [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getUDTs メソッドは、java.sql.DatabaseMetaData インターフェイスの getUDTs メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  


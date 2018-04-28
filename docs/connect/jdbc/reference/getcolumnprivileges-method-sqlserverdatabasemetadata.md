---
title: getColumnPrivileges メソッド (SQLServerDatabaseMetaData) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
apiname:
- SQLServerDatabaseMetaData.getColumnPrivileges
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4ab6a671-9573-4b95-8c23-364306c60d25
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6b88af8e4af62f556bd22a3769d587ad214a1273
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="getcolumnprivileges-method-sqlserverdatabasemetadata"></a>getColumnPrivileges メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  テーブルの列に対するアクセス権の記述を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.sql.ResultSet getColumnPrivileges(java.lang.String catalog,  
                                              java.lang.String schema,  
                                              java.lang.String table,  
                                              java.lang.String col)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *catalog*  
  
 A**文字列**カタログ名を格納しています。  
  
 *schema*  
  
 A**文字列**スキーマ名を格納しています。  
  
 *テーブル*  
  
 A**文字列**テーブル名を格納しています。  
  
 *col*  
  
 A**文字列**列名のパターンを格納しています。  
  
## <a name="return-value"></a>戻り値  
 A [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getColumnPrivileges メソッドは、java.sql.DatabaseMetaData インターフェイスの getColumnPrivileges メソッドによって指定されます。  
  
 GetColumnPrivileges メソッドによって返される結果セットには、次の情報が含まれます。  
  
|名前|型|Description|  
|----------|----------|-----------------|  
|TABLE_CAT|**文字列**|カタログ名。|  
|TABLE_SCHEM|**文字列**|テーブル スキーマ名です。|  
|TABLE_NAME|**文字列**|テーブル名。|  
|COLUMN_NAME|**文字列**|列名。|  
|GRANTOR|**文字列**|アクセス許可を与えるオブジェクトです。|  
|GRANTEE|**文字列**|アクセスを受け入れるオブジェクトです。|  
|PRIVILEGE|**文字列**|許可されたアクセスの種類です。|  
|IS_GRANTABLE|**文字列**|権限を与えられたユーザーが他のユーザーへのアクセスを許可できるかどうかを示します。|  
  
> [!NOTE]  
>  GetColumnPrivileges メソッドによって返されるデータに関する詳細については、「sp_column_privileges (TRANSACT-SQL)」を参照してください[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]オンライン ブック。  
  
## <a name="example"></a>例  
 次の例では、getColumnPrivileges メソッド内の Person.Contact テーブルの FirstName 列に対するアクセス権を使用して、[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]サンプル データベース。  
  
```  
public static void executeGetColumnPrivileges(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getColumnPrivileges("AdventureWorks", "Person", "Contact", "FirstName");  
      ResultSetMetaData rsmd = rs.getMetaData();  
  
      // Display the result set data.  
      int cols = rsmd.getColumnCount();  
      while(rs.next()) {  
         for (int i = 1; i <= cols; i++) {  
            System.out.println(rs.getString(i));  
         }  
      }  
      rs.close();  
}  
  
   catch (Exception e) {  
      e.printStackTrace();  
   }  
}  
```  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

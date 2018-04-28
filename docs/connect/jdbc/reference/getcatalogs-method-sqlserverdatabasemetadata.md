---
title: getCatalogs メソッド (SQLServerDatabaseMetaData) |Microsoft ドキュメント
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
- SQLServerDatabaseMetaData.getCatalogs
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7f8bd0f1-f340-4bb9-b559-0a6176124033
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3476342588d2639408cbc733ea322ae07fc0062b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="getcatalogs-method-sqlserverdatabasemetadata"></a>getCatalogs メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  接続されたサーバーで使用できるカタログ名を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.sql.ResultSet getCatalogs()  
```  
  
## <a name="return-value"></a>戻り値  
 A [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getCatalogs メソッドは、java.sql.DatabaseMetaData インターフェイスの getCatalogs メソッドによって指定されます。  
  
> [!NOTE]  
>  SQL Azure の呼び出しに、master データベースに接続する必要があります**SQLServerDatabaseMetaData.getCatalogs**です。 SQL Azure は、ユーザー データベースからカタログのセット全体を返すことをサポートしていません。 **SQLServerDatabaseMetaData.getCatalogs** sys.databases ビューを使用して、カタログを取得します。 アクセス許可の説明を参照してください[sys.databases (SQL Azure データベース)](http://go.microsoft.com/fwlink/?LinkId=217396)を理解しておく**SQLServerDatabaseMetaData.getCatalogs** SQL Azure で動作します。  
  
 GetCatalogs メソッドによって返される結果セットには、次の情報が含まれます。  
  
|名前|型|Description|  
|----------|----------|-----------------|  
|TABLE_CAT|**文字列**|システム データベースを含む、カタログの名前[!INCLUDE[msCoName](../../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]です。|  
  
## <a name="example"></a>例  
 次の例に含まれているすべてのデータベースの名前を取得する getCatalogs メソッドを使用して[!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]、システム データベースを含むです。  
  
```  
public static void executeGetCatalogs(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getCatalogs();  
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
  
  

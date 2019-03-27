---
title: getCatalogs メソッド (SQLServerDatabaseMetaData) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getCatalogs
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7f8bd0f1-f340-4bb9-b559-0a6176124033
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a7ad65c0563598b06b88d2d3f744ade4f37a8fc8
ms.sourcegitcommit: 7d4a3fc0f2622cbc6930d792be4a9b3fcac4c4b6
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 03/21/2019
ms.locfileid: "58305950"
---
# <a name="getcatalogs-method-sqlserverdatabasemetadata"></a>getCatalogs メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  接続されたサーバーで使用できるカタログ名を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.sql.ResultSet getCatalogs()  
```  
  
## <a name="return-value"></a>戻り値  
 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) オブジェクトです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この getCatalogs メソッドは、java.sql.DatabaseMetaData インターフェイスの getCatalogs メソッドで規定されています。  
  
> [!NOTE]  
>  SQL Azure でを呼び出す、master データベースに接続する必要があります**SQLServerDatabaseMetaData.getCatalogs**します。 SQL Azure では、ユーザー データベースからカタログ全体を返すことがサポートされていません。 **SQLServerDatabaseMetaData.getCatalogs** sys.databases ビューを使用して、カタログを取得します。 権限に関する情報を参照してください[sys.database_usage (Azure SQL データベース)](../../../relational-databases/system-catalog-views/sys-database-usage-azure-sql-database.md)を理解しておく**SQLServerDatabaseMetaData.getCatalogs** SQL Azure で動作します。  
  
 getCatalogs メソッドによって返される結果セットには、次の情報が含まれます。  
  
|[オブジェクト名]|型|[説明]|  
|----------|----------|-----------------|  
|TABLE_CAT|**String**|[!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のシステム データベースを含むカタログの名前です。|  
  
## <a name="example"></a>例  
 次の例では、getCatalogs メソッドを使用して、[!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に含まれるすべてのデータベース (システム データベースを含む) の名前を返す方法を示します。  
  
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
  
  

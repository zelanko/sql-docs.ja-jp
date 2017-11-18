---
title: "データ ソースのサンプル |Microsoft ドキュメント"
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
ms.assetid: b4a933ee-f2c6-4e0d-a96d-6dd061abf759
caps.latest.revision: 25
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 4c72d8ce8c6ed87687cb9db69c52e20aebe9e15f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="data-source-sample"></a>データ ソースのサンプル
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  これは、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]サンプル アプリケーションに接続する方法を示して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データ ソース オブジェクトを使用してデータベース。 データを取得する方法も示します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベース ストアド プロシージャを使用します。  
  
 このサンプルのコード ファイルは connectDS.java という名前で、次の場所にあります。  
  
 \<*インストール ディレクトリ*> \sqljdbc_\<*バージョン*>\\<*言語*> \samples\connections  
  
## <a name="requirements"></a>必要条件  
 このサンプル アプリケーションを実行するには、クラスパスに sqljdbc.jar ファイルまたは sqljdbc4.jar ファイルを含めるを設定する必要があります。 クラスパスに sqljdbc.jar または sqljdbc4.jar のエントリがない場合、サンプル アプリケーションで "Class not found" という一般的な例外がスローされます。 アクセスする必要も、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]サンプル データベース。 クラスパスを設定する方法の詳細については、次を参照してください。 [JDBC ドライバーを使用して](../../connect/jdbc/using-the-jdbc-driver.md)です。  
  
> [!NOTE]  
>  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] Sqljdbc.jar と sqljdbc4.jar な Java ランタイム環境 (JRE) 設定によって使用されるクラス ライブラリ ファイルを提供します。 選択する JAR ファイルの詳細については、次を参照してください。 [JDBC Driver のシステム要件](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md)です。  
  
## <a name="example"></a>例  
 次の例では、サンプル コードの setter メソッドを使用して、さまざまな接続プロパティを設定、 [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md)オブジェクトを呼び出し、続いて、 [getConnection](../../connect/jdbc/reference/getconnection-method-sqlserverdatasource.md)のメソッド、SQLServerDataSource オブジェクトを返す、 [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md)オブジェクト。  
  
 次に、使用するサンプル コード、 [prepareCall](../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md) 、SQLServerConnection オブジェクトを作成する方法、 [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)オブジェクト、し、 [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverpreparedstatement.md)ストアド プロシージャを実行するメソッドが呼び出されます。  
  
 最後に、サンプルを使用して、 [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)ストアド プロシージャによって返される結果を反復処理に executeQuery メソッドから返されたオブジェクト。  
  
```java
import java.sql.*;  
import com.microsoft.sqlserver.jdbc.*;  
  
public class connectDS {  
  
   public static void main(String[] args) {  
  
      // Declare the JDBC objects.  
      Connection con = null;  
      CallableStatement cstmt = null;  
      ResultSet rs = null;  
  
      try {  
         // Establish the connection.   
         SQLServerDataSource ds = new SQLServerDataSource();  
         ds.setUser("UserName");  
         ds.setPassword("*****");  
         ds.setServerName("localhost");  
         ds.setPortNumber(1433);   
         ds.setDatabaseName("AdventureWorks");  
         con = ds.getConnection();  
  
         // Execute a stored procedure that returns some data.  
         cstmt = con.prepareCall("{call dbo.uspGetEmployeeManagers(?)}");  
         cstmt.setInt(1, 50);  
         rs = cstmt.executeQuery();  
  
         // Iterate through the data in the result set and display it.  
         while (rs.next()) {  
            System.out.println("EMPLOYEE: " + rs.getString("LastName") +   
               ", " + rs.getString("FirstName"));  
            System.out.println("MANAGER: " + rs.getString("ManagerLastName") +   
               ", " + rs.getString("ManagerFirstName"));  
            System.out.println();  
         }  
      }  
  
      // Handle any errors that may have occurred.  
      catch (Exception e) {  
         e.printStackTrace();  
      }  
      finally {  
         if (rs != null) try { rs.close(); } catch(Exception e) {}  
         if (cstmt != null) try { cstmt.close(); } catch(Exception e) {}  
         if (con != null) try { con.close(); } catch(Exception e) {}  
         System.exit(1);  
      }  
   }  
}  
```  
  
## <a name="see-also"></a>参照  
 [接続およびデータの取得](../../connect/jdbc/connecting-and-retrieving-data.md)  
  
  


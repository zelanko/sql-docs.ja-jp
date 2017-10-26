---
title: "接続 URL のサンプル |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96fabc42-59d1-4cc0-93c5-db00cbe55e95
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8de387fce6f7367f4a2154c4bceb8ebe8447b336
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="connection-url-sample"></a>接続 URL のサンプル
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  これは、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]サンプル アプリケーションに接続する方法を示して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]接続 URL を使用してデータベース。 データを取得する方法も示します、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] SQL ステートメントを使用してデータベース。  
  
 このサンプルのコード ファイルは connectURL.java という名前で、次の場所にあります。  
  
 \<*インストール ディレクトリ*> \sqljdbc_\<*バージョン*>\\<*言語*> \samples\connections  
  
## <a name="requirements"></a>必要条件  
 このサンプル アプリケーションを実行するには、クラスパスに sqljdbc.jar ファイルまたは sqljdbc4.jar ファイルを含めるを設定する必要があります。 クラスパスに sqljdbc.jar または sqljdbc4.jar のエントリがない場合、サンプル アプリケーションで "Class not found" という一般的な例外がスローされます。 アクセスする必要も、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]サンプル データベース。 クラスパスを設定する方法の詳細については、次を参照してください。 [JDBC ドライバーを使用して](../../connect/jdbc/using-the-jdbc-driver.md)です。  
  
> [!NOTE]  
>  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] Sqljdbc.jar と sqljdbc4.jar な Java ランタイム環境 (JRE) 設定によって使用されるクラス ライブラリ ファイルを提供します。 選択する JAR ファイルの詳細については、次を参照してください。 [JDBC Driver のシステム要件](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md)です。  
  
## <a name="example"></a>例  
 次の例で、サンプル コード、接続 URL でさまざまな接続プロパティを設定および DriverManager クラスを返すの getConnection メソッドを呼び出して、 [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md)オブジェクト。  
  
 次に、使用するサンプル コード、 [createStatement](../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md) 、SQLServerConnection オブジェクトを作成する方法、 [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md)オブジェクト、し、 [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md)メソッドSQL ステートメントを実行すると呼びます。  
  
 最後に、サンプルを使用して、 [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) SQL ステートメントによって返される結果を反復処理に executeQuery メソッドから返されたオブジェクト。  
  
```java  
import java.sql.*;  
  
public class connectURL {  
  
   public static void main(String[] args) {  
  
      // Create a variable for the connection string.  
      String connectionUrl = "jdbc:sqlserver://localhost:1433;" +  
         "databaseName=AdventureWorks;user=UserName;password=*****";  
  
      // Declare the JDBC objects.  
      Connection con = null;  
      Statement stmt = null;  
      ResultSet rs = null;  
  
      try {  
         // Establish the connection.  
         Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");  
         con = DriverManager.getConnection(connectionUrl);  
  
         // Create and execute an SQL statement that returns some data.  
         String SQL = "SELECT TOP 10 * FROM Person.Contact";  
         stmt = con.createStatement();  
         rs = stmt.executeQuery(SQL);  
  
         // Iterate through the data in the result set and display it.  
         while (rs.next()) {  
            System.out.println(rs.getString(4) + " " + rs.getString(6));  
         }  
      }  
  
      // Handle any errors that may have occurred.  
      catch (Exception e) {  
         e.printStackTrace();  
      }  
      finally {  
         if (rs != null) try { rs.close(); } catch(Exception e) {}  
         if (stmt != null) try { stmt.close(); } catch(Exception e) {}  
         if (con != null) try { con.close(); } catch(Exception e) {}  
      }  
   }  
}  
```  
  
## <a name="see-also"></a>参照  
 [接続およびデータの取得](../../connect/jdbc/connecting-and-retrieving-data.md)  
  
  


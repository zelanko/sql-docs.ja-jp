---
title: "セットのデータ サンプルの結果をキャッシュ |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 13a95ebb-996c-4713-a1bd-5834fe22a334
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9061548b946d631f20a9b48ed49d56aac4a4f0fd
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="caching-result-set-data-sample"></a>結果セットのデータ サンプルのキャッシング
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  これは、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]サンプル アプリケーションをデータベースから大きなデータ セットを取得しを使用して、クライアント上でキャッシュされるデータの行の数を制御する方法を示して、 [setFetchSize](../../connect/jdbc/reference/setfetchsize-method-sqlserverresultset.md)のメソッド、 [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。  
  
> [!NOTE]  
>  クライアント上でキャッシュされる行数の制限は、結果セットが含むことのできる行の総数の制限とは異なります。 結果セットに含まれている行の合計数を制御するには、使用、 [setMaxRows](../../connect/jdbc/reference/setmaxrows-method-sqlserverstatement.md)のメソッド、 [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md)両方によって継承されるオブジェクト、 [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)と[SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)オブジェクト。  
  
 ステートメント オブジェクトを作成するときに使用する、カーソルの種類を指定することによって、Statement オブジェクトのいずれかを作成するときに、クライアントにキャッシュ行の数に制限を設定するにサーバー側カーソルを使用する必要があります最初。 たとえば、JDBC ドライバーが TYPE_SS_SERVER_CURSOR_FORWARD_ONLY カーソルの種類は、高速順方向専用で使用するための読み取り専用のサーバー側カーソル[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベース。  
  
> [!NOTE]  
>  SQL Server 固有のカーソルの種類を使用する代わりに、selectMethod 接続文字列プロパティの値を "cursor" に設定して使用する方法もあります。 JDBC ドライバーでサポートされるカーソルの種類の詳細については、次を参照してください。[カーソルの種類について](../../connect/jdbc/understanding-cursor-types.md)です。  
  
 ステートメントのオブジェクトに含まれているクエリを実行すると、データ クライアントに返される、その結果セット、データの量が一度に 1 つのデータベースから取得されますを制御する setFetchSize メソッドを呼び出すことができます。 たとえば、100 行のデータを含むテーブルがあり、フェッチ サイズを 10 に設定した場合、任意の時点でクライアント上では 10 行のデータのみがキャッシュされます。 これにより、データが処理される速度は遅くなりますが、クライアント上で使用されるメモリが少なくなるという利点があります。これは、大量のデータを処理する必要があるときに特に役立ちます。  
  
 このサンプルのコード ファイルは cacheRS.java という名前で、次の場所にあります。  
  
 \<*インストール ディレクトリ*> \sqljdbc_\<*バージョン*>\\<*言語*> \samples\resultsets  
  
## <a name="requirements"></a>必要条件  
 このサンプル アプリケーションを実行するには、クラスパスの設定で sqljdbc.jar ファイルまたは sqljdbc4.jar ファイルを追加する必要があります。 クラスパスに sqljdbc.jar または sqljdbc4.jar のエントリがない場合、サンプル アプリケーションで "Class not found" という一般的な例外がスローされます。 アクセスする必要も、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]サンプル データベース。 クラスパスを設定する方法の詳細については、次を参照してください。 [JDBC ドライバーを使用して](../../connect/jdbc/using-the-jdbc-driver.md)です。  
  
> [!NOTE]  
>  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] Sqljdbc.jar と sqljdbc4.jar な Java ランタイム環境 (JRE) 設定によって使用されるクラス ライブラリ ファイルを提供します。 選択する JAR ファイルの詳細については、次を参照してください。 [JDBC Driver のシステム要件](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md)です。  
  
## <a name="example"></a>例  
 次の例では、サンプル コードへの接続、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]サンプル データベース。 含む SQL ステートメントを使用し、 [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md)オブジェクト、サーバー側カーソルの種類を指定および SQL ステートメントを実行し、SQLServerResultSet オブジェクトに返されるデータを配置します。  
  
 次に、サンプル コードは、使用して、結果セットに引数として、フェッチ サイズを渡す、カスタム timerTest メソッドを呼び出します。 TimerTest メソッド setFetchSize メソッドを使用して、結果セットのフェッチ サイズを設定、テストの開始時刻を設定し、使用して結果セットを反復処理し、`While`ループします。 すぐに、`While`ループが終了したら、コードが、テストの停止時刻を設定し、フェッチ サイズ、処理、行の数を含むテストの結果を表示およびテストの実行にかかった時間です。  
  
```java
import java.sql.*;  
import com.microsoft.sqlserver.jdbc.SQLServerResultSet;  
  
public class cacheRS {  
  
   public static void main(String[] args) {  
  
      // Create a variable for the connection string.  
      String connectionUrl = "jdbc:sqlserver://localhost:1433;" +  
            "databaseName=AdventureWorks;integratedSecurity=true;";  
  
      // Declare the JDBC objects.  
      Connection con = null;  
      Statement stmt = null;  
      ResultSet rs = null;  
  
      try {  
  
         // Establish the connection.  
         Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");  
         con = DriverManager.getConnection(connectionUrl);  
  
         // Create and execute an SQL statement that returns a large  
         // set of data and then display it.  
         String SQL = "SELECT * FROM Sales.SalesOrderDetail;";  
         stmt = con.createStatement(SQLServerResultSet.TYPE_SS_SERVER_CURSOR_FORWARD_ONLY, +  
               SQLServerResultSet.CONCUR_READ_ONLY);  
  
         // Perform a fetch for every row in the result set.  
         rs = stmt.executeQuery(SQL);  
         timerTest(1, rs);  
         rs.close();  
  
         // Perform a fetch for every tenth row in the result set.  
         rs = stmt.executeQuery(SQL);  
         timerTest(10, rs);  
         rs.close();  
  
         // Perform a fetch for every 100th row in the result set.  
         rs = stmt.executeQuery(SQL);  
         timerTest(100, rs);  
         rs.close();  
  
         // Perform a fetch for every 1000th row in the result set.  
         rs = stmt.executeQuery(SQL);  
         timerTest(1000, rs);  
         rs.close();  
  
         // Perform a fetch for every 128th row (the default) in the result set.  
         rs = stmt.executeQuery(SQL);  
         timerTest(0, rs);  
         rs.close();  
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
  
   private static void timerTest(int fetchSize, ResultSet rs) {  
      try {  
  
         // Declare the variables for tracking the row count and elapsed time.  
         int rowCount = 0;  
         long startTime = 0;  
         long stopTime = 0;  
         long runTime = 0;  
  
         // Set the fetch size then iterate through the result set to  
         // cache the data locally.  
         rs.setFetchSize(fetchSize);  
         startTime = System.currentTimeMillis();  
         while (rs.next()) {  
            rowCount++;  
         }  
         stopTime = System.currentTimeMillis();  
         runTime = stopTime - startTime;  
  
         // Display the results of the timer test.  
         System.out.println("FETCH SIZE: " + rs.getFetchSize());  
         System.out.println("ROWS PROCESSED: " + rowCount);  
         System.out.println("TIME TO EXECUTE: " + runTime);  
         System.out.println();  
  
      } catch (Exception e) {  
         e.printStackTrace();  
      }  
   }  
}  
```  
  
## <a name="see-also"></a>参照  
 [結果セットの処理](../../connect/jdbc/working-with-result-sets.md)  
  
  


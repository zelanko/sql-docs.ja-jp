---
title: セットのデータ サンプルの結果をキャッシュ |Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 13a95ebb-996c-4713-a1bd-5834fe22a334
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4a0c7f60de8680229fdc3fc3ed3a95c26ad5ef5f
ms.sourcegitcommit: 6fa72c52c6d2256c5539cc16c407e1ea2eee9c95
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/27/2018
ms.locfileid: "39278573"
---
# <a name="caching-result-set-data-sample"></a>結果セットのデータ サンプルのキャッシング
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  この [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] サンプル アプリケーションは、データベースから大きなデータ セットを取得し、[SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) オブジェクトの [setFetchSize](../../connect/jdbc/reference/setfetchsize-method-sqlserverresultset.md) メソッドを使用して、クライアント上でキャッシュされるデータの行数を制御する方法を示しています。  
  
> [!NOTE]  
>  クライアント上でキャッシュされる行数の制限は、結果セットが含むことのできる行の総数の制限とは異なります。 結果セットに含まれる行の総数を制御するには、[SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) オブジェクトの [setMaxRows](../../connect/jdbc/reference/setmaxrows-method-sqlserverstatement.md) メソッドを使用します。これは、[SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) オブジェクトと [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) オブジェクトの両方に継承されます。  
  
 クライアント上でキャッシュされる行数に制限を設定するには、Statement オブジェクトの作成に使用するカーソルの種類を指定することで、いずれかの Statement オブジェクトを作成するときに、最初にサーバー側のカーソルを使用する必要があります。 たとえば、JDBC ドライバーでは TYPE_SS_SERVER_CURSOR_FORWARD_ONLY というカーソルの種類が提供されます。これは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] データベースで使用する高速順方向専用、読み取り専用のサーバー側カーソルです。  
  
> [!NOTE]  
>  SQL Server 固有のカーソルの種類を使用する代わりに、selectMethod 接続文字列プロパティの値を "cursor" に設定して使用する方法もあります。 JDBC ドライバーでサポートされるカーソルの種類の詳細については、次を参照してください。[カーソルの種類について](../../connect/jdbc/understanding-cursor-types.md)します。  
  
 Statement オブジェクトに含まれるクエリを実行し、データが結果セットとしてクライアントに返されたら、setFetchSize メソッドを呼び出して、データベースから一度に取得されるデータの量を制御できます。 たとえば、100 行のデータを含むテーブルがあり、フェッチ サイズを 10 に設定した場合、任意の時点でクライアント上では 10 行のデータのみがキャッシュされます。 これにより、データが処理される速度は遅くなりますが、クライアント上で使用されるメモリが少なくなるという利点があります。これは、大量のデータを処理する必要があるときに特に役立ちます。  
  
 このサンプルのコード ファイルは CacheRS.java という名前で、次の場所にあります。  
  
 \<*インストール ディレクトリ*> \sqljdbc_\<*バージョン*>\\<*言語*> \samples\resultsets  
  
## <a name="requirements"></a>必要条件  
 このサンプル アプリケーションを実行するには、クラスパスを設定して mssql-jdbc jar ファイルを含める必要があります。 また、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] サンプル データベースへのアクセス権限も必要です。 クラスパスを設定する方法の詳細については、次を参照してください。 [JDBC ドライバーを使用して](../../connect/jdbc/using-the-jdbc-driver.md)します。  
  
> [!NOTE]  
>  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] には、必要な Java ランタイム環境 (JRE) 設定に応じて使用される mssql-jdbc クラス ライブラリ ファイルが用意されています。 選択する JAR ファイルの詳細については、次を参照してください。 [JDBC Driver のシステム要件](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md)します。  
  
## <a name="example"></a>例  
 次の例では、サンプル コードは [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] サンプル データベースへの接続を行います。 次に、[SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) オブジェクトで SQL ステートメントを使用し、サーバー側のカーソルの種類を指定し、SQL ステートメントを実行して、返されたデータを SQLServerResultSet オブジェクトに配置します。  
  
 次に、サンプル コードはカスタム timerTest メソッドを呼び出し、使用するフェッチ サイズと結果セットを引数として渡します。 timerTest メソッドは、setFetchSize メソッドを使用して結果セットのフェッチ サイズを設定し、テストの開始時刻を設定し、`While` ループを使用して結果セットを繰り返し処理します。 `While` ループが終了したら、コードはテストの停止時刻を設定し、フェッチ サイズ、処理された行数、テストの実行にかかった時間など、テストの結果を表示します。  
  
```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

import com.microsoft.sqlserver.jdbc.SQLServerResultSet;

public class CacheRS {

    public static void main(String[] args) {

        // Create a variable for the connection string.
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=AdventureWorks;user=<user>;password=<password>";

        try (Connection con = DriverManager.getConnection(connectionUrl);
                Statement stmt = con.createStatement(SQLServerResultSet.TYPE_SS_SERVER_CURSOR_FORWARD_ONLY, SQLServerResultSet.CONCUR_READ_ONLY);) {

            String SQL = "SELECT * FROM Sales.SalesOrderDetail;";

            // Perform a fetch for every row in the result set.
            ResultSet rs = stmt.executeQuery(SQL);
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
        catch (SQLException e) {
            e.printStackTrace();
        }
    }

    private static void timerTest(int fetchSize,
            ResultSet rs) throws SQLException {

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
    }
}
```  
  
## <a name="see-also"></a>参照  
 [結果セットの処理](../../connect/jdbc/working-with-result-sets.md)  
  
  

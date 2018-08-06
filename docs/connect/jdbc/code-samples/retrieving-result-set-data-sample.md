---
title: セットのデータ サンプルの結果の取得 |Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 1b190c36-3d38-49a2-8599-612329675851
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fb68f2bedb680f990e2b0c4e4e559191915dd300
ms.sourcegitcommit: 6fa72c52c6d2256c5539cc16c407e1ea2eee9c95
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/27/2018
ms.locfileid: "39279063"
---
# <a name="retrieving-result-set-data-sample"></a>結果セットのデータ サンプルの取得
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  この [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] サンプル アプリケーションは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] データベースからデータ セットを取得し、そのデータを表示する方法を示しています。  
  
 このサンプルのコード ファイルは RetrieveRS.java という名前で、次の場所にあります。  
  
 \<*インストール ディレクトリ*> \sqljdbc_\<*バージョン*>\\<*言語*> \samples\resultsets  
  
## <a name="requirements"></a>必要条件  
 このサンプル アプリケーションを実行するには、クラスパスを設定して mssql-jdbc jar ファイルを含める必要があります。 また、[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] サンプル データベースへのアクセス権限も必要です。 クラスパスを設定する方法の詳細については、次を参照してください。 [JDBC ドライバーを使用して](../../../connect/jdbc/using-the-jdbc-driver.md)します。  
  
> [!NOTE]  
>  [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] には、必要な Java ランタイム環境 (JRE) 設定に応じて使用される mssql-jdbc クラス ライブラリ ファイルが用意されています。 選択する JAR ファイルの詳細については、次を参照してください。 [JDBC Driver のシステム要件](../../../connect/jdbc/system-requirements-for-the-jdbc-driver.md)します。  
  
## <a name="example"></a>例  
 次の例では、サンプル コードは [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] サンプル データベースへの接続を行います。 次に、[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) オブジェクトで SQL ステートメントを使用して、SQL ステートメントを実行し、返されたデータを [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) オブジェクトに配置します。  
  
 次に、サンプル コードはカスタム displayRow メソッドを呼び出して結果セット内のデータ行を繰り返し処理し、[getString](../../../connect/jdbc/reference/getstring-method-sqlserverresultset.md) メソッドを使用してデータの一部を表示します。
  
```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

public class RetrieveRS {

    public static void main(String[] args) {

        // Create a variable for the connection string.
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=AdventureWorks;user=<user>;password=<password>";

        try (Connection con = DriverManager.getConnection(connectionUrl); Statement stmt = con.createStatement();) {
            String SQL = "SELECT * FROM Production.Product;";
            ResultSet rs = stmt.executeQuery(SQL);
            displayRow("PRODUCTS", rs);
        }
        // Handle any errors that may have occurred.
        catch (SQLException e) {
            e.printStackTrace();
        }
    }

    private static void displayRow(String title,
            ResultSet rs) throws SQLException {
        System.out.println(title);
        while (rs.next()) {
            System.out.println(rs.getString("ProductNumber") + " : " + rs.getString("Name"));
        }
    }
}
```  
  
## <a name="see-also"></a>参照  
 [結果セットの処理](../../../connect/jdbc/working-with-result-sets.md)  
  
  

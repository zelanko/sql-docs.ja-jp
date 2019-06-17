---
title: 接続 URL のサンプル |Microsoft Docs
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 96fabc42-59d1-4cc0-93c5-db00cbe55e95
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: f13f175dc6f50818b5eef6b142f4d211103a4b3c
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66803155"
---
# <a name="connection-url-sample"></a>接続 URL のサンプル

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

この [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] サンプル アプリケーションは、接続 URL を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに接続する方法を示しています。 また、SQL ステートメントを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースからデータを取得する方法も示します。

このサンプルのコード ファイルは ConnectURL.java という名前で、次の場所にあります。

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples\connections
```

## <a name="requirements"></a>必要条件

このサンプル アプリケーションを実行するには、クラスパスを設定して mssql-jdbc jar ファイルを含める必要があります。 また、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] サンプル データベースへのアクセス権限も必要です。 クラスパスを設定する方法の詳細については、次を参照してください。 [JDBC ドライバーを使用して](../../connect/jdbc/using-the-jdbc-driver.md)します。

> [!NOTE]  
> [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] には、必要な Java ランタイム環境 (JRE) 設定に応じて使用される mssql-jdbc クラス ライブラリ ファイルが用意されています。 選択する JAR ファイルの詳細については、「[JDBC Driver のシステム要件](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md)」を参照してください。

## <a name="example"></a>例

次の例では、サンプル コードにより接続 URL のさまざまな接続プロパティを設定し、DriverManager クラスの getConnection メソッドを呼び出して、[SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) オブジェクトを返します。

次に、サンプル コードは SQLServerConnection オブジェクトの [createStatement](../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md) メソッドを使用して [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) オブジェクトを作成し、さらに [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md) メソッドが呼び出されて SQL ステートメントを実行します。

最後に、サンプルでは executeQuery メソッドから返された [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) オブジェクトを使用して、SQL ステートメントが返した結果を繰り返し処理します。

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

public class ConnectURL {
    public static void main(String[] args) {

        // Create a variable for the connection string.
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=AdventureWorks;user=<user>;password=<password>";

        try (Connection con = DriverManager.getConnection(connectionUrl); Statement stmt = con.createStatement();) {
            String SQL = "SELECT TOP 10 * FROM Person.Contact";
            ResultSet rs = stmt.executeQuery(SQL);

            // Iterate through the data in the result set and display it.
            while (rs.next()) {
                System.out.println(rs.getString("FirstName") + " " + rs.getString("LastName"));
            }
        }
        // Handle any errors that may have occurred.
        catch (SQLException e) {
            e.printStackTrace();
        }
    }
}
```

## <a name="see-also"></a>参照

[接続およびデータの取得](../../connect/jdbc/connecting-and-retrieving-data.md)

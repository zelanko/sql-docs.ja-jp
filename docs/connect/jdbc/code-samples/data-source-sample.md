---
title: データ ソースのサンプル |Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b4a933ee-f2c6-4e0d-a96d-6dd061abf759
caps.latest.revision: 25
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: aeb5c252d40c7c9bd389d5d628c02ba124009130
ms.sourcegitcommit: 6fa72c52c6d2256c5539cc16c407e1ea2eee9c95
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/27/2018
ms.locfileid: "39279003"
---
# <a name="data-source-sample"></a>データ ソースのサンプル
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  この [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] サンプル アプリケーションは、データ ソース オブジェクトを使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] データベースに接続する方法を示しています。 また、ストアド プロシージャを使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] データベースからデータを取得する方法も示します。  
  
 このサンプルのコード ファイルは ConnectDS.java という名前で、次の場所にあります。  
  
 \<*インストール ディレクトリ*> \sqljdbc_\<*バージョン*>\\<*言語*> \samples\connections  
  
## <a name="requirements"></a>必要条件  
 このサンプル アプリケーションを実行するには、クラスパスを設定して mssql-jdbc jar ファイルを含める必要があります。 また、[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] サンプル データベースへのアクセス権限も必要です。 クラスパスを設定する方法の詳細については、次を参照してください。 [JDBC ドライバーを使用して](../../../connect/jdbc/using-the-jdbc-driver.md)します。  
  
> [!NOTE]  
>  [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] には、必要な Java ランタイム環境 (JRE) 設定に応じて使用される mssql-jdbc クラス ライブラリ ファイルが用意されています。 選択する JAR ファイルの詳細については、次を参照してください。 [JDBC Driver のシステム要件](../../../connect/jdbc/system-requirements-for-the-jdbc-driver.md)します。  
  
## <a name="example"></a>例  
 次の例では、サンプル コードにより [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) オブジェクトの setter メソッドを使用してさまざまな接続プロパティを設定し、SQLServerDataSource オブジェクトの [getConnection](../../../connect/jdbc/reference/getconnection-method-sqlserverdatasource.md) メソッドを呼び出して、[SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) オブジェクトを返します。  
  
 次に、サンプル コードは SQLServerConnection オブジェクトの [prepareCall](../../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md) メソッドを使用して [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md) オブジェクトを作成し、さらに [executeQuery](../../../connect/jdbc/reference/executequery-method-sqlserverpreparedstatement.md) メソッドが呼び出されてストアド プロシージャを実行します。  
  
 最後に、サンプルでは executeQuery メソッドから返された [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) オブジェクトを使用して、ストアド プロシージャが返した結果を繰り返し処理します。  
  
```java
import java.sql.CallableStatement;
import java.sql.Connection;
import java.sql.ResultSet;
import java.sql.SQLException;

import com.microsoft.sqlserver.jdbc.SQLServerDataSource;

public class ConnectDS {

    public static void main(String[] args) {

        // Create datasource.
        SQLServerDataSource ds = new SQLServerDataSource();
        ds.setUser("<user>");
        ds.setPassword("<password>");
        ds.setServerName("<server>");
        ds.setPortNumber(<port>);
        ds.setDatabaseName("AdventureWorks");

        try (Connection con = ds.getConnection(); 
                CallableStatement cstmt = con.prepareCall("{call dbo.uspGetEmployeeManagers(?)}");) {
            // Execute a stored procedure that returns some data.
            cstmt.setInt(1, 50);
            ResultSet rs = cstmt.executeQuery();

            // Iterate through the data in the result set and display it.
            while (rs.next()) {
                System.out.println("EMPLOYEE: " + rs.getString("LastName") + ", " + rs.getString("FirstName"));
                System.out.println("MANAGER: " + rs.getString("ManagerLastName") + ", " + rs.getString("ManagerFirstName"));
                System.out.println();
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
 [接続およびデータの取得](../../../connect/jdbc/connecting-and-retrieving-data.md)  
  
  

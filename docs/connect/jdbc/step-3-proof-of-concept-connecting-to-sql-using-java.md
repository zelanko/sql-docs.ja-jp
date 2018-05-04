---
title: '手順 3: 概念実証の Java を使用する SQL への接続 |Microsoft ドキュメント'
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
ms.topic: conceptual
ms.assetid: 1504a348-1774-47ab-8967-288ec3985ae4
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0edefa70b2dab075f0e7995b561f608383d35010
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-java"></a>手順 3: 概念実証の Java を使用して SQL に接続します。
  
この例は、概念実証ののみを考慮してください。 サンプル コードでは、わかりやすくするため、簡略化し、Microsoft によって推奨されるベスト プラクティスを必ずしもは表しません。  
  
## <a name="step-1--connect"></a>手順 1: 接続  
  
SQL データベースに接続するには、接続クラスを使用します。   
  
```java  
  
    // Use the JDBC driver  
    import java.sql.*;  
    import com.microsoft.sqlserver.jdbc.*;  
      
        public class SQLDatabaseConnection {  
      
            // Connect to your database.  
            // Replace server name, username, and password with your credentials  
            public static void main(String[] args) {  
                String connectionString =  
                    "jdbc:sqlserver://yourserver.database.windows.net:1433;"  
                    + "database=AdventureWorks;"  
                    + "user=yourusername@yourserver;"  
                    + "password=yourpassword;"  
                    + "encrypt=true;"  
                    + "trustServerCertificate=false;"  
                    + "hostNameInCertificate=*.database.windows.net;"  
                    + "loginTimeout=30;";  
              
                // Declare the JDBC objects.  
                Connection connection = null;  
                              
                try {  
                    connection = DriverManager.getConnection(connectionString);  
      
                }  
                catch (Exception e) {  
                    e.printStackTrace();  
                }  
                finally {  
                    if (connection != null) try { connection.close(); } catch(Exception e) {}  
                }  
            }  
        }  
```  
  
## <a name="step-2-execute-a-query"></a>手順 2: クエリを実行します。  
このサンプルでは Azure SQL データベースへの接続、SELECT ステートメントを実行および選択した行を返します。   
  
```java  
    // Use the JDBC driver  
    import java.sql.*;  
    import com.microsoft.sqlserver.jdbc.*;  
      
        public class SQLDatabaseConnection {  
      
            // Connect to your database.  
            // Replace server name, username, and password with your credentials  
            public static void main(String[] args) {  
                String connectionString =  
                    "jdbc:sqlserver://yourserver.database.windows.net:1433;"  
                    + "database=AdventureWorks;"  
                    + "user=yourusername@yourserver;"  
                    + "password=yourpassword;"  
                    + "encrypt=true;"  
                    + "trustServerCertificate=false;"  
                    + "hostNameInCertificate=*.database.windows.net;"  
                    + "loginTimeout=30;";  
              
                // Declare the JDBC objects.  
                Connection connection = null;  
                Statement statement = null;   
                ResultSet resultSet = null;  
                              
                try {  
                    connection = DriverManager.getConnection(connectionString);  
      
                    // Create and execute a SELECT SQL statement.  
                    String selectSql = "SELECT TOP 10 Title, FirstName, LastName from SalesLT.Customer";  
                    statement = connection.createStatement();  
                    resultSet = statement.executeQuery(selectSql);  
      
                    // Print results from select statement  
                    while (resultSet.next())   
                    {  
                        System.out.println(resultSet.getString(2) + " "  
                            + resultSet.getString(3));  
                    }  
                }  
                catch (Exception e) {  
                    e.printStackTrace();  
                }  
                finally {  
                    // Close the connections after the data has been handled.  
                    if (resultSet != null) try { resultSet.close(); } catch(Exception e) {}  
                    if (statement != null) try { statement.close(); } catch(Exception e) {}  
                    if (connection != null) try { connection.close(); } catch(Exception e) {}  
                }  
            }  
        }  
```  
  
## <a name="step-3-insert-a-row"></a>手順 3: 行を挿入します。  
この例では、INSERT ステートメントの実行、パラメーターを渡すおよび主キーの自動生成された値を取得します。   
  
```java  
    // Use the JDBC driver  
    import java.sql.*;  
    import com.microsoft.sqlserver.jdbc.*;  
      
        public class SQLDatabaseConnection {  
      
            // Connect to your database.  
            // Replace server name, username, and password with your credentials  
            public static void main(String[] args) {  
                String connectionString =  
                    "jdbc:sqlserver://yourserver.database.windows.net:1433;"  
                    + "database=AdventureWorks;"  
                    + "user=yourusername@yourserver;"  
                    + "password=yourpassword;"  
                    + "encrypt=true;"  
                    + "trustServerCertificate=false;"  
                    + "hostNameInCertificate=*.database.windows.net;"  
                    + "loginTimeout=30;";  
              
                // Declare the JDBC objects.  
                Connection connection = null;  
                Statement statement = null;   
                ResultSet resultSet = null;  
                PreparedStatement prepsInsertProduct = null;  
                  
                try {  
                    connection = DriverManager.getConnection(connectionString);  
      
                    // Create and execute an INSERT SQL prepared statement.  
                    String insertSql = "INSERT INTO SalesLT.Product (Name, ProductNumber, Color, StandardCost, ListPrice, SellStartDate) VALUES "  
                        + "('NewBike', 'BikeNew', 'Blue', 50, 120, '2016-01-01');";  
      
                    prepsInsertProduct = connection.prepareStatement(  
                        insertSql,  
                        Statement.RETURN_GENERATED_KEYS);  
                    prepsInsertProduct.execute();  
                      
                    // Retrieve the generated key from the insert.  
                    resultSet = prepsInsertProduct.getGeneratedKeys();  
                      
                    // Print the ID of the inserted row.  
                    while (resultSet.next()) {  
                        System.out.println("Generated: " + resultSet.getString(1));  
                    }  
                }  
                catch (Exception e) {  
                    e.printStackTrace();  
                }  
                finally {  
                    // Close the connections after the data has been handled.  
                    if (prepsInsertProduct != null) try { prepsInsertProduct.close(); } catch(Exception e) {}  
                    if (resultSet != null) try { resultSet.close(); } catch(Exception e) {}  
                    if (statement != null) try { statement.close(); } catch(Exception e) {}  
                    if (connection != null) try { connection.close(); } catch(Exception e) {}  
                }  
            }  
        }  
```  
  
## <a name="additional-samples"></a>その他のサンプル  
[サンプル JDBC Driver アプリケーション](../../connect/jdbc/sample-jdbc-driver-applications.md)

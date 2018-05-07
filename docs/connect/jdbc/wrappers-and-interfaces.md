---
title: ラッパーとインターフェイス |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 27fc9b72-9f21-4728-abcb-5c015f28a6ab
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9a7316e5daa6fa27209a31a07ddf0ace84c191b0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="wrappers-and-interfaces"></a>ラッパーとインターフェイス
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 、クラスのプロキシを作成することがサポートするインターフェイスとするのに便利なラッパーに固有の JDBC api 拡張機能にアクセス、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]プロキシ インターフェイス経由します。  
  
## <a name="wrappers"></a>ラッパー  
 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] Java.sql.Wrapper インターフェイスをサポートします。 このインターフェイスに固有の JDBC API に access 拡張機能するためのメカニズムを提供、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]プロキシ インターフェイス経由します。  
  
 Java.sql.Wrapper インターフェイスには、2 つのメソッドの定義: **isWrapperFor**と**unwrap**です。 **IsWrapperFor**メソッドでは、指定した入力オブジェクトがこのインターフェイスを実装するかどうかを確認します。 **Unwrap**メソッドへのアクセスを許可するには、このインターフェイスを実装するオブジェクトを返します、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]固有のメソッドです。  
  
 **isWrapperFor**と**unwrap**メソッドに次のように公開されます。  
  
-   [isWrapperFor メソッド&#40;SQLServerCallableStatement&#41;](../../connect/jdbc/reference/iswrapperfor-method-sqlservercallablestatement.md)  
  
-   [unwrap メソッド&#40;SQLServerCallableStatement&#41;](../../connect/jdbc/reference/unwrap-method-sqlservercallablestatement.md)  
  
-   [isWrapperFor メソッド&#40;SQLServerConnectionPoolDataSource&#41;](../../connect/jdbc/reference/iswrapperfor-method-sqlserverconnectionpooldatasource.md)  
  
-   [unwrap メソッド&#40;SQLServerConnectionPoolDataSource&#41;](../../connect/jdbc/reference/unwrap-method-sqlserverconnectionpooldatasource.md)  
  
-   [isWrapperFor メソッド&#40;SQLServerDataSource&#41;](../../connect/jdbc/reference/iswrapperfor-method-sqlserverdatasource.md)  
  
-   [unwrap メソッド&#40;SQLServerDataSource&#41;](../../connect/jdbc/reference/unwrap-method-sqlserverdatasource.md)  
  
-   [isWrapperFor メソッド&#40;SQLServerPreparedStatement&#41;](../../connect/jdbc/reference/iswrapperfor-method-sqlserverpreparedstatement.md)  
  
-   [unwrap メソッド&#40;SQLServerPreparedStatement&#41;](../../connect/jdbc/reference/unwrap-method-sqlserverpreparedstatement.md)  
  
-   [isWrapperFor メソッド&#40;SQLServerStatement&#41;](../../connect/jdbc/reference/iswrapperfor-method-sqlserverstatement.md)  
  
-   [unwrap メソッド&#40;SQLServerStatement&#41;](../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md)  
  
-   [isWrapperFor メソッド&#40;SQLServerXADataSource&#41;](../../connect/jdbc/reference/iswrapperfor-method-sqlserverxadatasource.md)  
  
-   [unwrap メソッド&#40;SQLServerXADataSource&#41;](../../connect/jdbc/reference/unwrap-method-sqlserverxadatasource.md)  
  
## <a name="interfaces"></a>インターフェイス  
 以降で[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]JDBC Driver 3.0 では、インターフェイスを関連付けられたクラスからドライバー固有のメソッドにアクセスするアプリケーション サーバーを使用できます。 アプリケーション サーバーは、プロキシを公開することを作成することで、クラスをラップすることができます、 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]-インターフェイスから固有の機能です。 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]を持つインターフェイスをサポートする、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]固有のメソッドと定数をアプリケーション サーバーは、クラスのプロキシを作成できるようにします。  
  
 標準の Java インターフェイスのため、同じオブジェクトを使用するには、ドライバー固有の機能にアクセスするラップ解除されたまたはジェネリックでは後から派生[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]機能します。  
  
 次のインターフェイスが追加されています。  
  
-   [ISQLServerCallableStatement](../../connect/jdbc/reference/isqlservercallablestatement-interface.md)  
  
-   [ISQLServerConnection](../../connect/jdbc/reference/isqlserverconnection-interface.md)  
  
-   [ISQLServerDataSource](../../connect/jdbc/reference/isqlserverdatasource-interface.md)  
  
-   [ISQLServerPreparedStatement](../../connect/jdbc/reference/isqlserverpreparedstatement-interface.md)  
  
-   [ISQLServerResultSet](../../connect/jdbc/reference/isqlserverresultset-interface.md)  
  
-   [ISQLServerStatement](../../connect/jdbc/reference/isqlserverstatement-interface.md)  
  
## <a name="example"></a>例  
  
### <a name="description"></a>Description  
 このサンプルにアクセスする方法、 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]-DataSource オブジェクトから特定の機能です。 このデータ ソース クラスは、アプリケーション サーバーでラッピングされている可能性があります。 JDBC driver に固有の関数または定数にアクセスするには、ISQLServerDataSource インターフェイスへのデータ ソースのラップを解除し、このインターフェイスで宣言された関数を使用できます。  
  
### <a name="code"></a>コード  
  
```  
import javax.sql.*;  
import java.sql.*;  
import com.microsoft.sqlserver.jdbc.*;  
  
public class UnWrapTest {  
   public static void main(String[] args) {  
      // This is a test.  This DataSource object could be something from an appserver   
      // which has wrapped the real SQLServerDataSource with its own wrapper  
      SQLServerDataSource ds = new SQLServerDataSource();  
      checkSendStringParametersAsUnicode(ds);  
   }  
  
   // Unwrap to the ISQLServerDataSource interface to access the getSendStringParametersAsUnicode function  
   static void checkSendStringParametersAsUnicode(DataSource ds) {  
      try {  
         final ISQLServerDataSource sqlServerDataSource = ds.unwrap(ISQLServerDataSource.class);  
         boolean sendStringParametersAsUnicode = sqlServerDataSource.getSendStringParametersAsUnicode();  
  
         System.out.println("Send string as parameter value is:-" + sendStringParametersAsUnicode);  
  
      } catch (SQLException sqlE) {  
         System.out.println("Exception:-" + sqlE);  
      }  
   }  
}  
```  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーのデータ型について](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  

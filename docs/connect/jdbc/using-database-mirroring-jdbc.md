---
title: "データベース ミラーリング (JDBC) の使用 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ff59218-0d3b-4274-b647-9839c4955865
caps.latest.revision: 25
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: cdc263be0e8283ed1d71630a61f4e3d60406edc8
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="using-database-mirroring-jdbc"></a>データベース ミラーリングの使用 (JDBC)
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  データベース ミラーリングは、主にデータベースの可用性とデータの冗長性を向上するためのソフトウェア ソリューションです。 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 、データベース ミラーリングを暗黙的にサポートを提供すると、開発者は任意のコードを記述したり、データベース用に構成されている場合に、その他のアクションを実行する必要はありません。  
  
 データベースごとに実装されている、ミラー化すると、データベースのコピーを保持する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]実稼働データベースをスタンバイ サーバーでします。 このサーバーは、データベース ミラーリング セッションの構成および状態に応じて、ホット スタンバイ サーバーかウォーム スタンバイ サーバーのいずれかになります。 ホット スタンバイ サーバーは、コミットされたトランザクションを損失することなくラピッド フェールオーバーをサポートし、ウォーム スタンバイ サーバーは、サービス強制をサポートします (データ損失の可能性があります)。  
  
 実稼働データベースが呼び出されて、*プリンシパル*データベースとスタンバイ コピーを呼び出す、*ミラー*データベース。 プリンシパル データベースとミラー データベースは、別個のインスタンス上に存在する必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)](サーバー インスタンス) 可能性がある場合、別のコンピューター上に存在する必要があるとします。  
  
 プリンシパル サーバーと呼ばれる運用サーバー インスタンスは、ミラー サーバーと呼ばれるスタンバイ サーバー インスタンスと通信します。 プリンシパル サーバーとミラー サーバーは、データベース ミラーリング セッション内でパートナーとして機能します。 プリンシパル サーバーが失敗した場合、ミラー サーバーできますのデータベースにプリンシパル データベースと呼ばれるプロセスを介して*フェールオーバー*です。 たとえば、Partner_A と Partner_B がパートナー サーバーで、初期時点ではプリンシパル データベースがプリンシパル サーバーである Partner_A にあり、ミラー データベースがミラー サーバーである Partner_B にあるとします。 Partner_A がオフラインになった場合、Partner_B がフェールオーバーして現在のプリンシパル データベースになることができます。 Partner_A がミラー化セッションに再び参加すると、このサーバーがミラー サーバーになり、このサーバーのデータベースがミラー データベースになります。  
  
 Partner_A サーバーが破損して修復不可能な場合は、Partner_C サーバーをオンラインにして、プリンシパル サーバーとなった Partner_B のミラー サーバーとして機能させることができます。 ただし、このシナリオでは、データベース ミラーリング構成で使用される新しいサーバー名で接続文字列プロパティが更新されるように、クライアント アプリケーションにプログラミング ロジックを含める必要があります。 含めない場合、サーバーへの接続に失敗する可能性があります。  
  
 代替データベース ミラーリング構成は、さまざまなレベルのパフォーマンスとデータの安全性を提供し、さまざまな形態のフェールオーバーをサポートします。 詳細についてを参照してください「データベース ミラーリングの概要」[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]オンライン ブック。  
  
## <a name="programming-considerations"></a>プログラミングの考慮事項  
 プリンシパル データベース サーバーに障害が発生した場合、クライアント アプリケーションの API 呼び出しの応答がエラーになり、データベースへの接続が失われたことが伝えられます。 この問題が発生すると、データベースに対するコミットされていない変更はすべて失われ、現在のトランザクションはロールバックされます。 このような場合、アプリケーションでは接続を閉じて (または、データ ソース オブジェクトを解放して) から、再び開く必要があります。 接続時に、新しい接続はプリンシパル サーバーとなったミラー データベースに透過的にリダイレクトされます。クライアントが接続文字列またはデータ ソース オブジェクトを変更する必要はありません。  
  
 接続が最初に確立されると、プリンシパル サーバーはフェールオーバー パートナーの ID を、フェールオーバー発生時に使用されるクライアントに送信します。 アプリケーションが障害の発生したプリンシパル サーバーと最初の接続を確立しようとするとき、フェールオーバー パートナーの ID はクライアントに通知されていません。 クライアント、failoverPartner 接続文字列プロパティでは、このシナリオに対処することを許可して、必要に応じて、 [setFailoverPartner](../../connect/jdbc/reference/setfailoverpartner-method-sqlserverdatasource.md)データ ソース メソッドをクライアントに、フェールオーバーの id を指定できます自身でパートナーです。 クライアント プロパティはこのシナリオでのみ使用されます。プリンシパル サーバーが利用可能な場合は使用されません。  
  
> [!NOTE]  
>  接続文字列またはデータ ソース オブジェクトで failoverPartner が指定されている場合は、databaseName プロパティも設定する必要があります。これが設定されていないと、例外がスローされます。 failoverPartner および databaseName が明示的に指定されていないと、プリンシパル データベース サーバーに障害が発生した場合に、アプリケーションがフェールオーバーを実行しません。 つまり、透過的なリダイレクトは、failoverPartner および databaseName が明示的に指定された接続に対してのみ機能します。 FailoverPartner およびその他の接続文字列プロパティの詳細については、次を参照してください。[接続プロパティの設定](../../connect/jdbc/setting-the-connection-properties.md)です。  
  
 クライアントで指定されたフェールオーバー パートナー サーバーが、指定されたデータベースのフェールオーバー パートナーの役割を担っているサーバーを参照していない場合で、なおかつ参照先のサーバー/データベースがミラーリング機構に属している場合、接続はサーバーによって拒否されます。 ただし、 [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md)クラスを提供、 [getFailoverPartner](../../connect/jdbc/reference/getfailoverpartner-method-sqlserverdatasource.md)メソッドでは、このメソッドは、接続文字列で指定されたフェールオーバー パートナーの名前、またはsetFailoverPartner メソッドです。 現在使用されている実際のフェールオーバー パートナーの名前を取得するには、次を使用して[!INCLUDE[tsql](../../includes/tsql_md.md)]ステートメント。  
  
```  
SELECT m.mirroring_role_DESC, m.mirroring_state_DESC,  
m.mirroring_partner_instance FROM sys.databases as db,  
sys.database_mirroring AS m WHERE db.name = 'MirroringDBName'  
AND db.database_id = m.database_id  
```  
  
> [!NOTE]  
>  ミラーリング データベースの名前を使用するには、このステートメントを変更する必要があります。  
  
 接続の最初の試行が失敗した場合に備えて、接続文字列を更新するか、または再試行の戦略を立てるために、パートナー情報をキャッシュすることを検討してください。  
  
## <a name="example"></a>例  
 次の例では、最初にプリンシパル サーバーへの接続が試行されます。 接続に失敗して例外がスローされた場合、ミラー サーバーへの接続が試行されます。ミラー サーバーは新しいプリンシパル サーバーに昇格している可能性があります。 接続文字列での failoverPartner プロパティの使用に注意してください。  
  
```  
import java.sql.*;  
  
public class clientFailover {  
  
   public static void main(String[] args) {  
  
      // Create a variable for the connection string.  
      String connectionUrl = "jdbc:sqlserver://serverA:1433;" +  
         "databaseName=AdventureWorks;integratedSecurity=true;" +  
         "failoverPartner=serverB";  
  
      // Declare the JDBC objects.  
      Connection con = null;  
      Statement stmt = null;  
  
      try {  
         // Establish the connection to the principal server.  
         Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");  
         con = DriverManager.getConnection(connectionUrl);  
         System.out.println("Connected to the principal server.");  
  
         // Note that if a failover of serverA occurs here, then an  
         // exception will be thrown and the failover partner will  
         // be used in the first catch block below.  
  
         // Create and execute an SQL statement that inserts some data.  
         stmt = con.createStatement();  
  
         // Note that the following statement assumes that the   
         // TestTable table has been created in the AdventureWorks  
         // sample database.  
         stmt.executeUpdate("INSERT INTO TestTable (Col2, Col3) VALUES ('a', 10)");  
      }  
  
      // Handle any errors that may have occurred.  
      catch (SQLException se) {  
         try {  
            // The connection to the principal server failed,  
            // try the mirror server which may now be the new  
            // principal server.  
            System.out.println("Connection to principal server failed, " +  
            "trying the mirror server.");  
            con = DriverManager.getConnection(connectionUrl);  
            System.out.println("Connected to the new principal server.");  
            stmt = con.createStatement();  
            stmt.executeUpdate("INSERT INTO TestTable (Col2, Col3) VALUES ('a', 10)");  
         }  
         catch (Exception e) {  
            e.printStackTrace();  
         }  
      }  
      catch (Exception e) {  
         e.printStackTrace();  
      }  
      // Close the JDBC objects.  
      finally {  
         if (stmt != null) try { stmt.close(); } catch(Exception e) {}  
         if (con != null) try { con.close(); } catch(Exception e) {}  
      }  
   }  
}  
```  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーで SQL Server に接続します。](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)  
  
  


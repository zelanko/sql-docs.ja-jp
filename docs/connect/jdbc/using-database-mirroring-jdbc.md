---
title: データベース ミラーリング (JDBC) の使用 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 4ff59218-0d3b-4274-b647-9839c4955865
caps.latest.revision: 25
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7528a85cd8e2eb258a89e6d7971ce0f80fa90258
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38041429"
---
# <a name="using-database-mirroring-jdbc"></a>データベース ミラーリングの使用 (JDBC)
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  データベース ミラーリングは、主にデータベースの可用性とデータの冗長性を向上するためのソフトウェア ソリューションです。 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] は、データベース ミラーリングを暗黙的にサポートするため、データベース用に構成されていれば、開発者がコードを記述したり、その他の操作を行ったりする必要はありません。  
  
 データベース ミラーリングは、データベースごとに実装され、スタンバイ サーバー上に [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 運用データベースのコピーを保持します。 このサーバーは、データベース ミラーリング セッションの構成および状態に応じて、ホット スタンバイ サーバーかウォーム スタンバイ サーバーのいずれかになります。 ホット スタンバイ サーバーは、コミットされたトランザクションを損失することなくラピッド フェールオーバーをサポートし、ウォーム スタンバイ サーバーは、サービス強制をサポートします (データ損失の可能性があります)。  
  
 運用データベースは*プリンシパル* データベースと呼ばれ、スタンバイ コピーは*ミラー* データベースと呼ばれます。 プリンシパル データベースとミラー データベースは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] の別々のインスタンス (サーバー インスタンス) 上に存在する必要があります。また、可能であれば、これらのデータベースは別々のコンピューター上に配置してください。  
  
 プリンシパル サーバーと呼ばれる運用サーバー インスタンスは、ミラー サーバーと呼ばれるスタンバイ サーバー インスタンスと通信します。 プリンシパル サーバーとミラー サーバーは、データベース ミラーリング セッション内でパートナーとして機能します。 プリンシパル サーバーで障害が発生した場合、ミラー サーバーは*フェールオーバー*と呼ばれる処理を通じて、ミラー サーバーのデータベースをプリンシパル データベースにできます。 たとえば、Partner_A と Partner_B がパートナー サーバーで、初期時点ではプリンシパル データベースがプリンシパル サーバーである Partner_A にあり、ミラー データベースがミラー サーバーである Partner_B にあるとします。 Partner_A がオフラインになった場合、Partner_B がフェールオーバーして現在のプリンシパル データベースになることができます。 Partner_A がミラー化セッションに再び参加すると、このサーバーがミラー サーバーになり、このサーバーのデータベースがミラー データベースになります。  
  
 Partner_A サーバーが破損して修復不可能な場合は、Partner_C サーバーをオンラインにして、プリンシパル サーバーとなった Partner_B のミラー サーバーとして機能させることができます。 ただし、このシナリオでは、データベース ミラーリング構成で使用される新しいサーバー名で接続文字列プロパティが更新されるように、クライアント アプリケーションにプログラミング ロジックを含める必要があります。 含めない場合、サーバーへの接続に失敗する可能性があります。  
  
 代替データベース ミラーリング構成は、さまざまなレベルのパフォーマンスとデータの安全性を提供し、さまざまな形態のフェールオーバーをサポートします。 詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] オンライン ブックの「データベース ミラーリングの概要」を参照してください。  
  
## <a name="programming-considerations"></a>プログラミングの考慮事項  
 プリンシパル データベース サーバーに障害が発生した場合、クライアント アプリケーションの API 呼び出しの応答がエラーになり、データベースへの接続が失われたことが伝えられます。 この問題が発生すると、データベースに対するコミットされていない変更はすべて失われ、現在のトランザクションはロールバックされます。 このような場合、アプリケーションでは接続を閉じて (または、データ ソース オブジェクトを解放して) から、再び開く必要があります。 接続時に、新しい接続はプリンシパル サーバーとなったミラー データベースに透過的にリダイレクトされます。クライアントが接続文字列またはデータ ソース オブジェクトを変更する必要はありません。  
  
 接続が最初に確立されると、プリンシパル サーバーはフェールオーバー パートナーの ID を、フェールオーバー発生時に使用されるクライアントに送信します。 アプリケーションが障害の発生したプリンシパル サーバーと最初の接続を確立しようとするとき、フェールオーバー パートナーの ID はクライアントに通知されていません。 クライアントがこのシナリオに対処できるように、failoverPartner 接続文字列プロパティ、およびオプションで [setFailoverPartner](../../connect/jdbc/reference/setfailoverpartner-method-sqlserverdatasource.md) データ ソース メソッドを使用することで、クライアントはフェールオーバー パートナーの ID を独自に指定できます。 クライアント プロパティはこのシナリオでのみ使用されます。プリンシパル サーバーが利用可能な場合は使用されません。  
  
> [!NOTE]  
>  接続文字列またはデータ ソース オブジェクトで failoverPartner が指定されている場合は、databaseName プロパティも設定する必要があります。これが設定されていないと、例外がスローされます。 failoverPartner および databaseName が明示的に指定されていないと、プリンシパル データベース サーバーに障害が発生した場合に、アプリケーションがフェールオーバーを実行しません。 つまり、透過的なリダイレクトは、failoverPartner および databaseName が明示的に指定された接続に対してのみ機能します。 FailoverPartner およびその他の接続文字列プロパティの詳細については、次を参照してください。[接続プロパティの設定](../../connect/jdbc/setting-the-connection-properties.md)します。  
  
 クライアントで指定されたフェールオーバー パートナー サーバーが、指定されたデータベースのフェールオーバー パートナーの役割を担っているサーバーを参照していない場合で、なおかつ参照先のサーバー/データベースがミラーリング機構に属している場合、接続はサーバーによって拒否されます。 [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md) クラスは [getFailoverPartner](../../connect/jdbc/reference/getfailoverpartner-method-sqlserverdatasource.md) メソッドを提供しますが、このメソッドは接続文字列または setFailoverPartner メソッドで指定されたフェールオーバー パートナーの名前のみを返します。 現在使用されている実際のフェールオーバー パートナーの名前を取得するには、次の [!INCLUDE[tsql](../../includes/tsql_md.md)] ステートメントを使用します。  
  
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
 [JDBC ドライバーによる SQL Server への接続](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)  
  
  

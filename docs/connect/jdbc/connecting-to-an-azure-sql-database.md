---
title: Azure SQL database への接続 |Microsoft ドキュメント
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
ms.topic: article
ms.assetid: 49645b1f-39b1-4757-bda1-c51ebc375c34
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 7e7452a001f96b38b8e2a6047a144a82b5f957a9
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="connecting-to-an-azure-sql-database"></a>Azure SQL Database への接続
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  このトピックを使用する場合、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]への接続に、[!INCLUDE[ssAzure](../../includes/ssazure_md.md)]です。 接続の詳細については、[!INCLUDE[ssAzure](../../includes/ssazure_md.md)]を参照してください。  
  
-   [SQL Azure データベース](http://go.microsoft.com/fwlink/?LinkID=202490)  
  
-   [方法: JDBC を使用して SQL Azure への接続](http://msdn.microsoft.com/library/gg715284.aspx)  
  
-   [Java での SQL Azure を使用します。](http://msdn.microsoft.com/library/windowsazure/hh749029(VS.103).aspx)

-   [Azure Active Directory 認証を利用した接続](../../connect/jdbc/connecting-using-azure-active-directory-authentication.md)  
  
## <a name="details"></a>詳細  
 接続するとき、 [!INCLUDE[ssAzure](../../includes/ssazure_md.md)]、呼び出しに、master データベースに接続する必要があります**SQLServerDatabaseMetaData.getCatalogs**です。  
 [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] ユーザー データベースからカタログのセット全体を返すことはできません。 **SQLServerDatabaseMetaData.getCatalogs** sys.databases ビューを使用して、カタログを取得します。 アクセス許可の説明を参照してください[sys.databases (SQL Azure データベース)](http://go.microsoft.com/fwlink/?LinkId=217396)を理解しておく**SQLServerDatabaseMetaData.getCatalogs**の動作を[!INCLUDE[ssAzure](../../includes/ssazure_md.md)]です。  
  
 接続のドロップ  
 接続するとき、[!INCLUDE[ssAzure](../../includes/ssazure_md.md)]一定の期間の後に、ファイアウォールなどのネットワーク コンポーネントによってアイドル接続が終了する可能性があります。 このコンテキストでのアイドル接続には、次の 2 種類があります。  
  
-   TCP レイヤーでのアイドル状態。これは、任意の数のネットワーク デバイスによる切断が可能である状態です。  
  
-   SQL Azure ゲートウェイによってアイドル状態で TCP **keepalive** (接続の確立、TCP の観点からアイドル状態でない)、発生する可能性がありますあっていないアクティブなクエリが 30 分間です。 この場合ゲートウェイは、TDS 接続が 30 分間アイドル状態であると判断し、接続を終了します。  
  
 ネットワーク コンポーネントによってアイドル接続がドロップされる状況を回避するには、ドライバーが読み込まれているオペレーティング システムで、次のレジストリ設定 (Windows 以外の場合はこれらに相当する設定) を行う必要があります。  
  
|レジストリ設定|推奨値|  
|----------------------|-----------------------|  
|HKEY_LOCAL_MACHINE \ SYSTEM \ CurrentControlSet \ Services \ Tcpip \ パラメーター \ KeepAliveTime|30000|  
|HKEY_LOCAL_MACHINE \ SYSTEM \ CurrentControlSet \ Services \ Tcpip \ パラメーター \ KeepAliveInterval|1000|  
|HKEY_LOCAL_MACHINE \ SYSTEM \ CurrentControlSet \ Services \ Tcpip \ パラメーター \ TcpMaxDataRetransmissions|10|  
  
 レジストリ設定を有効にするには、設定後にコンピューターを再起動する必要があります。  
  
 Windows Azure の実行時にこの操作を行うには、スタートアップ タスクを作成してこれらのレジストリ キーを追加します。  たとえば、次のスタートアップ タスクをサービス定義ファイルに追加します。  
  
```  
<Startup>  
    <Task commandLine="AddKeepAlive.cmd" executionContext="elevated" taskType="simple">  
    </Task>  
</Startup>  
```  
  
 次に、AddKeepAlive.cmd ファイルをプロジェクトに追加します。 [出力ディレクトリにコピー] を [常にコピーする] に設定します。 AddKeepAlive.cmd ファイルのサンプルを次に示します。  
  
```  
if exist keepalive.txt goto done  
time /t > keepalive.txt  
REM Workaround for JDBC keep alive on SQL Azure  
REG ADD HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters /v KeepAliveTime /t REG_DWORD /d 30000 >> keepalive.txt  
REG ADD HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters /v KeepAliveInterval /t REG_DWORD /d 1000 >> keepalive.txt  
REG ADD HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters /v TcpMaxDataRetransmissions /t REG_DWORD /d 10 >> keepalive.txt  
shutdown /r /t 1  
:done  
```  
  
 接続文字列内の UserId へのサーバー名の追加  
 バージョン 4.0 の前に、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]に接続するとき、 [!INCLUDE[ssAzure](../../includes/ssazure_md.md)]、接続文字列内の UserId にサーバー名を追加する必要がありました。 たとえば、 user@servernameのようにします。 以降のバージョン 4.0 では、 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]、追加する必要はなくなりました@servername接続文字列内の UserId にします。  
  
 暗号化の使用に必要な hostNameInCertificate の設定  
 接続するとき、[!INCLUDE[ssAzure](../../includes/ssazure_md.md)]を指定する必要があります**hostNameInCertificate**を指定する場合**暗号化 = true**です。 (接続文字列でサーバー名が場合*shortName*.*domainName*、設定、 **hostNameInCertificate**プロパティを\*.*domainName*)。  
  
 以下に例を示します。  
  
```  
jdbc:sqlserver://abcd.int.mscds.com;databaseName= myDatabase;user=myName;password=myPassword;encrypt=true;hostNameInCertificate= *.int.mscds.com;  
```  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーによる SQL Server への接続](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)  
  
  

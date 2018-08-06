---
title: Azure SQL database への接続 |Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 49645b1f-39b1-4757-bda1-c51ebc375c34
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e716ec94db3f37dc51136f55884ac0c9eb33d236
ms.sourcegitcommit: 6fa72c52c6d2256c5539cc16c407e1ea2eee9c95
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/27/2018
ms.locfileid: "39278743"
---
# <a name="connecting-to-an-azure-sql-database"></a>Azure SQL Database への接続
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  この記事では、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] を使用して [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] に接続する際に発生する問題について説明します。 [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] への接続に関する詳細については、次のトピックを参照してください。  
  
-   [SQL Azure データベース](http://go.microsoft.com/fwlink/?LinkID=202490)  
  
-   [JDBC を使用して SQL Azure に接続する方法](http://msdn.microsoft.com/library/gg715284.aspx)  
  
-   [Java での SQL Azure の使用](http://msdn.microsoft.com/library/windowsazure/hh749029(VS.103).aspx)

-   [Azure Active Directory 認証を利用した接続](../../connect/jdbc/connecting-using-azure-active-directory-authentication.md)  
  
## <a name="details"></a>詳細  
 接続するとき、[!INCLUDE[ssAzure](../../includes/ssazure_md.md)]を呼び出す、master データベースに接続する必要があります**SQLServerDatabaseMetaData.getCatalogs**します。  
 [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] では、ユーザー データベースからカタログ全体を返すことがサポートされていません。 **SQLServerDatabaseMetaData.getCatalogs では、sys.databases ビューを使用してカタログを取得します。 権限に関する情報を参照してください[sys.databases (SQL Azure データベース)](http://go.microsoft.com/fwlink/?LinkId=217396)を理解しておく**SQLServerDatabaseMetaData.getCatalogs**での動作を[!INCLUDE[ssAzure](../../includes/ssazure_md.md)]します。  
  
 接続のドロップ  
 [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] への接続時に非アクティブな状態が一定時間続くと、ファイアウォールなどのネットワーク コンポーネントにより、アイドル接続が終了されることがあります。 このコンテキストでのアイドル接続には、次の 2 種類があります。  
  
-   TCP レイヤーでのアイドル状態。これは、任意の数のネットワーク デバイスによる切断が可能である状態です。  
  
-   SQL Azure ゲートウェイによるアイドル状態。これは、TCP **keepalive** メッセージ (TCP から見て接続がアイドルでない状態にするため) が発生することはあっても、アクティブなクエリが 30 分間発生していないという状態です。 この場合ゲートウェイは、TDS 接続が 30 分間アイドル状態であると判断し、接続を終了します。  
  
 ネットワーク コンポーネントによってアイドル接続がドロップされる状況を回避するには、ドライバーが読み込まれているオペレーティング システムで、次のレジストリ設定 (Windows 以外の場合はこれらに相当する設定) を行う必要があります。  
  
|レジストリ設定|推奨値|  
|----------------------|-----------------------|  
|HKEY_LOCAL_MACHINE \ SYSTEM \ CurrentControlSet \ Services \ Tcpip \ パラメーター \ KeepAliveTime|30000|  
|HKEY_LOCAL_MACHINE \ SYSTEM \ CurrentControlSet \ Services \ Tcpip \ パラメーター \ KeepAliveInterval|1000|  
|HKEY_LOCAL_MACHINE \ SYSTEM \ CurrentControlSet \ Services \ Tcpip \ パラメーター \ TcpMaxDataRetransmissions|10|  
  
 設定後にコンピューターを再起動して、レジストリ設定を有効にします。  
  
 Windows Azure の実行時にこの操作を行うには、スタートアップ タスクを作成してこれらのレジストリ キーを追加します。  たとえば、次のスタートアップ タスクをサービス定義ファイルに追加します。  
  
```  
<Startup>  
    <Task commandLine="AddKeepAlive.cmd" executionContext="elevated" taskType="simple">  
    </Task>  
</Startup>  
```  
  
 次に、AddKeepAlive.cmd ファイルをプロジェクトに追加します。 [出力ディレクトリにコピー] を [常にコピーする] に設定します。 AddKeepAlive.cmd ファイルのサンプルを次に示します。  
  
```bat
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
 Version 4.0 より前の [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] では、[!INCLUDE[ssAzure](../../includes/ssazure_md.md)] に接続する際に、接続文字列内の UserId にサーバー名を追加する必要がありました。 たとえば、 user@servernameのようにします。 Version 4.0 以降の [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] では、接続文字列内の UserId に @servername を追加する必要がなくなりました。  
  
 暗号化の使用に必要な hostNameInCertificate の設定  
 接続するとき、[!INCLUDE[ssAzure](../../includes/ssazure_md.md)]を指定する必要があります**hostNameInCertificate**を指定する場合**暗号化 = true**します。 (接続文字列でサーバー名が場合*shortName*.*domainName*、設定、 **hostNameInCertificate**プロパティを\*.*domainName*)。  
  
 例 :  
  
```java
jdbc:sqlserver://abcd.int.mscds.com;databaseName= myDatabase;user=myName;password=myPassword;encrypt=true;hostNameInCertificate= *.int.mscds.com;  
```  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーによる SQL Server への接続](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)  
  
  

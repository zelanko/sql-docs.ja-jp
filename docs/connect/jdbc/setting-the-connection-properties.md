---
title: "接続プロパティの設定 |Microsoft ドキュメント"
ms.custom: 
ms.date: 04/11/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1b62700-f046-488d-bd6b-a5cd8fc345b7
caps.latest.revision: "154"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: a7c789e4a69230e3c1e99e3766223bf40628294f
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="setting-the-connection-properties"></a>接続プロパティの設定」を参照してください。
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  接続文字列のプロパティは、さまざまな方法で指定できます。  
  
-   名前として DriverManager クラスを使用して接続するときに、接続 URL における値のプロパティを = です。  
  
-   名前として = 値のプロパティで、*プロパティ*DriverManager クラスの Connect メソッドのパラメーターです。  
  
-   ドライバーのデータ ソースの適切な setter メソッドの値として指定できます。 例:  
  
    ```  
  
    datasource.setServerName(value)  
    datasource.setDatabaseName(value)  
  
    ```  
  
## <a name="remarks"></a>解説  
 プロパティ名の大文字と小文字は区別されず、重複したプロパティ名は次の順序で解決されます。  
  
1.  API 引数 (user、password など)  
  
2.  プロパティ コレクション。  
  
3.  接続文字列の最後のインスタンス。  
  
 プロパティ名には不明な値を使用することもできます。JDBC ドライバーはこのような値の大文字と小文字の区別について検証しません。  
  
 シノニムを使用できます。これは、重複したプロパティ名と同じ順序で解決されます。  
  
 次の表は、JDBC ドライバーで現在使用できるすべての接続文字列プロパティを示しています。  
  
|プロパティ|型|既定値|Description|  
|--------------|----------|-------------|-----------------|  
|accessToken|文字列|null|このプロパティを使用して、アクセス トークンを使用して SQL データベースに接続します。 **accessToken**接続 URL を使用して設定することはできません。|  
|applicationIntent|文字列|ReadWrite|アプリケーションがサーバーに接続するときのワークロードのタイプを宣言します。 指定できる値は**ReadOnly**と**ReadWrite**です。 詳細については、次を参照してください。 [High Availability, Disaster Recovery の JDBC ドライバー サポート](../../connect/jdbc/jdbc-driver-support-for-high-availability-disaster-recovery.md)です。|  
|applicationName|文字列<br /><br /> [128 文字以下]|null|アプリケーション名、または"[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]"名前が指定されていない場合。 さまざまな特定のアプリケーションを識別するために使用[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]プロファイリング ツールおよびロギング ツールです。|  
|認証 (authentication)|文字列|NotSpecified|Microsoft JDBC Driver 6.0 for SQL Server から始まり、この省略可能なプロパティは、接続に使用する SQL 認証方法を示します。 指定できる値は**ActiveDirectoryIntegrated**、 **ActiveDirectoryPassword**、 **SqlPassword**と既定**NotSpecified**です。<br /><br /> 使用して**ActiveDirectoryIntegrated**統合 Windows 認証を使用して SQL データベースに接続します。<br /><br /> 使用して**ActiveDirectoryPassword** Azure AD のプリンシパル名とパスワードを使用して SQL データベースに接続します。<br /><br /> 使用して**SqlPassword**を使用して、SQL Server に接続する**userName**/**ユーザー**と**パスワード**プロパティです。<br /><br /> 使用して**NotSpecified**上記のどの認証方法が必要な場合です。<br /><br /> **重要:**認証は、ActiveDirectoryIntegrated に設定されている場合、次の 2 つのライブラリをインストールする必要があります: **SQLJDBC_AUTH です。DLL** (JDBC ドライバー パッケージで使用可能) と Azure Active Directory の認証ライブラリの SQL Server (**ADALSQL です。DLL**) 複数の言語で使用可能になる (x86、amd64)、ダウンロード センターから[Microsoft Active Directory の認証ライブラリの Microsoft SQL Server](https://www.microsoft.com/en-us/download/details.aspx?id=48742)です。 JDBC ドライバーでは、バージョンのみがサポート**1.0.2028.318 以上**ADALSQL 用です。DLL です。<br /><br /> **注:**認証プロパティに設定すると任意の値以外の**NotSpecified**既定ではドライバーは Secure Sockets Layer (SSL) 暗号化を使用します。<br /><br /> Azure Active Directory 認証を構成する方法については、次を参照してください。[認証して SQL Database を使用して Azure Active Directory に接続する](https://azure.microsoft.com/en-us/documentation/articles/sql-database-aad-authentication/)です。|  
|authenticationScheme|文字列|"NativeAuthentication"|統合セキュリティの種類、アプリケーションを使用することを示します。 指定できる値は**java Kerberos**と既定**NativeAuthentication**です。<br /><br /> 使用する場合**authenticationScheme = java Kerberos**で完全修飾ドメイン名 (FQDN) を指定する必要があります、 **serverName**または**serverSpn**プロパティです。 指定しない場合は、エラーが発生します (Kerberos データベースにサーバーが見つからない)。<br /><br /> 使用する方法についての**authenticationScheme**を参照してください[を使用して Kerberos 統合認証を SQL Server への接続](../../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md)です。|  
|columnEncryptionSetting|文字列<br /><br /> ["Enabled"&#124;無効な"]|Disabled|「有効」に設定すると、Microsoft JDBC Driver 6.0 for SQL Server Always Encrypted (AE) 機能の先頭を使用します。 AE を有効にすると、JDBC ドライバーは SQL Server の暗号化されたデータベースの列に格納されている機密データについて透過的に暗号化と暗号化の解除を行います。<br /><br /> 参照してください[JDBC ドライバーで Always Encrypted を使用して](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md)詳細についてはします。<br /><br /> **注:** Always Encrypted は SQL Server 2016 またはそれ以降のバージョンで利用できます。|  
|databaseName、database|文字列<br /><br /> [128 文字以下]|null|接続するデータベース名です。 指定しない場合は、既定のデータベースへの接続が確立されます。|  
|disableStatementPooling|boolean<br /><br /> ["true"&#124;false"]|true|現在は、値 "true" のみがサポートされています。 "false" に設定した場合は、例外が発生します。|  
|enablePrepareOnFirstPreparedStatementCall|boolean<br /><br /> ["true"&#124;false"]|オプション|この構成が false に設定されている場合、準備されたステートメントの最初の実行が sp_executesql を呼び出すし、sp_prepexec を呼び出すし、準備されたステートメント ハンドルを実際にセットアップが 2 つ目の実行が発生したら、ステートメントを準備できません。|
|encrypt|boolean<br /><br /> ["true"&#124;false"]|オプション|指定するには、"true"に設定、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]サーバーにインストールされている証明書がある場合に、クライアントとサーバー間で送信されるすべてのデータに Secure Sockets Layer (SSL) 暗号化を使用します。 既定値は false です。<br /><br /> Microsoft JDBC Driver 6.0 for SQL Server から始まりに、新しい接続の設定 'authentication' が既定で SSL 暗号化を使用します。 詳細については、'authentication' プロパティを参照してください。|  
|failoverPartner|文字列|null|データベース ミラーリング構成で使用されるフェールオーバー サーバーの名前です。 このプロパティは、プリンシパル サーバーへの初期接続に失敗した場合に使用されます。初期接続が行われた後は、このプロパティは無視されます。 databaseName プロパティと組み合わせて使用する必要があります。<br /><br /> **注:**ドライバーは接続文字列で failoverPartner プロパティの一部として、フェールオーバー パートナー インスタンスのサーバー インスタンスのポート番号を指定することをサポートしていません。 ただし、プリンシパル サーバー インスタンスの serverName、instanceName、portNumber の各プロパティ、およびフェールオーバー パートナー インスタンスの failoverPartner プロパティを同じ接続文字列の中で指定することはできます。<br /><br /> 仮想ネットワーク名を指定する場合、**サーバー**接続プロパティでは、データベース ミラーリングを使用することはできません。 参照してください[High Availability, Disaster Recovery の JDBC ドライバー サポート](../../connect/jdbc/jdbc-driver-support-for-high-availability-disaster-recovery.md)詳細についてはします。|  
|fips|ブール値を [「真/偽」]|"false"|このプロパティは、fips が JVM を有効になっている**true**です。|
|fipsProvider|文字列|null|JVM で構成されている FIPS プロバイダーです。 リフレッシュ レート。 BCFIPS または SunPKCS11 NSS します。|
|gsscredential|org.ietf.jgss.GSSCredential|null|SQL Server 用 Microsoft JDBC Driver 6.2 以降、Kerberos 制約付き委任を使用するユーザーの資格情報は、このプロパティに渡されることができます。 <BR/>これで使用する必要があります**integratedSecurity**として**true**と**java Kerberos** **authenticationscheme**です。|
|hostNameInCertificate|文字列|null|検証に使用されるホスト名、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] SSL 証明書。<br /><br /> HostNameInCertificate プロパティが指定されていないかに設定の null の場合、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]を使用して、 **serverName**を検証するホスト名として、接続 URL のプロパティの値、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] SSL 証明書。<br /><br /> **注:**と組み合わせてこのプロパティは使用、**暗号化**/**認証**プロパティおよび**trustServerCertificate**プロパティです。 接続 Secure Sockets Layer (SSL) 暗号化を使用する場合にのみ、このプロパティが証明書の検証に影響し、 **trustServerCertificate**が"false"に設定します。 渡された値を確認してください**hostNameInCertificate**で、サブジェクト代替名 (SAN) SSL 接続のサーバー証明書を成功させるのには共通名 (CN) または DNS 名と完全に一致します。 詳細については、次を参照してください。[について SSL サポート](../../connect/jdbc/understanding-ssl-support.md)です。|  
|INSTANCENAME|文字列<br /><br /> [128 文字以下]|null|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]への接続にインスタンス名。 指定しない場合は、既定のインスタンスへの接続が確立されます。 instanceName と port の両方を指定する場合については、port の注を参照してください。<br /><br /> 仮想ネットワーク名を指定する場合、**サーバー**接続プロパティは使用できません**instanceName**接続プロパティです。 参照してください[High Availability, Disaster Recovery の JDBC ドライバー サポート](../../connect/jdbc/jdbc-driver-support-for-high-availability-disaster-recovery.md)詳細についてはします。|  
|integratedSecurity|boolean<br /><br /> ["true"&#124;false"]|オプション|Windows 資格情報を使用することを示すために、"true"に設定[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]Windows オペレーティング システムでします。 "true" の場合、JDBC ドライバーは、コンピューターまたはネットワーク ログオン時に提供された資格情報を見つけるために、ローカル コンピューターの資格情報のキャッシュを検索します。<br /><br /> "True"に設定 (で**authenticationscheme = java Kerberos**) で Kerberos 資格情報を使用することを示すために、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 Kerberos 認証の詳細については、次を参照してください。[を使用して Kerberos 統合認証を SQL Server への接続](../../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md)です。 <br /><br /> "false" の場合は、ユーザー名とパスワードを指定する必要があります。| 
|jaasConfigurationName|文字列|SQLJDBCDriver|SQL Server 用 Microsoft JDBC Driver 6.2 以降、SQL Server に接続するたびは Kerberos 接続を確立するために、独自の JAAS ログイン構成ファイルを持つことができます。 ログイン構成ファイルの名前は、このプロパティを介して渡されることができます。 <BR/> 既定では、ドライバーはプロパティを設定`useDefaultCcache = true`IBM Jvm のおよび`useTicketCache = true`他の Jvm をします。|
|keyStoreAuthentication|文字列|null| Microsoft JDBC Driver 6.0 for SQL Server から始まり、このプロパティはシームレスに Always Encrypted との接続を設定するキー ストアの場所を識別し、キー ストアへの認証に使用される認証方式を決定します。 Microsoft JDBC Driver 6.0 for SQL Server をサポートしている設定を Java キー ストアのシームレスにこのプロパティを設定する必要がありますを使用して"**keyStoreAuthentication = JavaKeyStorePassword**"です。 使用するにはこのプロパティも設定する必要が注、 **keyStoreLocation**と**keyStoreSecret** Java キー ストアのプロパティです。 <br/><br/>詳細については、次を参照してください。 [JDBC ドライバーで Always Encrypted を使用して](https://msdn.microsoft.com/library/mt591987%28v=sql.110%29.aspx?f=255&MSPPError=-2147217396)です。 
|keyStoreLocation|文字列|null|ときに**keyStoreAuthentication = JavaKeyStorePassword**、 **keyStoreLocation**プロパティは、Always Encrypted で使用する列マスター _ キーを格納する Java キーストア ファイルへのパスを識別します。データ。 パスがキーストア ファイル名を含める必要がありますに注意してください。<br/><br/>詳細については、次を参照してください。 [JDBC ドライバーで Always Encrypted を使用して](https://msdn.microsoft.com/library/mt591987%28v=sql.110%29.aspx?f=255&MSPPError=-2147217396)です。
|keyStoreSecret|文字列|null|ときに**keyStoreAuthentication = JavaKeyStorePassword**、 **keyStoreSecret**プロパティは、キーの場合と同様にキーストアに使用するパスワードを識別します。 Java キー ストアを使用するため、キーストアとキーのパスワード必要があります、同じであることに注意してください。<br/><br/>詳細については、次を参照してください。 [JDBC ドライバーで Always Encrypted を使用して](https://msdn.microsoft.com/library/mt591987%28v=sql.110%29.aspx?f=255&MSPPError=-2147217396)です。
|lastUpdateCount|boolean<br /><br /> ["true"&#124;false"]|true|値が "true" の場合、サーバーに渡された SQL ステートメントから最終的な更新数のみを返します。また、SELECT、INSERT、または DELETE ステートメントのいずれか 1 つで使用して、サーバーのトリガーにより追加された更新数を無視することができます。 このプロパティを "false" に設定すると、サーバーのトリガーにより返される更新数を含む、すべての更新数が返されます。<br /><br /> **注:**このプロパティは、これを使用する場合にのみ適用されます、 [executeUpdate](../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md)メソッドです。 他のすべてのメソッドの戻り値のすべての結果を実行し、カウントを更新します。 このプロパティは、サーバーのトリガーにより返される更新数にのみ影響します。 トリガーの実行の一部として得られる結果セットまたはエラーには影響しません。|  
|lockTimeout|int|-1|データベースがロック タイムアウトを通知するまでに待機する時間 (ミリ秒) です。既定では、無期限に待機します。 指定されている場合、この値は接続上のすべてのステートメントに対する既定値になります。 なお**Statement.setQueryTimeout()**特定のステートメントのタイムアウトを設定するために使用できます。 この値は、待機しないことを示す 0 に設定できます。|  
|loginTimeout|int [0..65535]|15|失敗した接続がタイムアウトするまで、ドライバーが待機する秒数。 0 の値は、タイムアウトが既定のシステム タイムアウトであることを示します。既定のシステム タイムアウトは、既定では 15 秒に指定されています。 0 以外の値は、ドライバーがタイムアウトを通知して接続を失敗させるまでに待機する時間 (秒) を示します。<br /><br /> 仮想ネットワーク名を指定する場合、**サーバー**接続プロパティでは、フェールオーバー接続が成功するための十分な時間を許可するのには 3 分間以上のタイムアウト値を指定する必要があります。 参照してください[High Availability, Disaster Recovery の JDBC ドライバー サポート](../../connect/jdbc/jdbc-driver-support-for-high-availability-disaster-recovery.md)詳細についてはします。|  
|multiSubnetFailover|ブール値|オプション|常に指定**multiSubnetFailover = true**の可用性グループ リスナーに接続するときに、[!INCLUDE[ssSQL11](../../includes/sssql11_md.md)]可用性グループ、または[!INCLUDE[ssSQL11](../../includes/sssql11_md.md)]フェールオーバー クラスター インスタンス。 **multiSubnetFailover = true**構成[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]を迅速に検出し、(現在) アクティブなサーバーへの接続を提供します。 可能な値は、true と false です。 参照してください[High Availability, Disaster Recovery の JDBC ドライバー サポート](../../connect/jdbc/jdbc-driver-support-for-high-availability-disaster-recovery.md)詳細についてはします。<br /><br /> プログラムからアクセスすることができます、 **multiSubnetFailover**接続プロパティに[getPropertyInfo](../../connect/jdbc/reference/getpropertyinfo-method-sqlserverdriver.md)、 [getMultiSubnetFailover](../../connect/jdbc/reference/getmultisubnetfailover-method-sqlserverdatasource.md)、および[setMultiSubnetFailover](../../connect/jdbc/reference/setmultisubnetfailover-method-sqlserverdatasource.md)です。<br /><br /> **注:** Microsoft JDBC Driver 6.0 for SQL Server 可用性グループ リスナーに接続するときは、true に multiSubnetFailover を設定する必要が不要になった以降します。 新しいプロパティ、 **transparentNetworkIPResolution**検出し、(現在) アクティブなサーバーへの接続は、これが既定では、有効になっています。|  
|packetSize|int [-1 &#124; 0 &#124; 512..32767]|8000|SQL Server との通信に使用されるネットワーク パケット サイズです (バイトで指定します)。 値が -1 の場合は、サーバーの既定のパケット サイズが使用されます。 値が 0 の場合は、最大値 (32767) が使用されます。 このプロパティが許容範囲外の値に設定されている場合は、例外が発生します。<br /><br /> **重要:**お勧めしません、暗号化が有効な場合に packetSize プロパティを使用する (暗号化 = true)。 使用すると、接続エラーが発生する可能性があります。 詳細については、次を参照してください。、 [setPacketSize](../../connect/jdbc/reference/setpacketsize-method-sqlserverdatasource.md)のメソッド、 [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md)クラスです。|  
|パスワード|文字列<br /><br /> [128 文字以下]|null|SQL ユーザー名とパスワードを持つ接続が発生した場合のデータベース パスワードです。<BR/>Kerberos 接続のプリンシパル名とパスワードを持つ場合は、このプロパティは Kerberos プリンシパルのパスワードに設定します。|  
|portNumber、port|int [0..65535]|1433|ポートを[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]がリッスンしています。 ポート番号が接続文字列に指定されている場合は、sqlbrowser に対する要求は作成されません。 port と instanceName の両方が指定されている場合は、指定されたポートへの接続が確立されます。 ただし、 **instanceName**を検証し、ポートが一致しない場合、エラーがスローされます。<br /><br /> **重要:**ことをお勧めするポート番号常に指定する、これは sqlbrowser を使用するよりも安全です。|  
|queryTimeout|int|0|クエリでは、タイムアウトまで待機する秒数が発生しました。 既定値は 0、無限のタイムアウトを意味します。|
|responseBuffering|文字列<br /><br /> ["full"&#124;アダプティブ"]|adaptive|このプロパティを "adaptive" に設定すると、必要に応じて最小限のデータがバッファリングされます。 既定のモードは "adaptive" です。<br /><br /> このプロパティが "full" に設定されている場合、ステートメントの実行時に結果セット全体がサーバーから読み取られます。<br /><br /> **注:**バージョン 1.2 の JDBC ドライバーをアップグレードした後、既定のバッファリング動作が"adaptive"にします。 場合は、アプリケーションでは、"responseBuffering"プロパティが設定しないと、アプリケーションで version 1.2 の既定の動作を保持する、接続のプロパティ、またはを使用して、responseBufferring プロパティを"full"を設定する必要があります、 [setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)のメソッド、 [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md)オブジェクト。|  
|selectMethod|文字列<br /><br /> [「直接」&#124;"カーソル"]|直接|このプロパティが "cursor" に設定されている場合、TYPE_FORWARD_ONLY および CONCUR_READ_ONLY のカーソルに対して接続上で作成されるクエリごとに、データベース カーソルが作成されます。 このプロパティは、通常、クライアントのメモリ内に収まらない非常に大きな結果セットをアプリケーションが生成する場合にのみ必要です。 このプロパティが "cursor" に設定されると、結果セットの行が限定された数だけクライアントのメモリに保持されます。 既定の動作では、すべての結果セットの行がクライアントのメモリに保持されます。 この動作により、アプリケーションがすべての行を処理する場合は、パフォーマンスが最も高くなります。|  
|sendStringParametersAsUnicode|boolean<br /><br /> ["true"&#124;false"]|true|場合、 **sendStringParametersAsUnicode**プロパティが"true"にパラメーターが Unicode 形式でサーバーに送信される文字列に設定します。<br /><br /> 場合、 **sendStringParametersAsUnicode**プロパティが"false"に設定、文字列パラメーターが Unicode ではなく ASCII/MBCS などの Unicode 以外の形式でサーバーに送信されます。<br /><br /> 既定値、 **sendStringParametersAsUnicode**プロパティが"true"です。<br /><br /> **注:** 、 **sendStringParametersAsUnicode**のパラメーター値を送信するときにのみ、プロパティがチェック**CHAR**、 **VARCHAR**、または**LONGVARCHAR** JDBC の型。 SetNString、setNCharacterStream、setNClob メソッドなど、新しい JDBC 4.0 national character メソッド[SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)と[SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)クラス、常にパラメーター値がこのプロパティの設定に関係なく、Unicode でサーバーに送信します。<br /><br /> パフォーマンスを最適化、 **CHAR**、 **VARCHAR**、および**LONGVARCHAR** JDBC データ型では、アプリケーションを設定する必要があります、 **sendStringParametersAsUnicode**プロパティを"false"を使用して、setString、setCharacterStream、setClob 非 national character メソッドの[SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)と[SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)クラスです。<br /><br /> アプリケーションを設定すると、 **sendStringParametersAsUnicode**プロパティを Unicode データにアクセスする非 national character メソッドは、サーバー側の型を使用して、"false"(など**nchar**、 **nvarchar**と**ntext**)、データベースの照合順序は非 national character メソッドで渡される文字列パラメーターの文字をサポートしていない場合、一部のデータが失われる可能性があります。<br /><br /> アプリケーションが、setNString、setNCharacterStream、setNClob の national character メソッドを使用する必要がありますに注意してください、 [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)と[SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)クラス**NCHAR**、 **NVARCHAR**、および**LONGNVARCHAR** JDBC データ型。|  
|sendTimeAsDatetime|boolean<br /><br /> ["true"&#124;false"]|true|このプロパティで追加されました[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]JDBC Driver 3.0 です。<br /><br /> Java.sql.Time 値としてサーバーに送信する場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **datetime**値。<br /><br /> Java.sql.Time 値としてサーバーに送信する false の場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]**時間**値。<br /><br /> **sendTimeAsDatetime**もで変更できるプログラムで[SQLServerDataSource.setSendTimeAsDatetime](../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md)です。<br /><br /> 今後のリリースでは、このプロパティの既定値が変更される可能性があります。<br /><br /> 方法の詳細については[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]java.sql.Time 値を構成するサーバーに送信する、前に、次を参照してください。 [java.sql.Time 値を構成する方法は、サーバーに送信される](../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md)です。|  
|serverName、server|文字列|null|実行するコンピューター[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。<br /><br /> 仮想ネットワーク名を指定することも、[!INCLUDE[ssHADR](../../includes/sshadr_md.md)]可用性グループです。 参照してください[High Availability, Disaster Recovery の JDBC ドライバー サポート](../../connect/jdbc/jdbc-driver-support-for-high-availability-disaster-recovery.md)詳細についてはします。|  
|serverNameAsACE|boolean<br /><br /> ["true"&#124;false"]|オプション|Microsoft JDBC Driver 6.0 for SQL Server 以降では、"true" に設定すると、ドライバーが Unicode のサーバー名を互換性のある ASCII エンコード (Punycode) に変換して接続する必要があることを示します。 この設定が false の場合、ドライバーは、ユーザーによって提供されたサーバー名を使用して接続します。<br /><br /> 参照してください[JDBC ドライバーの国際対応機能](../../connect/jdbc/international-features-of-the-jdbc-driver.md)詳細についてはします。|  
|serverPreparedStatementDiscardThreshold|Integer|10|サーバーで未処理のハンドルをクリーンアップするための呼び出しが実行される前に、数の未処理の準備されたステートメント破棄操作 (sp_unprepare) が接続ごとの未処理できますを制御します。 場合は、設定は、< = 1 解除-を準備する準備されたステートメント閉じるでアクションをすぐに実行されます。 設定されている場合 > 1 これらの呼び出しは sp_unprepare の多くの呼び出しのオーバーヘッドを避けるためにまとめてバッチ処理します。|
|serverSpn|文字列|null|Microsoft JDBC Driver 4.2 for SQL Server 以降では、このオプションのプロパティを使用して Java Kerberos 接続のサービス プリンシパル名 (SPN) を指定できます。  組み合わせて使用**authenticationScheme**です。<br /><br /> 形式での SPN を指定することができます:"MSSQLSvc/fqdn:port@REALM"いる fqdn は完全修飾ドメイン名、port はポート番号、および領域とは大文字で SQL Server の Kerberos 領域です。<br /><br /> 注: @REALM (Kerberos 構成で指定) と同じクライアントの既定の領域は、SQL Server の Kerberos 領域と同じ場合は省略可能です。<br /><br /> 使用する方法についての**serverSpn** Java Kerberos を参照してください。[を使用して Kerberos 統合認証を SQL Server への接続](../../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md)です。|  
|socketTimeout|int|0|ソケットのタイムアウトが発生する前に待機するミリ秒数を読み取るか、受け入れます。 既定値は 0、無限のタイムアウトを意味します。|
|TransparentNetworkIPResolution|boolean<br /><br /> ["true"&#124;false"]|true|Microsoft JDBC Driver 6.0 for SQL Server、このプロパティ、transparentNetworkIPResolution 以降、迅速に検出し、(現在) アクティブなサーバーへの接続を提供します。 使用可能な値は true または false 場合は true で、既定値として。<br /><br /> アプリケーションは Microsoft JDBC Driver 6.0 for SQL Server、以前への接続文字列を設定する必要がある"multiSubnetFailover = true"を AlwaysOn 可用性グループに接続されているかを示します。 MultiSubnetFailover 接続キーワードを true に設定せず、アプリケーションは、AlwaysOn 可用性グループへの接続中にタイムアウトを発生する可能性があります。 Microsoft JDBC Driver 6.0 for SQL Server から始まり、multiSubnetFailover もはや、true に設定するアプリケーションは必要ありません。 <br /><br />**注:**とき transparentNetworkIPResolution = true の場合、最初の接続試行は 500 ミリ秒タイムアウトとして。 後続の試みは、multiSubnetFailover プロパティで使用するタイムアウトと同じロジックを使用します。|  
|trustServerCertificate|boolean<br /><br /> ["true"&#124;false"]|オプション|指定するには、"true"に設定、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]は検証されません、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] SSL 証明書。<br /><br /> "True"の場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]通信レイヤーが SSL で暗号化されている場合は、SSL 証明書が自動的に信頼します。<br /><br /> "False"の場合、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]サーバー SSL 証明書を検証します。 サーバー証明書の検証が失敗した場合は、エラーが発生して接続が終了します。 既定値は"false"です。 渡された値を確認してください**serverName**が成功する SSL 接続のサーバー証明書のサブジェクト代替名の Common Name (CN) または DNS 名と完全に一致します。 詳細については、次を参照してください。[について SSL サポート](../../connect/jdbc/understanding-ssl-support.md)です。<br /><br /> **注:**と組み合わせてこのプロパティは使用、**暗号化**/**認証**プロパティです。 このプロパティは、接続が SSL 暗号化を使用する場合にのみサーバー SSL 証明書の検証をのみ影響します。|  
|trustStore|文字列|null|証明書の trustStore ファイルへのパス (ファイル名を含む) です。 trustStore ファイルには、クライアントが信頼する証明書の一覧が含まれています。<br /><br /> このプロパティが指定されていないか null に設定されている場合、ドライバーは、信頼マネージャー ファクトリの検索ルールに従って、使用する証明書ストアを決定します。<br /><br /> **既定の SunX509 TrustManagerFactory では、次の検索順序で信頼済みマテリアルを検索しようとしています。**<br /><br /> Java 仮想マシン (JVM) システム プロパティの "javax.net.ssl.trustStore" で指定されたファイル<br /><br /> "\<java ホーム >/ライブラリ/セキュリティ/jssecacerts"ファイル。<br /><br /> "\<java ホーム >/ライブラリ/セキュリティ/cacerts"ファイル。<br /><br /> <br /><br /> 詳細については、Sun Microsystems の Web サイトで、SUNX509 TrustManager Interface に関するドキュメントを参照してください。<br /><br /> **注:**接続 SSL 暗号化を使用する場合にのみにこのプロパティが証明書の trustStore の検索にのみに影響し、 **trustServerCertificate**プロパティが"false"に設定します。|  
|trustStorePassword|文字列|null|trustStore データの整合性を確認するために使用するパスワードです。<br /><br /> trustStore プロパティは設定されているが trustStorePassword プロパティは設定されていない場合、trustStore の整合性は確認されません。<br /><br /> trustStore プロパティと trustStorePassword プロパティの両方が指定されていない場合、ドライバーでは、JVM システム プロパティの "javax.net.ssl.trustStore" と "javax.net.ssl.trustStorePassword" が使用されます。 "javax.net.ssl.trustStorePassword" システム プロパティが指定されていない場合、trustStore の整合性は確認されません。<br /><br /> trustStore プロパティは設定されていないが trustStorePassword プロパティは設定されている場合、JDBC ドライバーでは、"javax.net.ssl.trustStore" で指定されたファイルがトラスト ストアとして使用され、指定された trustStorePassword を使用してトラスト ストアの整合性が確認されます。 これは、クライアント アプリケーションでパスワードを JVM システム プロパティに格納しないようにする場合に必要となることがあります。<br /><br /> **注:** trustStorePassword プロパティのみに影響を与える証明書の trustStore の検索、接続が SSL 接続を使用する場合にのみ、 **trustServerCertificate**プロパティが"false"に設定します。|  
|trustStoreType|文字列|JKS|PKCS12 または型のいずれかで FIPS プロバイダーによって定義 FIPS モード セット信頼ストアの種類。|
|user、userName|文字列<br /><br /> [128 文字以下]|null|データベース ユーザーの SQL ユーザー名とパスワードを持つ接続が発生した場合。<BR/>Kerberos 接続のプリンシパル名とパスワードを持つ場合は、このプロパティは Kerberos プリンシパル名に設定します。|  
|workstationID|文字列<br /><br /> [128 文字以下]|\<空の文字列 >|ワークステーション ID。 さまざまな特定のワークステーションを識別するために使用[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]プロファイリング ツールおよびロギング ツールです。 指定されていない場合、\<空の文字列 > を使用します。|  
|xopenStates|boolean<br /><br /> ["true"&#124;false"]|オプション|"true" に設定すると、ドライバーが XOPEN 互換の状態コードを例外で返します。 既定では、SQL 99 の状態コードを返します。|  

> [!NOTE]  
>  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]サーバー ANSI_DEFAULTS および IMPLICIT_TRANSACTIONS 以外の接続プロパティの既定値を取得します。 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]を ON に ANSI_DEFAULTS を自動的に設定し、IMPLICIT_TRANSACTIONS は OFF にします。  

> [!Note]
> 重要: 認証は、ActiveDirectoryPassword に設定されている場合、次のライブラリは必要がありますクラスパスに含まれる: [azure active directory-ライブラリ-用の java](https://github.com/AzureAD/azure-activedirectory-library-for-java)です。 確認できます[Maven リポジトリ](https://mvnrepository.com/artifact/com.microsoft.azure/adal4j)です。 ライブラリとその依存関係をダウンロードする最も簡単な方法で使用されている Maven: 
 >1. まず、Maven、システムにインストールします。 
 >2. 移動して、 [GitHub ページ](https://github.com/Microsoft/mssql-jdbc)ドライバーの
 >3. Pom.xml ファイルをダウンロードします。
 >4. ライブラリとその依存関係をダウンロードする次の Maven コマンドを実行します mvn 依存関係: コピー-依存関係。
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーによる SQL Server への接続](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)  
 [FIPS モード](../../connect/jdbc/fips-mode.md)
  
  

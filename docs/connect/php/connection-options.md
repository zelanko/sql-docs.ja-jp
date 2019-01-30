---
title: 接続のオプション |Microsoft Docs
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 6d1ea295-8e34-438e-8468-4bbc0f76192c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1dc50fb96c6ff5e88119186ec81f9608f25f42c3
ms.sourcegitcommit: 1e28f923cda9436a4395a405ebda5149202f8204
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55044835"
---
# <a name="connection-options"></a>接続オプション
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

このトピックでは、連想配列で許可されているオプション (SQLSRV ドライバーで [sqlsrv_connect](../../connect/php/sqlsrv-connect.md) を使用する場合)、またはデータ ソース名 (dsn) で許可されているキーワード (PDO_SQLSRV ドライバーで [PDO::__construct](../../connect/php/pdo-construct.md) を使用する場合) を一覧に示します。  

## <a name="table-of-connection-options"></a>接続オプションの表

|Key|[値]|[説明]|既定|  
|-------|---------|---------------|-----------|  
|APP|String|トレースで使用されるアプリケーション名を指定します。|値は設定されません。|  
|ApplicationIntent|String|アプリケーションがサーバーに接続するときのワークロードのタイプを宣言します。 有効値は、ReadOnly と ReadWrite です。<br /><br />詳細については[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]サポート[!INCLUDE[ssHADR](../../includes/sshadr_md.md)]を参照してください[高可用性、ディザスター リカバリーのためサポート](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)します。|ReadWrite|  
|AttachDBFileName|String|サーバーがアタッチするデータベース ファイルを指定します。|値は設定されません。|  
|[認証]|次の文字列のいずれか:<br /><br />'SqlPassword'<br /><br />'ActiveDirectoryPassword'|認証モードを指定します。|未設定。|  
|CharacterSet<br /><br />(PDO_SQLSRV ドライバーではサポートされていません)|String|サーバーにデータを送信するために使用する文字セットを指定します。<br /><br />可能な値は SQLSRV_ENC_CHAR と UTF-8 です。 詳細については、「[ソフト NUMA を使用するように組み込みの UTF-8 サポートを使用した UTF-8 データの送信と取得](../../connect/php/how-to-send-and-retrieve-utf-8-data-using-built-in-utf-8-support.md)」をご覧ください。|SQLSRV_ENC_CHAR|  
|ColumnEncryption|**[有効]** または **[無効]**|Always Encrypted 機能が有効か無効かどうかを指定します。 |Disabled|  
|ConnectionPooling|接続プールを有効にするには、1 または **true** 。<br /><br />接続プールを無効にするには、0 または **false** 。|接続を接続プールから割り当てる (1 または **true**) か、割り当てない (0 または **false**) かを指定します。<sup>1</sup>|**true** (1)|  
|ConnectRetryCount|0 ~ 255 (両端を含む) の整数|を行う前に切断された接続を再確立を試みるの最大数。 既定では、発生した場合に、接続を再確立するため 1 回の試行が行われます。 値の 0 の場合は、再接続は試行されません。|1|  
|ConnectRetryInterval|1 ~ 60 (包括) の整数|時間 (秒単位) の間には、接続が再確立を試行します。 アプリケーションでは、接続が破損を検出するとすぐに再接続を試み、再試行する前に ConnectRetryInterval 秒待機します。 このキーワードには、ConnectRetryCount が 0 に等しい場合は無視されます。|1|  
|データベース|String|確立中の接続に使用されているデータベースの名前を指定します<sup>2</sup>。|使用されているログインの既定のデータベース。|  
|Driver|String|SQL Server と通信するために使用する Microsoft ODBC ドライバーを指定します。<br /><br />有効な値は次のとおりです。<br />ODBC Driver 17 for SQL Server<br />ODBC Driver 13 for SQL Server<br />ODBC Driver 11 for SQL Server (Windows のみ)。|Driver キーワードが指定されていないときに Microsoft Drivers for PHP for SQL Server しようとすると、システムでサポートされている Microsoft ODBC ドライバーを検索以降、最新の ODBC ではこれにします。|  
|Encrypt|暗号化を有効にするには、1 または **true** 。<br /><br />暗号化を無効にするには、0 または **false** 。|SQL Server との通信を暗号化する (1 または **true**) か、暗号化しない (0 または **false**) かを指定します<sup>3</sup>。|**false** (0)|  
|Failover_Partner|String|プライマリ サーバーが利用できないときに使用する、データベースのミラーのサーバーおよびインスタンス (有効かつ構成されている場合) を指定します。<br /><br />Failover_Partner を MultiSubnetFailover とともに使用する場合には、制限があります。 詳細については、次を参照してください。[高可用性、ディザスター リカバリーのサポート](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)します。|値は設定されません。|  
|KeyStoreAuthentication|**KeyVaultPassword**<br /><br />**KeyVaultClientSecret**|Azure Key Vault にアクセスするための認証方法です。 資格情報の種類は KeyStorePrincipalId KeyStoreSecret と使用を制御します。 詳細については、次を参照してください。[を使用して Azure Key Vault](../../connect/php/using-always-encrypted-php-drivers.md###using-azure-key-vault)します。|未設定。|
|KeyStorePrincipalId|String|Azure Key Vault にアクセスしようとしました。 アカウントの識別子。 <br /><br />KeyStoreAuthentication 場合**KeyVaultPassword**、Azure Active Directory のユーザー名があります。 <br /><br />KeyStoreAuthentication 場合**KeyVaultClientSecret**アプリケーションのクライアント id これでなければなりません。|未設定。|
|KeyStoreSecret|String|Azure Key Vault にアクセスしようとしました。 アカウントの資格情報シークレット。 <br /><br />KeyStoreAuthentication 場合**KeyVaultPassword**、Azure Active Directory パスワードを必要があります。 <br /><br />KeyStoreAuthentication 場合**KeyVaultClientSecret**アプリケーションのクライアント シークレットがあります。|未設定。|
|LoginTimeout|整数 (SQLSRV ドライバー)<br /><br />文字列 (PDO_SQLSRV ドライバー)|接続の試行に失敗するまで待機する秒数を指定します。|タイムアウトはありません。|  
|MultipleActiveResultSets|複数のアクティブな結果セットを使用するには、1 または **true** 。<br /><br />複数のアクティブな結果セットを無効にするには、0 または **false** 。|複数のアクティブな結果セット (MARS) のサポートを無効にするか、または明示的に有効にします。<br /><br />詳細については、「[ソフト NUMA を使用するように複数のアクティブな結果セットを無効にする&#40;MARS&#41;](../../connect/php/how-to-disable-multiple-active-resultsets-mars.md)します。|true (1)|  
|MultiSubnetFailover|String|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 可用性グループまたは [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] フェールオーバー クラスター インスタンスの可用性グループ リスナーに接続する際には、必ず **multiSubnetFailover=yes** を指定してください。 **multiSubnetFailover=yes** によって、(現在) アクティブなサーバーを迅速に検出し、接続するように [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] が構成されます。 可能な値は Yes と No です。<br /><br />詳細については[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]サポート[!INCLUDE[ssHADR](../../includes/sshadr_md.md)]を参照してください[高可用性、ディザスター リカバリーのためサポート](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)します。|いいえ|  
|PWD<br /><br />(PDO_SQLSRV ドライバーではサポートされていません)|String|SQL Server 認証で接続するときに使用するユーザー ID に関連付けるパスワードを指定します<sup>4</sup>。|値は設定されません。|  
|QuotedId|SQL-92 ルールを使用するには、1 または **true**。<br /><br />レガシ ルールを使用するには、0 または **false** 。|引用符で囲まれた識別子に SQL-92 ルールを使用する (1 または **true**) か、またはレガシ Transact-SQL ルールを使用する (0 または **false**) かを指定します。|**true** (1)|  
|ReturnDatesAsStrings<br /><br />(PDO_SQLSRV ドライバーではサポートされていません)|日付/時刻型を文字列として返すには、1 または **true** 。<br /><br />日付/時刻型を PHP **DateTime** 型として返すには、0 または **false** 。|日付/時刻型 (datetime、date、time、datetime2、および datetimeoffset) を文字列または PHP 型として取得します。 PDO_SQLSRV ドライバーを使用する場合、日付は文字列として返されます。 PDO_SQLSRV ドライバーには **datetime** 型はありません。<br /><br />詳細については、「[ソフト NUMA を使用するようにSQLSRV ドライバーを使用して日付/時刻型を文字列として取得する](../../connect/php/how-to-retrieve-date-and-time-type-as-strings-using-the-sqlsrv-driver.md)」をご覧ください。|**false**|  
|スクロール可能|String|「buffered」は、結果セット全体をメモリ内にキャッシュするために、クライアント側の (バッファー) カーソルが必要ですることを示します。 詳細については、「[カーソルの種類 &#40;SQLSRV ドライバー&#41;](../../connect/php/cursor-types-sqlsrv-driver.md)」を参照してください。|順方向専用カーソル|  
|[サーバー]<br /><br />(SQLSRV ドライバーではサポートされていません)|String|接続する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス。<br /><br />また、AlwaysOn 可用性グループへの接続に仮想ネットワーク名を指定することもできます。 詳細については[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]サポート[!INCLUDE[ssHADR](../../includes/sshadr_md.md)]を参照してください[高可用性、ディザスター リカバリーのためサポート](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)します。|サーバーは必須キーワードです (ただし、接続文字列の最初のキーワードである必要はありません)。 サーバー名がキーワードに渡されない場合は、ローカル インスタンスへの接続が試行されます。<br /><br />サーバーに渡される値には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの名前またはインスタンスの IP アドレスを指定できます。 必要に応じて、ポート番号を指定できます (たとえば、`sqlsrv:server=(local),1033`)。<br /><br />[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] のバージョン 3.0 以降では、 `server=(localdb)\instancename`で LocalDB インスタンスを指定することもできます。 詳細については、次を参照してください。 [LocalDB のサポート](../../connect/php/php-driver-for-sql-server-support-for-localdb.md)します。|  
|TraceFile|String|トレース データに使用するファイルのパスを指定します。|値は設定されません。|  
|TraceOn|トレースを有効にするには、1 または **true** 。<br /><br />トレースを無効にするには、0 または **false** 。|確立中の接続に対して ODBC トレースを有効にする (1 または **true**) か、または無効にする (0 または **false**) かを指定します。|**false** (0)|  
|TransactionIsolation|SQLSRV ドライバーは、次の値を使用します。<br /><br />SQLSRV_TXN_READ_UNCOMMITTED<br /><br />SQLSRV_TXN_READ_COMMITTED<br /><br />SQLSRV_TXN_REPEATABLE_READ<br /><br />SQLSRV_TXN_SNAPSHOT<br /><br />SQLSRV_TXN_SERIALIZABLE<br /><br />PDO_SQLSRV ドライバーは、次の値を使用します。<br /><br />PDO::SQLSRV_TXN_READ_UNCOMMITTED<br /><br />PDO::SQLSRV_TXN_READ_COMMITTED<br /><br />PDO::SQLSRV_TXN_REPEATABLE_READ<br /><br />PDO::SQLSRV_TXN_SNAPSHOT<br /><br />PDO::SQLSRV_TXN_SERIALIZABLE|トランザクション分離レベルを指定します。<br /><br />トランザクション分離の詳細については、SQL Server のドキュメントの「[SET TRANSACTION ISOLATION LEVEL](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md)」を参照してください。|SQLSRV_TXN_READ_COMMITTED<br /><br />内の複数の<br /><br />PDO::SQLSRV_TXN_READ_COMMITTED|  
|TransparentNetworkIPResolution|**[有効]** または **[無効]**|ホスト名に関連付けられているホスト名の IP が応答しないと、複数の ip アドレスがある 1 つ目が解決されると、接続シーケンスを影響を与えます。<br /><br />別の接続シーケンスを提供する MultiSubnetFailover とやり取りします。 詳細については、次を参照してください。[透過的なネットワーク IP 解決](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)または[透過的なネットワーク IP 解決を使用して](https://docs.microsoft.com/sql/connect/odbc/using-transparent-network-ip-resolution)します。|有効|
|TrustServerCertificate|証明書を信頼する場合は、1 または **true** 。<br /><br />証明書を信頼しない場合は、0 または **false** 。|クライアントが自己署名サーバー証明書を信頼する (1 または **true**) か、または拒否する (0 または **false**) かを指定します。|**false** (0)|  
|UID<br /><br />(PDO_SQLSRV ドライバーではサポートされていません)|String|SQL Server 認証で接続するときに使用するユーザー ID を指定します<sup>4</sup>。|値は設定されません。|  
|WSID|String|トレースするコンピューターの名前を指定します。|値は設定されません。|  

1. `ConnectionPooling`属性を使用して、Linux およびファルダで接続プールを有効または無効にすることはできません 「[接続のプール (Microsoft SQL Server 用 Drivers for PHP)](../../connect/php/connection-pooling-microsoft-drivers-for-php-for-sql-server.md)」を参照してください。

2. 確立された接続で実行されるすべてのクエリは、*Database* 属性で指定されたデータベースに対して行われます。 ただし、ユーザーが適切なアクセス許可を持っている場合は、完全修飾名を使用して他のデータベース内のデータにアクセスできます。 たとえば、*master* データベースが *Database* 接続属性で設定されている場合でも、完全修飾名を使用して、*AdventureWorks.HumanResources.Employee* テーブルにアクセスする Transact-SQL クエリを実行できます。  

3. *Encryption* を有効にすると、データの暗号化に必要な計算オーバーヘッドにより、いくつかのアプリケーションのパフォーマンスに影響を与える可能性があります。  

4. 接続する *UID* 認証で接続する場合は、 *PWD* 属性と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 属性の両方を設定する必要があります。  

サポートされているキーの多くは、ODBC 接続文字列属性です。 ODBC 接続文字列については、「 [SQL Server Native Client での接続文字列キーワードの使用](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)」を参照してください。

## <a name="see-also"></a>参照  
[サーバーへの接続](../../connect/php/connecting-to-the-server.md)  

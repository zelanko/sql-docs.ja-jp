---
title: 接続オプション |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6d1ea295-8e34-438e-8468-4bbc0f76192c
caps.latest.revision: 37
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a176aaa76934c10c4b7cd3526b59d889d1533268
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35307241"
---
# <a name="connection-options"></a>接続オプション
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

このトピックでは、連想配列で許可されているオプション (SQLSRV ドライバーで [sqlsrv_connect](../../connect/php/sqlsrv-connect.md) を使用する場合) または データ ソース名 (dsn) で許可されているキーワード (PDO_SQLSRV ドライバーで [PDO::__construct](../../connect/php/pdo-construct.md) を使用する場合) を一覧表示しています。

## <a name="table-of-connection-options"></a>接続オプションの表
|Key|値|説明|既定|  
|-------|---------|---------------|-----------|  
|APP|String|トレースで使用されるアプリケーション名を指定します。|値は設定されません。|  
|ApplicationIntent|String|アプリケーションがサーバーに接続するときのワークロードのタイプを宣言します。 有効値は、ReadOnly と ReadWrite です。<br /><br />詳細については[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]サポート[!INCLUDE[ssHADR](../../includes/sshadr_md.md)]を参照してください[高可用性、災害復旧をサポート](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)です。|ReadWrite|  
|AttachDBFileName|String|サーバーがアタッチするデータベース ファイルを指定します。|値は設定されません。|  
|[認証]|次の文字列のいずれかです。<br /><br />'SqlPassword'<br /><br />'ActiveDirectoryPassword'|認証モードを指定します。|設定されていません。|  
|CharacterSet<br /><br />(PDO_SQLSRV ドライバーではサポートされていません)|String|サーバーにデータを送信するために使用する文字セットを指定します。<br /><br />可能な値は SQLSRV_ENC_CHAR と UTF-8 です。 詳細については、「 [方法: 組み込みの UTF-8 サポートを使用した UTF-8 データの送信と取得](../../connect/php/how-to-send-and-retrieve-utf-8-data-using-built-in-utf-8-support.md)」を参照してください。|SQLSRV_ENC_CHAR|  
|ColumnEncryption<br /><br />(Windows でのみサポート)|**有効になっている**または**無効になっています。**|Always Encrypted 機能が有効かどうかを指定します。 |Disabled|  
|ConnectionPooling|接続プールを有効にするには、1 または **true** 。<br /><br />接続プールを無効にするには、0 または **false** 。|接続が接続プールから割り当てられているかどうかを指定します (1 または**true**) か (0 または**false**).<sup>1</sup>|**true** (1)|  
|ConnectRetryCount|0 ~ 255 (包括) の整数|渡す前に切断された接続を再確立を試みるの最大数。 既定では、1 回の試行が壊れている場合、接続を再確立しようとするは。 値の 0 の場合は、再接続は試行されません。|1|  
|ConnectRetryInterval|1 ~ 60 (包括) の整数|時間 (秒)、間には、接続が再確立を試みます。 アプリケーションでは、接続が破損を検出するとすぐに再接続を試みますされ、再試行する前に ConnectRetryInterval 秒待機し。 このキーワードには、ConnectRetryCount が 0 に等しい場合は無視されます。|1|  
|[データベース]|String|確立中の接続の使用中で、データベースの名前を指定<sup>2</sup>です。|使用されているログインの既定のデータベース。|  
|Driver|String|SQL Server と通信するために使用する Microsoft ODBC ドライバーを指定します。<br /><br />有効な値は次のとおりです。<br />SQL Server 用 ODBC Driver 17<br />ODBC Driver 13 for SQL Server<br />ODBC Driver 11 for SQL Server (Windows のみ)。|Driver キーワードが指定されていない Microsoft Drivers for PHP for SQL Server とシステムでは、サポートされている Microsoft ODBC ドライバーの種類の存在を検出と ODBC の最新バージョンで開始されます。|  
|Encrypt|暗号化を有効にするには、1 または **true** 。<br /><br />暗号化を無効にするには、0 または **false** 。|SQL Server との通信を暗号化するかどうかを指定します (1 または**true**) か暗号化しない (0 または**false**)<sup>3</sup>です。|**false** (0)|  
|Failover_Partner|String|プライマリ サーバーが利用できないときに使用する、データベースのミラーのサーバーおよびインスタンス (有効かつ構成されている場合) を指定します。<br /><br />Failover_Partner を MultiSubnetFailover とともに使用する場合には、制限があります。 詳細については、次を参照してください。 [High Availability, Disaster Recovery のサポート](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)です。|値は設定されません。|  
|LoginTimeout|整数 (SQLSRV ドライバー)<br /><br />文字列 (PDO_SQLSRV ドライバー)|接続の試行に失敗するまで待機する秒数を指定します。|タイムアウトはありません。|  
|MultipleActiveResultSets|複数のアクティブな結果セットを使用するには、1 または **true** 。<br /><br />複数のアクティブな結果セットを無効にするには、0 または **false** 。|複数のアクティブな結果セット (MARS) のサポートを無効にするか、または明示的に有効にします。<br /><br />詳細については、次を参照してください。[する方法: 複数のアクティブな結果を無効にする&#40;MARS&#41;](../../connect/php/how-to-disable-multiple-active-resultsets-mars.md)です。|true (1)|  
|MultiSubnetFailover|String|常に指定**multiSubnetFailover = [はい]** の可用性グループ リスナーに接続するときに、[!INCLUDE[ssSQL11](../../includes/sssql11_md.md)]可用性グループ、または[!INCLUDE[ssSQL11](../../includes/sssql11_md.md)]フェールオーバー クラスター インスタンス。 **multiSubnetFailover = yes**構成[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]を迅速に検出し、(現在) アクティブなサーバーへの接続を提供します。 可能な値は Yes と No です。<br /><br />詳細については[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]サポート[!INCLUDE[ssHADR](../../includes/sshadr_md.md)]を参照してください[高可用性、災害復旧をサポート](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)です。|いいえ|  
|PWD<br /><br />(PDO_SQLSRV ドライバーではサポートされていません)|String|SQL Server 認証で接続するときに使用されるユーザー ID に関連付けられているパスワードを指定します<sup>4</sup>です。|値は設定されません。|  
|QuotedId|1 または**true** sql-92 ルールを使用します。<br /><br />レガシ ルールを使用するには、0 または **false** 。|引用符で囲まれた識別子に sql-92 ルールを使用するかどうかを指定します (1 または**true**) またはレガシ TRANSACT-SQL ルールを使用する (0 または**false**)。|**true** (1)|  
|ReturnDatesAsStrings<br /><br />(PDO_SQLSRV ドライバーではサポートされていません)|日付/時刻型を文字列として返すには、1 または **true** 。<br /><br />日付/時刻型を PHP **DateTime** 型として返すには、0 または **false** 。|日付/時刻型 (datetime、date、time、datetime2、および datetimeoffset) を文字列または PHP 型として取得します。 PDO_SQLSRV ドライバーを使用する場合、日付は文字列として返されます。 PDO_SQLSRV ドライバーを持たない**datetime**型です。<br /><br />詳細については、「 [方法: SQLSRV ドライバーを利用し、日付/時刻型を取得する](../../connect/php/how-to-retrieve-date-and-time-type-as-strings-using-the-sqlsrv-driver.md)」を参照してください。|**false**|  
|Scrollable|String|「buffered」は、結果セット全体をメモリ内にキャッシュするために、クライアント側の (バッファー) カーソルが必要ですることを示します。 詳細については、次を参照してください。[カーソルの種類&#40;SQLSRV ドライバー&#41;](../../connect/php/cursor-types-sqlsrv-driver.md)です。|順方向専用カーソル|  
|[サーバー]<br /><br />(SQLSRV ドライバーではサポートされていません)|String|接続する [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] インスタンス。<br /><br />また、AlwaysOn 可用性グループへの接続に仮想ネットワーク名を指定することもできます。 詳細については[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]サポート[!INCLUDE[ssHADR](../../includes/sshadr_md.md)]を参照してください[高可用性、災害復旧をサポート](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)です。|サーバーは必須キーワードです (ただし、接続文字列の最初のキーワードである必要はありません)。 サーバー名がキーワードに渡されない場合は、ローカル インスタンスに接続する、試行が行われます。<br /><br />サーバーに渡される値には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] インスタンスの名前またはインスタンスの IP アドレスを指定できます。 必要に応じて、ポート番号を指定することができます (たとえば、 `sqlsrv:server=(local),1033`)。<br /><br />[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] のバージョン 3.0 以降では、 `server=(localdb)\instancename`で LocalDB インスタンスを指定することもできます。 詳細については、次を参照してください。 [LocalDB のサポート](../../connect/php/php-driver-for-sql-server-support-for-localdb.md)です。|  
|TraceFile|String|トレース データに使用するファイルのパスを指定します。|値は設定されません。|  
|TraceOn|トレースを有効にするには、1 または **true** 。<br /><br />トレースを無効にするには、0 または **false** 。|ODBC トレースを有効にするかどうかを指定します (1 または**true**) または無効に (0 または**false**) の確立中の接続。|**false** (0)|  
|TransactionIsolation|SQLSRV ドライバーは、次の値を使用します。<br /><br />SQLSRV_TXN_READ_UNCOMMITTED<br /><br />SQLSRV_TXN_READ_COMMITTED<br /><br />SQLSRV_TXN_REPEATABLE_READ<br /><br />SQLSRV_TXN_SNAPSHOT<br /><br />SQLSRV_TXN_SERIALIZABLE<br /><br />PDO_SQLSRV ドライバーは、次の値を使用します。<br /><br />PDO::SQLSRV_TXN_READ_UNCOMMITTED<br /><br />PDO::SQLSRV_TXN_READ_COMMITTED<br /><br />PDO::SQLSRV_TXN_REPEATABLE_READ<br /><br />PDO::SQLSRV_TXN_SNAPSHOT<br /><br />PDO::SQLSRV_TXN_SERIALIZABLE|トランザクション分離レベルを指定します。<br /><br />トランザクションの分離の詳細については、次を参照してください。 [SET TRANSACTION ISOLATION LEVEL](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md) SQL Server のドキュメントにします。|SQLSRV_TXN_READ_COMMITTED<br /><br />または<br /><br />PDO::SQLSRV_TXN_READ_COMMITTED|  
|TransparentNetworkIPResolution|**有効になっている**または**無効になっています。**|ホスト名に関連付けられている最初の解決のホスト名の IP が応答しないと、複数の ip アドレスがあるときに、接続シーケンスに影響します。<br /><br />別の接続シーケンスを提供する MultiSubnetFailover とやり取りします。 詳細については、次を参照してください。[透過的なネットワーク IP 解決を使用して](https://docs.microsoft.com/en-us/sql/connect/odbc/using-transparent-network-ip-resolution)です。|有効|
|TrustServerCertificate|証明書を信頼する場合は、1 または **true** 。<br /><br />証明書を信頼しない場合は、0 または **false** 。|クライアントが信頼する必要があるかどうかを指定します (1 または**true**) または拒否 (0 または**false**) 自己署名サーバー証明書。|**false** (0)|  
|UID<br /><br />(PDO_SQLSRV ドライバーではサポートされていません)|String|SQL Server 認証で接続するときに使用されるユーザー ID を指定<sup>4</sup>です。|値は設定されません。|  
|WSID|String|トレースするコンピューターの名前を指定します。|値は設定されません。|  

1. `ConnectionPooling`属性は、Linux およびファルダで接続プールを有効/無効にするには使用できません 参照してください[接続のプール (Microsoft Drivers for PHP for SQL Server)](../../connect/php/connection-pooling-microsoft-drivers-for-php-for-sql-server.md)です。

2. 確立された接続で実行されるすべてのクエリがで指定されているデータベースに加えられた、*データベース*属性。 ただし、ユーザーに適切なアクセス許可がある場合は、他のデータベース内のデータは完全修飾名を使用してアクセスできます。 たとえば場合、*マスター*に設定されているデータベース、*データベース*にアクセスする TRANSACT-SQL クエリを実行することも可能である接続属性、 *AdventureWorks.HumanResources.Employee*完全修飾名を使用してテーブル。  

3. *Encryption* を有効にすると、データの暗号化に必要な計算オーバーヘッドにより、いくつかのアプリケーションのパフォーマンスに影響を与える可能性があります。  

4. 接続する *UID* 認証で接続する場合は、 *PWD* 属性と [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 属性の両方を設定する必要があります。  

サポートされているキーの多くは、ODBC 接続文字列属性です。 ODBC 接続文字列については、次を参照してください。 [SQL Native Client で接続文字列キーワードを使用して](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)です。  

## <a name="see-also"></a>参照  
[サーバーへの接続](../../connect/php/connecting-to-the-server.md)  

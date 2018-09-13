---
title: Sqlcmd による接続 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- sqlcmd
ms.assetid: 61a2ec0d-1bcb-4231-bea0-cff866c21463
caps.latest.revision: 45
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 792d167461ae330689bda8dfd10806258ccd704f
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 08/14/2018
ms.locfileid: "42787876"
---
# <a name="connecting-with-sqlcmd"></a>sqlcmd による接続
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

[sqlcmd](http://go.microsoft.com/fwlink/?LinkID=154481) ユーティリティは、Linux および macOS の [!INCLUDE[msCoName](../../../includes/msconame_md.md)]ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] で使用できます。
  
次のコマンドは、Windows 認証 (Kerberos) を使用する方法を示してと[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]認証では、それぞれします。
  
```  
sqlcmd –E –Sxxx.xxx.xxx.xxx  
sqlcmd –Sxxx.xxx.xxx.xxx –Uxxx -Pxxx  
```  
  
## <a name="available-options"></a>利用可能なオプション

現在のリリースでは、次のオプションを使用できます。  
  
- -? 表示`sqlcmd`使用量。  
  
- -a パケット サイズを要求します。  
  
- -b エラーがある場合にバッチ ジョブを終了します。  
  
- -c *batch_terminator*バッチ ターミネータを指定します。  
  
- -C サーバー証明書を信頼します。  

- -d *database_name*問題、 `USE ` *database_name*ステートメントを開始するときに`sqlcmd`します。  

- -D `sqlcmd` -S オプションに渡された値が、データ ソース名 (DSN) として解釈されるようにします。 詳細については、このトピックの最後の「`sqlcmd` および `bcp` の DSN サポート」を参照してください。  
  
- -e 入力スクリプトを標準出力デバイス (stdout) に書き込みます。

- 信頼関係接続の統合認証を使用します。Linux または macOS のクライアントから統合認証を使用して、信頼関係接続を作成する方法についての詳細については、次を参照してください。 [Using Integrated Authentication](../../../connect/odbc/linux-mac/using-integrated-authentication.md)します。

- -h *number_of_rows*  列ヘッダーの間に出力する行数を指定します。  
  
- -H ワークステーション名を指定します。  
  
- -i *input_file*[,*input_file*[,…]] SQL ステートメントまたはストアド プロシージャのバッチを含むファイルを指定します。  
  
- -I セット、`SET QUOTED_IDENTIFIER`接続オプションをオンにします。  
  
- -k  制御文字を削除するか、置き換えます。  
  
- **-K * * * application_intent*  
アプリケーションがサーバーに接続するときのワークロードのタイプを宣言します。 現在サポートされている値は、 **ReadOnly**だけです。 **-K** を指定しない場合、`sqlcmd` では AlwaysOn 可用性グループのセカンダリ レプリカへの接続がサポートされません。 詳細については、次を参照してください。 [ODBC Driver on Linux と macOS の高可用性とディザスター リカバリー](../../../connect/odbc/linux-mac/odbc-driver-on-linux-support-for-high-availability-disaster-recovery.md)します。  
  
> [!NOTE]  
> **-K** は、CTP for SUSE Linux ではサポートされていません。 ただし、**に渡される DSN ファイルで**ApplicationIntent=ReadOnly`sqlcmd` キーワードを指定できます。 詳細については、このトピックの最後の「`sqlcmd` および `bcp` の DSN サポート」を参照してください。  
  
- -l *timeout* サーバーへの接続の試行時に、`sqlcmd` のログインがタイムアウトするまでの秒数を指定します。

- -m *error_level* stdout に送信されるエラー メッセージを制御します。  
  
- **-M * * * multisubnet_failover*  
[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 可用性グループまたは [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] フェールオーバー クラスター インスタンスの可用性グループ リスナーに接続する際には、必ず **-M** を指定してください。 **-M** を指定すると、フェールオーバーを迅速に検出して、(現在) アクティブなサーバーに接続できます。 **-M** を指定しない場合、 **-M** は無効になります。 詳細については[!INCLUDE[ssHADR](../../../includes/sshadr_md.md)]を参照してください[ODBC Driver on Linux と macOS の高可用性とディザスター リカバリー](../../../connect/odbc/linux-mac/odbc-driver-on-linux-support-for-high-availability-disaster-recovery.md)します。  
  
> [!NOTE]  
> **-M** は、CTP for SUSE Linux ではサポートされていません。 ただし、`sqlcmd` に渡される DSN ファイルで **MultiSubnetFailover=Yes** キーワードを指定できます。 詳細については、このトピックの最後の「`sqlcmd` および `bcp` の DSN サポート」を参照してください。  
  
- -N 接続を暗号化します。  
  
- -o *output_file* `sqlcmd` からの出力を受信するファイルを指定します。  
  
- -p  すべての結果セットのパフォーマンス統計を出力します。  
  
- -P  ユーザー パスワードを指定します。  
  
- -q *commandline_query*クエリを実行するときに`sqlcmd`が開始されるが、クエリの実行が完了したときに終了しません。  

- -Q *commandline_query*クエリを実行するときに`sqlcmd`を開始します。 クエリが終了すると `sqlcmd` は終了します。  

- -r エラー メッセージを stderr にリダイレクトします。

- -R ドライバーがクライアントの地域別設定を使用して、通貨および日時データを文字データへ変換します。 現時点では、en_US (英語 (米国)) 書式設定のみを使用します。
  
- -s *column_separator_char*列の区切り文字を指定します。  

- -S [*protocol*:] *server*[**,***port*]  
インスタンスを指定[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]に接続するかどうか、-d はまたはを使用する DSN。 Linux および macOS 上の ODBC ドライバーが必要です-%s なお**tcp**は唯一の有効なプロトコルです。  
  
- -t *query_timeout* コマンド (または SQL ステートメント) がタイムアウトになるまでの時間を秒数で指定します。  
  
- -u input_file の形式に関係なく、output_file を Unicode 形式で格納するように指定します。  
  
- -U *login_id*ユーザーのログイン ID を指定します  
  
- -V *error_severity_level* ERRORLEVEL 変数を設定するために使用される重大度レベルを制御します。  
  
- -w *column_width*出力用の画面幅を指定します。  
  
- -W 列から後続の空白を削除します。  
  
- -x 変数の代入を無効にします。  
  
- -X コマンド、スタートアップ スクリプト、および環境変数を無効にします。  
  
- -y *variable_length_type_display_width*設定、`sqlcmd`スクリプト変数`SQLCMDMAXFIXEDTYPEWIDTH`します。
  
- -Y *fixed_length_type_display_width*設定、`sqlcmd`スクリプト変数`SQLCMDMAXVARTYPEWIDTH`します。


## <a name="available-commands"></a>使用可能なコマンド

現在のリリースでは、次のコマンドを使用できます。  
  
-   [:]!!  
  
-   :Connect  
  
-   :Error  
  
-   [:]EXIT  
  
-   GO [*count*]  
  
-   :Help  
  
-   :List  
  
-   :Listvar  
  
-   :On Error  
  
-   :Out  
  
-   :Perftrace  
  
-   [:]QUIT  
  
-   :r  
  
-   :RESET  
  
-   :setvar  
  
## <a name="unavailable-options"></a>利用できないオプション
現在のリリースでは、次のオプションは使用できません。  

- -A  専用管理者接続 (DAC) を使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] にログインします。 専用管理者接続 (DAC) を作成する方法については、「[プログラミング ガイドライン](../../../connect/odbc/linux-mac/programming-guidelines.md)」を参照してください。  
  
- -f *code_page* 入力と出力のコード ページを指定します。  
  
- -L  ローカルに構成されたサーバー コンピューターと、ネットワーク上でブロードキャストしているサーバー コンピューター名の一覧を表示します。  
  
- -v  `sqlcmd` スクリプトで使用できる `sqlcmd` スクリプト変数を作成します。  
  
次の代替方法を使用することができます。 別のファイルに追加することができますし、1 つのファイル内のパラメーターに配置します。 これにより、パラメーター ファイルを使用して値を置き換えることができます。 たとえば、次のコンテンツを使用して、`a.sql` というファイル (パラメーター ファイル) を作成します。
  
    :setvar ColumnName object_id  
    :setvar TableName sys.objects  
  
次に、置換のためのパラメーターを使用して、`b.sql` というファイルを作成します。  
  
    select $(ColumnName) from $(TableName)  

、コマンドラインで組み合わせる`a.sql`と`b.sql`に`c.sql`次のコマンドを使用します。  
  
    cat a.sql > c.sql 
  
    cat b.sql >> c.sql  
  
実行`sqlcmd`して`c.sql`入力ファイルとして。  
  
    slqcmd -S<…> -P<..> –U<..> -I c.sql  

- ~ z*パスワード*パスワードを変更します。  
  
- ~ Z*パスワード*パスワードの変更と終了します。  

## <a name="unavailable-commands"></a>使用できないコマンド

現在のリリースでは、次のコマンドは利用できません。  
  
-   :ED  
  
-   :ServerList  
  
-   :XML  
  
## <a name="dsn-support-in-sqlcmd-and-bcp"></a>sqlcmd および bcp の DSN サポート

-D を指定した場合は、**sqlcmd** または **bcp** `-S` オプション (または **sqlcmd**: 接続コマンド) でサーバー名ではなくデータ ソース名 (DSN) を指定できます。 -D により**sqlcmd**または**bcp** -s オプションで、DSN に指定されたサーバーに接続します。  
  
システム Dsn に格納されている、 `odbc.ini` ODBC SysConfigDir ディレクトリ内のファイル (`/etc/odbc.ini`標準インストールで)。 ユーザー Dsn に格納されている`.odbc.ini`でユーザーのホーム ディレクトリ (`~/.odbc.ini`)。
  
Linux または macOS 上の DSN では、次のエントリがサポートされています。

-   **ApplicationIntent=ReadOnly**  

-   **Database = * * * database_name*  
  
-   **Driver for SQL Server ODBC Driver 11 を =** または**Driver for SQL Server ODBC Driver 13 を =**
  
-   **MultiSubnetFailover=Yes**  
  
-   **サーバー = * * * server_name_or_IP_address*  
  
-   **Trusted_Connection=yes**|**no**  
  
DSN では DRIVER エントリのみが必要ですが、サーバーに接続するには、`sqlcmd` または `bcp` が SERVER エントリ内の値を必要とします。  

DSN と `sqlcmd` または `bcp` コマンド ラインの両方で同じオプションが指定されている場合は、コマンドライン オプションが、DSN で使用される値をオーバーライドします。 たとえば、DSN に DATABASE エントリがあり、`sqlcmd` コマンドラインに **-d** が含まれる場合、**-d** に渡される値が使用されます。 DSN で **Trusted_Connection=yes** が指定されている場合は、Kerberos 認証が使用され、ユーザー名 (**–U**) とパスワード (**–P**) は無視されます (指定されている場合)。

エイリアス `alias isql="sqlcmd –D"` を定義して、`isql` を呼び出す既存のスクリプトを、`sqlcmd` を使用するように変更できます。  

## <a name="see-also"></a>参照  
[**bcp** による接続](../../../connect/odbc/linux-mac/connecting-with-bcp.md)  
 

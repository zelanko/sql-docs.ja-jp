---
title: Sqlcmd による接続 |Microsoft ドキュメント
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
ms.openlocfilehash: c330fd329f28fa7d89b62b9af6bb8d4bb67c2bc4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="connecting-with-sqlcmd"></a>sqlcmd による接続
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

[Sqlcmd](http://go.microsoft.com/fwlink/?LinkID=154481)ユーティリティでは、 [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Linux や macOS にします。
  
次のコマンドは、Windows 認証 (Kerberos) を使用する方法を示して、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]認証では、それぞれします。
  
```  
sqlcmd –E –Sxxx.xxx.xxx.xxx  
sqlcmd –Sxxx.xxx.xxx.xxx –Uxxx -Pxxx  
```  
  
## <a name="available-options"></a>使用可能なオプション

現在のリリースでは、次のオプションを使用できます。  
  
- -? 表示`sqlcmd`使用します。  
  
- -a、パケット サイズを要求します。  
  
- -b Terminate バッチ ジョブ エラーがある場合。  
  
- -c *batch_terminator*バッチ ターミネータを指定します。  
  
- -C サーバー証明書を信頼します。  

- -d *database_name*問題、 `USE ` *database_name*ステートメントを開始するときに`sqlcmd`です。  

- -D によりに渡された値、 `sqlcmd` -s オプションのデータ ソース名 (DSN) として解釈されます。 詳細については、次を参照してください。"での DSN サポート`sqlcmd`と`bcp`"このトピックの最後にします。  
  
- -e は、標準出力デバイス (stdout) を入力スクリプトを記述できます。

- -E は、信頼関係接続 (統合認証です。) を使用してください。Linux または macOS クライアントから統合認証を使用して信頼関係接続の作成に関する詳細については、次を参照してください。 [Using Integrated Authentication](../../../connect/odbc/linux-mac/using-integrated-authentication.md)です。

- -h *number_of_rows*列見出し間に出力する行数を指定します。  
  
- -H では、ワークステーション名を指定します。  
  
- -i *input_file*[、*input_file*[,...]ストアド プロシージャまたは SQL ステートメントのバッチを含むファイルを識別します。  
  
- -I セット、`SET QUOTED_IDENTIFIER`接続オプションをオンにします。  
  
- -k は、削除するか、制御文字を置き換えます。  
  
- **-K * * * application_intent*  
アプリケーションがサーバーに接続するときのワークロードのタイプを宣言します。 現在サポートされている値は、**ReadOnly** だけです。 場合 **-k**が指定されていない`sqlcmd`AlwaysOn 可用性グループのセカンダリ レプリカへの接続をサポートしていません。 詳細については、次を参照してください。 [ODBC Driver on Linux and macOS - 高可用性と災害復旧](../../../connect/odbc/linux-mac/odbc-driver-on-linux-support-for-high-availability-disaster-recovery.md)です。  
  
> [!NOTE]  
> **-K** は、CTP for SUSE Linux ではサポートされていません。 ただしを指定できます、 **ApplicationIntent = ReadOnly**に渡される DSN ファイルでキーワード`sqlcmd`です。 詳細については、次を参照してください。"での DSN サポート`sqlcmd`と`bcp`"このトピックの最後にします。  
  
- -l*タイムアウト*するまでの秒数を指定、`sqlcmd`サーバーに接続しようとすると、ログインがタイムアウトします。

- -m *error_level*コントロールするエラー メッセージは stdout に送信されます。  
  
- **-M * * * multisubnet_failover*  
[!INCLUDE[ssSQL11](../../../includes/sssql11_md.md)] 可用性グループまたは [!INCLUDE[ssSQL11](../../../includes/sssql11_md.md)] フェールオーバー クラスター インスタンスの可用性グループ リスナーに接続する際には、必ず **-M** を指定してください。 **-M**迅速に検出およびフェールオーバー (現在) アクティブなサーバーへの接続を提供します。 **-M** を指定しない場合、 **-M** は無効になります。 詳細については[!INCLUDE[ssHADR](../../../includes/sshadr_md.md)]を参照してください[ODBC Driver on Linux and macOS - 高可用性と災害復旧](../../../connect/odbc/linux-mac/odbc-driver-on-linux-support-for-high-availability-disaster-recovery.md)です。  
  
> [!NOTE]  
> **-M** は、CTP for SUSE Linux ではサポートされていません。 ただしを指定できます、 **MultiSubnetFailover = Yes**に渡される DSN ファイル内のキーワード`sqlcmd`です。 詳細については、次を参照してください。"での DSN サポート`sqlcmd`と`bcp`"このトピックの最後にします。  
  
- -N 接続を暗号化します。  
  
- -o *output_file*からの出力を受信するファイルを識別`sqlcmd`です。  
  
- すべての結果の-p 印刷パフォーマンス統計情報を設定します。  
  
- -P では、ユーザーのパスワードを指定します。  
  
- -q *commandline_query*クエリを実行するときに`sqlcmd`開始されるが、クエリの実行が終了したら、終了しません。  

- -Q *commandline_query*クエリを実行するときに`sqlcmd`を開始します。 `sqlcmd` クエリの終了時に終了します。  

- -r stderr にエラー メッセージをリダイレクトします。

- -R は、クライアントの地域別設定を使用して、文字データに通貨および日付と時刻のデータを変換するドライバーをさせます。 現時点では、en_US (英語 (米国)) 書式設定のみを使用します。
  
- -s *column_separator_char*列の区切り文字を指定します。  

- -S [*プロトコル*:]*サーバー*[**、* * * ポート*]  
インスタンスを指定[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]に接続するかどうか、-d はまたはを使用する DSN。 ODBC driver on Linux and macOS が -%s が必要です。 なお**tcp**唯一の有効なプロトコルです。  
  
- -t *query_timeout*コマンド (または SQL ステートメント) がタイムアウトするまでの秒数を指定します。  
  
- -u を指定してその output_file は input_file の形式に関係なく、Unicode 形式で格納されます。  
  
- -U *login_id*ユーザー ログイン ID を指定します  
  
- -V *error_severity_level* ERRORLEVEL 変数の設定に使用される重大度レベルを制御します。  
  
- -w *column_width*出力用の画面幅を指定します。  
  
- W は、列から末尾のスペースを削除します。  
  
- -x 変数の代入の無効化します。  
  
- -X コマンド、スタートアップ スクリプト、および環境変数を無効にします。  
  
- -y *variable_length_type_display_width*設定、`sqlcmd`スクリプト変数`SQLCMDMAXFIXEDTYPEWIDTH`です。
  
- -Y *fixed_length_type_display_width*設定、`sqlcmd`スクリプト変数`SQLCMDMAXVARTYPEWIDTH`です。


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
現在のリリースで、次のオプションがご利用いただけません。  

- ログイン A[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]専用管理者接続 (DAC) を使用します。 専用管理者接続 (DAC) を作成する方法については、次を参照してください。[プログラミング ガイドライン](../../../connect/odbc/linux-mac/programming-guidelines.md)です。  
  
- -f *code_page*入力と出力のコード ページを指定します。  
  
- -L は、ローカルに構成されているサーバー コンピューターおよびネットワーク上でブロードキャストしているサーバー コンピューターの名前を一覧表示します。  
  
- -v を作成する、`sqlcmd`で使用できるスクリプトの変数、`sqlcmd`スクリプト。  
  
次の代替方法を使用することができます。 別のファイルに追加することができますし、1 つのファイル内のパラメーターに配置します。 これにより、パラメーター ファイルを使用して値を置き換えることができます。 たとえば、という名前のファイルを作成`a.sql`(パラメーター ファイル)、次のコンテンツ。
  
    :setvar ColumnName object_id  
    :setvar TableName sys.objects  
  
という名前のファイルを作成し、`b.sql`交換のパラメーターを使用します。  
  
    select $(ColumnName) from $(TableName)  

コマンドラインで結合`a.sql`と`b.sql`に`c.sql`次のコマンドを使用します。  
  
    cat a.sql > c.sql 
  
    cat b.sql >> c.sql  
  
実行`sqlcmd`して`c.sql`入力ファイルとして。  
  
    slqcmd -S<…> -P<..> –U<..> -I c.sql  

- -z*パスワード*パスワードを変更します。  
  
- -Z*パスワード*パスワードの変更と終了します。  

## <a name="unavailable-commands"></a>使用できないコマンド

現在のリリースでは、次のコマンドがご利用いただけません。  
  
-   :ED  
  
-   :ServerList  
  
-   :XML  
  
## <a name="dsn-support-in-sqlcmd-and-bcp"></a>sqlcmd および bcp の DSN サポート

サーバー名の代わりにデータ ソース名 (DSN) を指定することができます、 **sqlcmd**または**bcp** `-S`オプション (または**sqlcmd** : 接続コマンド)-d を指定した場合 -D により**sqlcmd**または**bcp** -s オプションで、DSN に指定されたサーバーに接続します。  
  
システム Dsn に格納されている、 `odbc.ini` ODBC SysConfigDir ディレクトリ内のファイル (`/etc/odbc.ini`標準インストールで)。 ユーザー Dsn に格納されている`.odbc.ini`でユーザーのホーム ディレクトリ (`~/.odbc.ini`)。
  
次のエントリは、Linux または macOS DSN でサポートされます。

-   **ApplicationIntent = ReadOnly**  

-   **データベース = * * * database_name*  
  
-   **Driver for SQL Server ODBC Driver 11 を =** または**Driver for SQL Server ODBC Driver 13 を =**
  
-   **MultiSubnetFailover = Yes**  
  
-   **サーバー = * * * server_name_or_IP_address*  
  
-   **Trusted_Connection=yes**|**no**  
  
Dsn では DRIVER エントリのみが必要ですが、サーバーに接続する`sqlcmd`または`bcp`サーバー エントリに値が必要です。  

DSN の両方で同じオプションが指定されている場合、`sqlcmd`または`bcp`コマンド ライン コマンド ライン オプションは、DSN で使用される値をオーバーライドします。 例では、DSN に DATABASE エントリと`sqlcmd`コマンドラインが含まれています **-d**に渡された値 **-d**を使用します。 場合**Trusted_Connection = [はい]** DSN、Kerberos 認証を使用し、ユーザー名で指定された (**– U**) とパスワード (**– P**)、指定した場合は無視されます。

呼び出す既存のスクリプト`isql`を使用するように変更する`sqlcmd`は次の別名を定義することによって:`alias isql="sqlcmd –D"`です。  

## <a name="see-also"></a>参照  
[使用した接続**bcp**](../../../connect/odbc/linux-mac/connecting-with-bcp.md)  
 

---
title: sqlcmd ユーティリティ | Microsoft Docs
ms.custom: ''
ms.date: 11/29/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- statements [SQL Server], command prompt
- QUIT command
- Transact-SQL statements, command prompt
- EXIT command
- sqlcmd commands
- ED command
- sqlcmd utility
- command prompt utilities [SQL Server], sqlcmd
- '!! command'
- stored procedures [SQL Server], command prompt
- system stored procedures [SQL Server], command prompt
- sqlcmd utility, about sqlcmd utility
- scripts [SQL Server], command prompt
- RESET command
- GO command
ms.assetid: e1728707-5215-4c04-8320-e36f161b834a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d128085012c0ef3a9bc58b147f982a26d2c094b8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63035388"
---
# <a name="sqlcmd-utility"></a>sqlcmd ユーティリティ
  ユーティリティを使用すると[!INCLUDE[tsql](../includes/tsql-md.md)] 、ステートメント、システムプロシージャ、およびスクリプトファイルを、コマンドプロンプト、SQLCMD モードの**クエリエディター** 、Windows スクリプトファイル、または[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]エージェントジョブのオペレーティングシステム (cmd.exe) ジョブステップで入力できます。 `sqlcmd` このユーティリティでは、ODBC を使用して [!INCLUDE[tsql](../includes/tsql-md.md)] バッチを実行します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]は、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]**クエリエディター**の標準モードと SQLCMD モードでの実行に SqlClient を使用します。 コマンド ラインから `sqlcmd` を実行する場合、`sqlcmd` では ODBC ドライバーが使用されます。 同じクエリでも、[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] の SQLCMD モードで実行する場合と `sqlcmd` ユーティリティで実行する場合とでは、適用される既定のオプションが異なるので、動作も異なる可能性があります。  
  
 現在、`sqlcmd` ではコマンド ライン オプションと値の間に空白を入れる必要はありません。 ただし、将来のリリースでは、コマンド ライン オプションと値の間に空白が必要になる可能性があります。  
  
## <a name="syntax"></a>構文  
  
```  
  
   sqlcmd  
   -a  
   packet_size  
   -A (dedicated administrator connection)  
-b (terminate batch job if there is an error)  
-cbatch_terminator-C (trust the server certificate)  
-ddb_name-e (echo input)  
-E (use trusted connection)  
-fcodepage | i:codepage[,o:codepage] | o:codepage[,i:codepage]  
-hrows_per_header-Hworkstation_name-iinput_file-I (enable quoted identifiers)  
-k[1 | 2] (remove or replace control characters)  
-Kapplication_intent-llogin_timeout-L[c] (list servers, optional clean output)  
-merror_level-Mmultisubnet_failover-N (encrypt connection)  
-ooutput_file-p[1] (print statistics, optional colon format)  
-Ppassword-q "cmdline query"-Q "cmdline query" (and exit)  
-r[0 | 1] (msgs to stderr)  
-R (use client regional settings)  
-scol_separator-S [protocol:]server[\instance_name][,port]  
-tquery_timeout-u (unicode output file)  
-Ulogin_id-vvar = "value"-Verror_severity_level-wcolumn_width-W (remove trailing spaces)  
-x (disable variable substitution)  
-X[1] (disable commands, startup script, environment variables and optional exit)  
-yvariable_length_type_display_width-Yfixed_length_type_display_width-znew_password -Znew_password (and exit)  
  
-? (usage)  
```  
  
## <a name="command-line-options"></a>コマンド ライン オプション  
 **ログイン関連のオプション**  
  **-A**  
 専用管理者接続 (DAC) を使用して [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] にログインします。 この種類の接続は、サーバーのトラブルシューティングで使用されます。 またこの接続は、DAC をサポートしているサーバー コンピューターでのみ機能します。 DAC が使用できない場合は、`sqlcmd` はエラー メッセージを生成して終了します。 DAC の詳細については、「 [データベース管理者用の診断接続](../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md)」を参照してください。  
  
 **-C**  
 クライアントでこのスイッチを使用して、サーバーの証明書を検証せずに暗黙的に信頼するようにクライアントを構成できます。 このオプションは、ADO.NET オプションの `TRUSTSERVERCERTIFICATE = true`と同等です。  
  
 **-d** _db_name_  
 を開始`USE` ** `sqlcmd`するときに db_name ステートメントを発行します。 このオプションにより、`sqlcmd` スクリプト変数 SQLCMDDBNAME が設定されます。 これにより初期データベースが指定されます。 既定値は、ログインの既定データベースのプロパティです。 データベースが存在しない場合は、エラー メッセージが生成され、`sqlcmd` は終了します。  
  
 **-l** _login_timeout_  
 サーバーに接続を試みたときに、`sqlcmd` が ODBC ドライバーにログインするまでのタイムアウトを秒数で指定します。 このオプションにより、`sqlcmd` スクリプト変数 SQLCMDLOGINTIMEOUT が設定されます。 
  `sqlcmd` でのログインに関する既定のタイムアウトは 8 秒です。 ログイン タイムアウトは、0 ～ 65,534 の数値にする必要があります。 指定した値が数値以外の場合、または範囲外の場合、`sqlcmd` はエラー メッセージを生成します。 この値に 0 を指定すると、タイムアウトは無制限になります。  
  
 **-E**  
 ユーザー名とパスワードを使用せずにセキュリティ接続を使用して [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] にログオンします。 既定では、-E を指定しないと、`sqlcmd` ではセキュリティ接続オプションが使用されます。  
  
 
  **-E** オプションを使用すると、SQLCMDPASSWORD などのユーザー名とパスワード用に使用できる環境変数の設定が無視されます。 
  **-E** オプションが **-U** オプションまたは **-P** オプションと共に使用されると、エラー メッセージが生成されます。  
  
 **-H** _workstation_name_  
 ワークステーション名です。 このオプションにより、`sqlcmd` スクリプト変数 SQLCMDWORKSTATION が設定されます。 ワークステーション名は **sys.processes** カタログ ビューの **hostname** 列に一覧表示され、ストアド プロシージャ **sp_who** を使用して取得できます。 このオプションが指定されていない場合の既定値は、現在のコンピューター名になります。 この名前は、異なる `sqlcmd` セッションを識別する場合に使用できます。  
  
 **-K** _application_intent_  
 アプリケーションがサーバーに接続するときのワークロードのタイプを宣言します。 現在サポートされている値は、 **ReadOnly**だけです。 
  **-K** を指定しない場合、sqlcmd ユーティリティでは AlwaysOn 可用性グループのセカンダリ レプリカへの接続がサポートされません。 詳細については、「[アクティブなセカンダリ: 読み取り可能なセカンダリレプリカ](../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)」を参照してください。  
  
 `-M`*multisubnet_failover*  
 
  `-M` 可用性グループまたは [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] フェールオーバー クラスター インスタンスの可用性グループ リスナーに接続する際には、必ず [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] を指定してください。 
  `-M` を指定すると、(現在) アクティブなサーバーを迅速に検出して接続できます。 
  `-M` が指定されていない場合、`-M` は無効になります。 の詳細につい[!INCLUDE[ssHADR](../includes/sshadr-md.md)]ては、「[可用性グループリスナー、クライアント接続、およびアプリケーションのフェールオーバー &#40;SQL Server&#41;](../database-engine/listeners-client-connectivity-application-failover.md)、[可用性グループの作成と構成 &#40;SQL Server ](../database-engine/availability-groups/windows/creation-and-configuration-of-availability-groups-sql-server.md)&#41;、[フェールオーバークラスタリングと AlwaysOn 可用性グループ](../database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md)&#40;SQL Server&#41;、および[アクティブなセカンダリ: 読み取り可能なセカンダリレプリカ](../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)」を参照してください。  
  
 **-N**  
 クライアントでこのスイッチを使用して、暗号化された接続を要求できます。  
  
 **-P** _パスワード_  
 ユーザーが指定するパスワードです。 パスワードでは大文字と小文字が区別されます。 -U オプションを使用して **-P**オプションを使用せず、sqlcmdpassword 環境変数が設定されていない場合`sqlcmd` 、はユーザーにパスワードの入力を求めます。 **-P**オプションをコマンドプロンプトの最後に使用する場合は、パスワード`sqlcmd`を使用しないで既定のパスワード (NULL) が使用されます。  
  
> [!IMPORTANT]  
>  空白のパスワードは使用しないでください。 強力なパスワードを使用してください。 詳細については、「 [強力なパスワード](../relational-databases/security/strong-passwords.md)」を参照してください。  
  
 パスワード プロンプトは、次のようにパスワード プロンプトをコンソールに出力することによって表示されます。 `Password:`  
  
 ユーザーが行った入力は表示されません。 つまり、入力時には何も表示されず、カーソルが移動しません。  
  
 SQLCMDPASSWORD 環境変数を使用して、現在のセッションに既定のパスワードを設定できます。 したがって、パスワードをバッチ ファイルにハード コードする必要はありません。  
  
 次の例では、まずコマンド プロンプトで SQLCMDPASSWORD 変数を設定してから `sqlcmd` ユーティリティにアクセスします。 コマンド プロンプトで、次のように入力します。  
  
 `SET SQLCMDPASSWORD= p@a$$w0rd`  
  
> [!IMPORTANT]  
>  このとき、コンピューターのモニターにはパスワードが表示されてしまうので、注意してください。  
  
 次のコマンド プロンプトが表示されたら、次のように入力します:  
  
 `sqlcmd`  
  
 ユーザー名とパスワードの組み合わせが正しくない場合は、エラー メッセージが生成されます。  
  
> [!NOTE]  
>  OSQLPASSWORD 環境変数は旧バージョンとの互換性を維持しています。 SQLCMDPASSWORD 環境変数は OSQLPASSWORD 環境変数よりも優先されます。つまり`sqlcmd` 、と**osql**を相互に干渉することなく使用でき、古いスクリプトは引き続き機能します。  
  
 
  **-P** オプションが **-E** オプションと共に使用されると、エラー メッセージが生成されます。  
  
 
  **-P** オプションの後に複数の引数があると、エラー メッセージが生成され、プログラムが終了します。  
  
 **-S** [*protocol*:]*サーバー*[**\\**_instance_name_] [**,**_port_]  
 接続先となる [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスを指定します。 このオプションにより、`sqlcmd` スクリプト変数 SQLCMDSERVER が設定されます。  
  
 そのサーバー コンピューター上の * の既定のインスタンスに接続するには、* server_name[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] を指定します。 サーバー ** コンピューター上**\\** __ のの[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]名前付きインスタンスに接続するには server_name [instance_name] を指定します。 サーバー コンピューターを指定しない場合、`sqlcmd` は、ローカル コンピューター上にある [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の既定のインスタンスに接続します。 このオプションは、ネットワーク上の`sqlcmd`リモートコンピューターからを実行する場合に必要です。  
  
 *プロトコル*には`tcp` 、(tcp/ip)、 `lpc` (共有メモリ)、または`np` (名前付きパイプ) を指定できます。  
  
 を`sqlcmd`開始するときに*server_name* [ **\\** _instance_name_ ] を指定しない場合[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 、は sqlcmdserver 環境変数を確認して使用します。  
  
> [!NOTE]  
>  OSQLSERVER 環境変数は旧バージョンとの互換性を維持しています。 SQLCMDSERVER 環境変数は、OSQLSERVER 環境変数よりも優先されます。つまり`sqlcmd` 、と**osql**を相互に干渉することなく使用でき、古いスクリプトは引き続き機能します。  
  
 **-U** _login_id_  
 ユーザーのログイン ID です。  
  
> [!NOTE]  
>  OSQLUSER 環境変数は旧バージョンとの互換性を維持しています。 SQLCMDUSER 環境変数は OSQLUSER 環境変数よりも優先されます。 これは`sqlcmd` 、と**osql**を相互に干渉せずに使用できることを意味します。 また、既存の **osql** スクリプトは引き続き実行することができます。  
  
 **-U**オプションも **-P**オプションも指定しない場合、 `sqlcmd`は Windows 認証モードを使用[!INCLUDE[msCoName](../includes/msconame-md.md)]して接続を試みます。 認証は `sqlcmd` を実行しているユーザーの Windows アカウントに基づきます。  
  
 
  **-U** オプションが **-E** オプション (このトピックの後半で説明) と同時に使用されると、エラー メッセージが生成されます。 
  **-U** オプションの後に複数の引数があると、エラー メッセージが生成され、プログラムが終了します。  
  
 **-z** _new_password_  
 パスワードの変更:  
  
 `sqlcmd -U someuser -P s0mep@ssword -z a_new_p@a$$w0rd`  
  
 **-Z** _new_password_  
 パスワードの変更と終了:  
  
 `sqlcmd -U someuser -P s0mep@ssword -Z a_new_p@a$$w0rd`  
  
 **入力/出力オプション**  
  **-f** _コードページ_ | **i:**_コードページ_[**, o:**_codepage_] |**o:**_codepage_[**, i:**_codepage_]  
 入力と出力のコード ページを指定します。 コード ページ番号は、インストールされた Windows コード ページを指定する数値です。  
  
 コード ページには次の変換規則があります。  
  
-   コード ページを指定しないと、入力ファイルが変換不要の Unicode ファイルでない限り、`sqlcmd` では、入力ファイルと出力ファイルの両方に現在のコード ページが使用されます。  
  
-   
  `sqlcmd` では、ビッグ エンディアンとリトル エンディアンの両方の Unicode 入力ファイルが自動的に認識されます。 
  **-u** オプションを指定すると、出力は常にリトル エンディアン Unicode になります。  
  
-   出力ファイルを指定しないと、出力コード ページはコンソールのコード ページになります。 その結果、コンソールに出力が正しく表示されます。  
  
-   複数の入力ファイルの場合、同じコード ページが指定されているものと見なされます。 Unicode 入力ファイルと Unicode 以外の入力ファイルを混在させることができます。  
  
 Cmd.exe のコード ページを確認するには、コマンド プロンプトに「`chcp`」と入力します。  
  
 **-i** _input_file_[**、**_input_file2_...]  
 SQL ステートメントまたはストアド プロシージャのバッチを含むファイルを指定します。 複数のファイルを指定すると、それらのファイルは順番に読み取られて処理されます。 ファイル名とファイル名の間には空白を使用しないでください。 
  `sqlcmd` により、最初に、指定したすべてのファイルが存在しているかどうかがチェックされます。 1 つ以上のファイルが存在していない場合は、`sqlcmd` は終了します。 -i と -Q/-q オプションは同時に使用できません。  
  
 パスの例:  
  
 **-i**C:\\<ファイル名\>  
  
 **-i** \\ \\<Server\> \\<共有 $>\\<ファイル名\>  
  
 **-i**"C:\ フォルダー\\<ファイル名\>"  
  
 空白を含むファイル パスは、引用符で囲む必要があります。  
  
 このオプションは **、-i**_input_file_ **-** i_input_file_のように複数回使用できます。  
  
 **-o** _output_file_  
 
  `sqlcmd` からの出力を受信するファイルを指定します。  
  
 
  **-u** が指定されている場合は、 *output_file* は Unicode 形式で格納されます。 ファイル名が無効な場合は、エラー メッセージが生成され、`sqlcmd` が終了します。 
  `sqlcmd` は、同じファイルに対する複数の `sqlcmd` プロセスの同時書き込みはサポートしていません。 出力ファイルが破損するか、または不適切なファイルになる可能性があります。 ファイル形式の詳細については、 **-f** スイッチを参照してください。 このファイルが存在しない場合は作成されます。 以前の `sqlcmd` セッションで同じ名前のファイルが作成されていた場合は、上書きされます。 ここで指定されるファイルは **stdout** ファイルではありません。 **Stdout**ファイルが指定されている場合、このファイルは使用されません。  
  
 パスの例:  
  
 **-o**C:\\< ファイル名>  
  
 **-o** \\ \\<Server\> \\<$>\\<ファイル名を共有します\>  
  
 **-o "** C:\ フォルダー\\<ファイル名\>を指定する (c)  
  
 空白を含むファイル パスは、引用符で囲む必要があります。  
  
 **-r**[**0** | **1**]  
 エラー メッセージ出力を画面にリダイレクトします (**stderr**)。 パラメーターを指定しない場合や、 **0**を指定した場合は、重大度レベル 11 以上のエラー メッセージだけがリダイレクトされます。 
  **1**を指定した場合は、PRINT を含むすべてのエラー メッセージ出力がリダイレクトされます。 -o を使用しても効果はありません。 既定では、メッセージは **stdout**に送られます。  
  
 **-R**  
 で`sqlcmd`は、クライアントのロケールに基づいてから[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]取得された数値、通貨、日付、および時刻の各列がによってローカライズされます。 既定では、これらの列はサーバーの地域別設定を使用して表示されます。  
  
 **-u**  
 
  *input_file* の形式に関係なく、 *output_file*を Unicode 形式で格納するように指定します。  
  
 **クエリ実行オプション**  
  **-e**  
 入力スクリプトを標準出力デバイス (**stdout**) に書き込みます。  
  
 **-I**  
 SET QUOTED_IDENTIFIER 接続オプションを ON に設定します。 既定では、OFF に設定されています。 詳細については、「 [SET QUOTED_IDENTIFIER &#40;transact-sql&#41;](/sql/t-sql/statements/set-quoted-identifier-transact-sql)」を参照してください。  
  
 **-q "** _cmdline query_ **"**  
 
  `sqlcmd` の起動時にクエリを実行しますが、クエリの実行が完了しても `sqlcmd` を終了しません。 セミコロンで区切られた複数のクエリを実行できます。 次の例で示すように、クエリを引用符で囲みます。  
  
 コマンド プロンプトで、次のように入力します。  
  
 `sqlcmd -d AdventureWorks2012 -q "SELECT FirstName, LastName FROM Person.Person WHERE LastName LIKE 'Whi%';"`  
  
 `sqlcmd -d AdventureWorks2012 -q "SELECT TOP 5 FirstName FROM Person.Person;SELECT TOP 5 LastName FROM Person.Person;"`  
  
> [!IMPORTANT]  
>  クエリでは GO ターミネータを使用しないでください。  
  
 このオプションと共に `-b` を指定すると、`sqlcmd` はエラーで終了します。 
  `-b` オプションについては、このトピックの後半で説明します。  
  
 **-Q "** _cmdline query_ **"**  
 
  `sqlcmd` の起動時にクエリを実行し、`sqlcmd` を即時終了します。 セミコロンで区切られた複数のクエリを実行できます。  
  
 次の例で示すように、クエリを引用符で囲みます。  
  
 コマンド プロンプトで、次のように入力します。  
  
 `sqlcmd -d AdventureWorks2012 -Q "SELECT FirstName, LastName FROM Person.Person WHERE LastName LIKE 'Whi%';"`  
  
 `sqlcmd -d AdventureWorks2012 -Q "SELECT TOP 5 FirstName FROM Person.Person;SELECT TOP 5 LastName FROM Person.Person;"`  
  
> [!IMPORTANT]  
>  クエリでは GO ターミネータを使用しないでください。  
  
 このオプションと共に `-b` を指定すると、`sqlcmd` はエラーで終了します。 
  `-b` オプションについては、このトピックの後半で説明します。  
  
 **-t** _query_timeout_  
 コマンド (または SQL ステートメント) がタイムアウトするまでの秒数を指定します。このオプションにより`sqlcmd` 、スクリプト変数 SQLCMDSTATTIMEOUT が設定されます。 *Time_out*値が指定されていない場合、コマンドはタイムアウトしません。*クエリ * * time_out*には、1から65534までの数値を指定する必要があります。 指定した値が数値以外の場合、または範囲外の場合、`sqlcmd` はエラー メッセージを生成します。  
  
> [!NOTE]  
>  実際のタイムアウト値は、指定した *time_out* 値より数秒異なる場合があります。  
  
 **-vvar =** _値_[ **var =** _値_...]  
 スクリプトで`sqlcmd`使用できるスクリプト変数を作成します。 `sqlcmd` 値に空白が含まれる場合は、値を引用符で囲みます。 複数の**_var_**=**"*`values`*"** 値を指定できます。 指定した値にエラーが生じた場合は、`sqlcmd` は、エラー メッセージを生成してから終了します。  
  
 `sqlcmd -v MyVar1=something MyVar2="some thing"`  
  
 `sqlcmd -v MyVar1=something -v MyVar2="some thing"`  
  
 **-x**  
 
  `sqlcmd` ではスクリプト変数が無視されます。 これは、$(*variable_name*) などの標準変数と同じ形式の文字列を含む INSERT ステートメントが、スクリプトに多数含まれている場合に便利です。  
  
 **書式設定のオプション**  
  **-h** _ヘッダー_  
 列ヘッダーの間に出力する行数を指定します。 既定では、各クエリの結果に対して、ヘッダーは 1 つだけ表示されます。 このオプションにより、`sqlcmd` スクリプト変数 SQLCMDHEADERS が設定されます。 ヘッダーを出力しない場合は、 **-1** を指定します。 有効でない値があると、`sqlcmd` はエラー メッセージを生成してから終了します。  
  
 **-k** [**1** | **2**]  
 タブ、改行文字などのすべての制御文字を出力から削除します。 これにより、データが返されたときの列の形式が維持されます。 1 を指定した場合、制御文字は 1 つの空白に置き換えられます。 2 を指定すると、連続する制御文字が 1 つの空白に置き換えられます。 **-k**は **-k1**と同じです。  
  
 **-s** _col_separator_  
 列の区切り文字を指定します。 既定では、空白になっています。 このオプションにより、`sqlcmd` スクリプト変数 SQLCMDCOLSEP が設定されます。 アンパサンド (&)、セミコロン (;) など、オペレーティング システムで特別な意味を持つ文字を使用する場合は、その文字を引用符 (") で囲みます。 列の区切り文字には、任意の 8 ビットの文字を指定できます。  
  
 **-w** _column_width_  
 出力用の画面幅を指定します。 このオプションにより、`sqlcmd` スクリプト変数 SQLCMDCOLWIDTH が設定されます。 列幅は 8 よりも大きくかつ 65,536 よりも小さい値にする必要があります。 指定した列幅が範囲外の場合、`sqlcmd` はエラー メッセージを生成します。 既定の幅は 80 文字です。 指定した列幅を超えると、出力行は次の列に折り返されます。  
  
 **-W**  
 このオプションは、列から後続の空白を削除します。 他のアプリケーションにエクスポートするデータを準備するときは、 **-s** オプションと同時にこのオプションを使用します。 
  **-y** または **-Y** オプションと共には使用できません。  
  
 **-y** _variable_length_type_display_width_  
 
  `sqlcmd` スクリプト変数 SQLCMDMAXVARTYPEWIDTH が設定されます。 既定値は 256 です。 長い可変長のデータ型に返される文字数を制限します。  
  
-   `varchar(max)`  
  
-   `nvarchar(max)`  
  
-   `varbinary(max)`  
  
-   `xml`  
  
-   `UDT (user-defined data types)`  
  
-   `text`  
  
-   `ntext`  
  
-   `image`  
  
> [!NOTE]  
>  UDT は実装によって固定長にもなります。 固定長の UDT の長さが *display_width*よりも短い場合は、返される UDT の値は影響を受けません。 ただし、 *display_width*よりも長い場合は、出力は切り捨てられます。  
  
 
> [!IMPORTANT]  
>  返されるデータのサイズによって、サーバーとネットワークの両方に重大なパフォーマンスの問題が発生する可能性があるため、 **-y 0** オプションは十分注意して使用してください。  
  
 **-Y** _fixed_length_type_display_width_  
 
  `sqlcmd` スクリプト変数 SQLCMDMAXFIXEDTYPEWIDTH が設定されます。 既定値は 0 (無制限) です。 次のデータ型に返される文字数を制限します。  
  
-   `char(`*n* `)`。ここで、1<= n<= 8000  
  
-   `nchar(n`*n* `)`。ここで、1<= n<= 4000  
  
-   `varchar(n`*n* `)`。ここで、1<= n<= 8000  
  
-   `nvarchar(n`*n* `)`。ここで、1<= n<= 4000  
  
-   `varbinary(n`*n* `)`。ここで、1<= n<= 4000  
  
-   `variant`  
  
 **エラー報告のオプション**  
  `-b`  
 エラーが発生したときに、`sqlcmd` を終了し、DOS ERRORLEVEL 値を返します。 
  ** のエラー メッセージの重大度が 10 よりも高い場合、DOS ERRORLEVEL 変数に返される値は **1[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] です。それ以外の場合は、**0** が返されます。 
  `-V` オプションが `-b` と共に設定されている場合、`sqlcmd` を使用して設定した値よりも重大度が低いときは、`-V` はエラーを報告しません。 コマンド プロンプト バッチ ファイルにより ERRORLEVEL の値をテストすることができ、エラーを適切に処理できます。 
  `sqlcmd` は重大度レベル 10 (情報メッセージ) に対してはエラーを報告しません。  
  
 
  `sqlcmd` スクリプトに正しくないコメントや構文エラーが含まれている場合やスクリプト変数が不足している場合、返される ERRORLEVEL は 1 です。  
  
 **-m** _error_level_  
 
  **stdout**に送信されるエラー メッセージを制御します。 重大度レベルがこのレベル以上のメッセージが送信されます。 この値を **-1**に設定すると、情報メッセージを含めすべてのメッセージが送信されます。 
  **-m** と **-1**の間にスペースは使用できません。 たとえば、 **-m-1** は有効で、 **-m-1** は有効でありません。  
  
 このオプションにより、`sqlcmd` スクリプト変数 SQLCMDERRORLEVEL も設定されます。 この変数の既定値は 0 です。  
  
 `-V`*error_severity_level*  
 ERRORLEVEL 変数を設定するために使用される重大度レベルを制御します。 重大度レベルがこの値以上のエラー メッセージによって、ERRORLEVEL が設定されます。 0 より小さい値は 0 と報告されます。 バッチ ファイルおよび CMD ファイルを使用して、ERRORLEVEL 変数の値をテストできます。  
  
 **その他のオプション**  
  **-a** _packet_size_  
 異なるサイズのパケットを要求します。 このオプションにより、`sqlcmd` スクリプト変数 SQLCMDPACKETSIZE が設定されます。 *packet_size*には、512 ~ 32767 の値を指定する必要があります。 既定値は 4096 です。 大きなパケット サイズを指定すると、GO コマンド間に多数の SQL ステートメントが含まれているスクリプトの実行パフォーマンスが向上します。 既定値よりも大きいパケット サイズを要求できます。 ただし、要求が拒否された場合、`sqlcmd` はサーバーの既定のパケット サイズを使用します。  
  
 **-c** _batch_terminator_  
 バッチ ターミネータを指定します。 既定では、"GO" だけが入力されている行があると、コマンドが終了したと見なされ、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] に送られます。 バッチ ターミネータをリセットする場合、[!INCLUDE[tsql](../includes/tsql-md.md)] の予約キーワードやオペレーティング システムで特別な意味を持つ文字は、先頭に円記号が付いているかどうかに関係なく、使用しないでください。  
  
 **-L**[**c**]  
 ローカルに構成されたサーバー コンピューターと、ネットワーク上でブロードキャストしているサーバー コンピューター名の一覧を表示します。 このパラメーターは、他のパラメーターと組み合わせて使用することはできません。 一覧表示できるサーバー コンピューターの最大数は 3,000 です。 バッファーのサイズが原因でサーバーの一覧が切り捨てられる場合は、警告メッセージが表示されます。  
  
> [!NOTE]  
>  ネットワーク上のブロードキャストの性質により、 `sqlcmd`は、すべてのサーバーからタイムリーな応答を受信できない場合があります。 そのため、返されるサーバーのリストは、このオプションの実行ごとに異なる可能性があります。  
  
 省略可能なパラメーター **c**が指定されている場合、出力は Servers: ヘッダー行なしで表示され、各サーバー行は先頭にスペースなしで一覧表示されます。 これは、クリーン アウトプットとも呼ばれます。 クリーン アウトプットを使用すると、スクリプト言語の処理パフォーマンスが向上します。  
  
 **-p**[**1**]  
 すべての結果セットのパフォーマンス統計を出力します。 次は、パフォーマンス統計の形式の例です。  
  
 `Network packet size (bytes): n`  
  
 `x xact[s]:`  
  
 `Clock Time (ms.): total       t1  avg       t2 (t3 xacts per sec.)`  
  
 各値の説明:  
  
 
  `x` = [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] によって処理されるトランザクション数。  
  
 
  `t1` = すべてのトランザクションにかかる合計時間、  
  
 
  `t2` = 単一のトランザクションにかかる平均時間。  
  
 
  `t3` = 1 秒あたりの平均トランザクション数。  
  
 すべての時間はミリ秒単位です。  
  
 省略可能なパラメーター **1** を指定した場合は、統計の出力形式は、スプレッドシートへ容易にインポートできる、またはスクリプトによって処理できる、コロンで区切られた形式となります。  
  
 省略可能なパラメーターが**1**以外の値の場合は、エラーが生成`sqlcmd`され、終了します。  
  
 `-X`[**1**]  
 
  `sqlcmd` がバッチ ファイルから実行される場合に、システムのセキュリティを損なう可能性のあるコマンドを無効にします。 無効なコマンドも認識されます。`sqlcmd` は警告メッセージを表示して継続します。 省略可能なパラメーター **1**を指定し`sqlcmd`た場合、はエラーメッセージを生成して終了します。 
  `-X` オプションを使用した場合に無効になるコマンドは次のとおりです。  
  
-   **プロンプト**  
  
-   **!!** _メニュー_  
  
 
  `-X` オプションを指定すると、環境変数が `sqlcmd` に渡されなくなります。 また、SQLCMDINI スクリプト変数を使用して指定した、スタートアップ スクリプトも実行できなくなります。 変数の`sqlcmd`スクリプト作成の詳細については、「 [Sqlcmd をスクリプト変数と共に使用する](../relational-databases/scripting/sqlcmd-use-with-scripting-variables.md)」を参照してください。  
  
 **-?**  
 
  `sqlcmd` オプションの構文の概要を表示します。  
  
## <a name="remarks"></a>解説  
 オプションは、構文の例に示されている順序に従って使用する必要はありません。  
  
 複数の結果が返される場合は、`sqlcmd` は同じバッチの各結果セットの間に空白行を 1 行ずつ出力します。 さらに、実行さ\<れたステートメントに適用されない "x> 行が影響を受けました" というメッセージは表示されません。  
  
 対話的に`sqlcmd`使用するに`sqlcmd`は、このトピックで前述した1つ以上のオプションを使用して、コマンドプロンプトで「」と入力します。 詳細については、「 [Sqlcmd ユーティリティの使用](../relational-databases/scripting/sqlcmd-use-the-utility.md)」を参照してください。  
  
> [!NOTE]  
>  **-L**、 **-Q**、 **-Z** 、または **-i**の`sqlcmd`オプションを実行すると、が終了します。  
  
 コマンド環境 (Cmd.exe) での `sqlcmd` コマンド ライン全体の長さは、すべての引数と拡張変数を含めて、オペレーティング システムの Cmd.exe によって決まります。  
  
## <a name="variable-precedence-low-to-high"></a>変数の優先順位 (低から高)  
  
1.  システム レベル環境変数  
  
2.  ユーザー レベル環境変数  
  
3.  コマンドシェル (**set** X = Y) は、実行`sqlcmd`前にコマンドプロンプトで設定します。  
  
4.  **sqlcmd-v**X = Y  
  
5.  **: Setvar**X Y  
  
> [!NOTE]  
>  環境変数を表示するには、 **[コントロール パネル]** の **[システム]** アイコンを開き、 **[詳細設定]** タブをクリックします。  
  
## <a name="sqlcmd-scripting-variables"></a>sqlcmd スクリプト変数  
  
|変数|関連スイッチ|R/W|Default|  
|--------------|--------------------|----------|-------------|  
|SQLCMDUSER|-U|R|""|  
|SQLCMDPASSWORD|-P|--|""|  
|SQLCMDSERVER|-S|R|"DefaultLocalInstance"|  
|SQLCMDWORKSTATION|-H|R|"ComputerName"|  
|SQLCMDDBNAME|-d|R|""|  
|SQLCMDLOGINTIMEOUT|-l|R/W|"8" (秒)|  
|SQLCMDSTATTIMEOUT|-t|R/W|"0" = 無制限に待機|  
|SQLCMDHEADERS|-h|R/W|"0"|  
|SQLCMDCOLSEP|-s|R/W|" "|  
|SQLCMDCOLWIDTH|-w|R/W|"0"|  
|SQLCMDPACKETSIZE|-a|R|"4096"|  
|SQLCMDERRORLEVEL|-M|R/W|0|  
|SQLCMDMAXVARTYPEWIDTH|-y|R/W|"256"|  
|SQLCMDMAXFIXEDTYPEWIDTH|-y|R/W|"0" = 無制限|  
|SQLCMDEDITOR||R/W|"edit.com"|  
|SQLCMDINI||R|""|  
  
 SQLCMDUSER、SQLCMDPASSWORD、および SQLCMDSERVER は、**:Connect**  
  
  が使用されているときに設定されます。  
  
 R は、その値がプログラムの初期化時に一度だけ設定できることを示します。  
  
 R/W は、 **setvar** コマンドを使用して値を変更できること、および後続のコマンドに新しい値が反映されることを示します。  
  
## <a name="sqlcmd-commands"></a>sqlcmd コマンド  
 内`sqlcmd`のステートメント[!INCLUDE[tsql](../includes/tsql-md.md)]に加えて、次のコマンドも使用できます。  
  
|||  
|-|-|  
|**[** *カウント*]|**: リスト**|  
|[**:**] **RESET**|**: エラー**|  
|[**:**] **ED**|**: 出力**|  
|[**:**] **!!**|**:P erftrace**|  
|[**:**] **QUIT**|**: 接続**|  
|[**:**] **EXIT**|**: エラー発生時**|  
|**: r**|**: ヘルプ**|  
|**: ServerList**|**: XML** [**ON** &#124; **OFF**]|  
|**: Setvar**|**: Listvar**|  
  
 
  `sqlcmd` コマンドを使用するときは、次の点に注意してください。  
  
-   GO を除くすべての `sqlcmd` コマンドは、コロン (:) によってプレフィックス指定する必要があります。  
  
    > [!IMPORTANT]  
    >  既存の **osql** スクリプトとの互換性を保つために、一部のコマンドはコロンなしで認識されます。 これは、[**:**] によって示されています。  
  
-   
  `sqlcmd` コマンドが認識されるのは、コマンドが行の先頭にある場合のみです。  
  
-   すべての `sqlcmd` コマンドには、大文字と小文字の区別はありません。  
  
-   各コマンドは個別の行に指定する必要があります。 コマンドの後には、[!INCLUDE[tsql](../includes/tsql-md.md)] ステートメントまたは別のコマンドを指定できません。  
  
-   コマンドは即座に実行されます。 
  [!INCLUDE[tsql](../includes/tsql-md.md)] ステートメントのように、実行バッファーに配置されません。  
  
 **編集 (コマンドを)**  
  [**:**] **ED**  
 テキスト エディターを開始します。 このエディターは、現在の [!INCLUDE[tsql](../includes/tsql-md.md)] バッチまたは最後に実行したバッチを編集する場合に使用できます。 最後に実行したバッチを編集するには、最後のバッチの実行が完了した直後に **ED** コマンドを入力する必要があります。  
  
 テキスト エディターは、SQLCMDEDITOR 環境変数で定義したエディターです。 既定のエディターは "Edit" です。 エディターを変更するには、SQLCMDEDITOR 環境変数を設定します。 たとえば、エディターを [!INCLUDE[msCoName](../includes/msconame-md.md)] メモ帳に設定するには、コマンド プロンプトで次のように入力します。  
  
 `SET SQLCMDEDITOR=notepad`  
  
 [**:**] **RESET**  
 ステートメント キャッシュをクリアします。  
  
 **: リスト**  
 ステートメント キャッシュの内容を出力します。  
  
 **変数:**  
  **: Setvar** \< **var**> [ **"*`value`*"** ]  
 
  `sqlcmd` スクリプト変数を定義します。 スクリプト変数は `$(VARNAME)`という形式になります。  
  
 変数名では大文字と小文字が区別されません。  
  
 スクリプト変数は次の方法で指定できます。  
  
-   コマンド ラインのオプションを暗黙的に使用します。 たとえば、 **-l**オプションを指定すると、SQLCMDLOGINTIMEOUT `sqlcmd`変数が設定されます。  
  
-   
  **:Setvar** コマンドを明示的に使用します。  
  
-   
  `sqlcmd` の実行前に環境変数を定義します。  
  
> [!NOTE]  
>  
  `-X` オプションを使用すると、環境変数が `sqlcmd` に渡されなくなります。  
  
 
  **:Setvar** を使って定義した変数と環境変数が同じ名前の場合は、 **:Setvar** を使用して定義した変数が優先されます。  
  
 変数名には空白文字を含めることはできません。  
  
 また変数名には、$ (var) のような変数表現と同じ形式を使用することはできません。  
  
 スクリプト変数の文字列値に空白文字が含まれる場合は、値を引用符で囲みます。 スクリプト変数の値を設定していない場合は、そのスクリプト変数は削除されます。  
  
 **: Listvar**  
 現在設定されているスクリプト変数の一覧を表示します。  
  
> [!NOTE]  
>  によって`sqlcmd`設定されたスクリプト変数と、 **: Setvar**コマンドを使用して設定されたスクリプト変数のみが表示されます。  
  
 **出力コマンド**  
  **: エラー**   
 **_\<_**_ファイル名_** _>|_ STDERR |STDOUT**    
 すべてのエラー出力を、 *file name*によって指定されたファイル、または **stderr** や **stdout**にリダイレクトします。 
  **Error** コマンドは、スクリプト内で複数回使用できます。 既定では、エラー出力は **stderr**に送られます。  
  
 *ファイル名*  
 出力を受信するファイルを作成して開きます。 ファイルが既に存在している場合は、ファイルは 0 バイトに切り詰められます。 権限またはその他の理由でファイルが使用できない場合は、出力は切り替えられず、最後に指定した出力先または既定の出力先に送信されます。  
  
 **標準**  
 エラー出力を **stderr** ストリームに切り替えます。 ストリームがリダイレクトされている場合は、ストリームがリダイレクトされた対象がエラー出力を受信します。  
  
 **STDOUT**  
 エラー出力を **stdout** ストリームに切り替えます。 ストリームがリダイレクトされている場合は、ストリームがリダイレクトされた対象がエラー出力を受信します。  
  
 **: 出力\< ** _ファイル名_ **>** |  **** STDERR| **STDOUT**  
 すべてのクエリ結果を、 *file name*によって指定されたファイル、または **stderr** や **stdout**に作成してリダイレクトします。 既定では、出力は **stdout**に送られます。 ファイルが既に存在している場合は、ファイルは 0 バイトに切り詰められます。 
  **Out** コマンドは、スクリプト内で複数回使用できます。  
  
 **:P erftrace \< ** _ファイル名_ **>** |  **STDERR**| **STDOUT**  
 すべてのパフォーマンス トレース情報を、 *file name*によって指定されたファイル、または **stderr** や **stdout**に作成してリダイレクトします。 既定では、パフォーマンス トレース出力は **stdout**に送られます。 ファイルが既に存在している場合は、ファイルは 0 バイトに切り詰められます。 
  **Perftrace** コマンドは、スクリプト内で複数回使用できます。  
  
 **実行制御コマンド**  
  **: エラー時**[ `exit`  |  `ignore`]  
 スクリプト実行中またはバッチ実行中のエラー発生時に対応するアクションを設定します。  
  
 
  `exit` オプションを使用した場合、`sqlcmd` は該当するエラー値を表示して終了します。  
  
 
  `ignore` オプションを使用すると、`sqlcmd` はエラーを無視し、バッチまたはスクリプトの実行を続行します。 既定では、エラー メッセージが出力されます。  
  
 [**:**] **QUIT**  
 
  `sqlcmd` が終了します。  
  
 [**:**]**終了**[ **(*`statement`*)** ]  
 では、から`sqlcmd`の戻り値として SELECT ステートメントの結果を使用できます。 数値の場合、結果行の最終行の第 1 列は、4 バイトの (長) 整数に変換されます。 MS-DOS は、下位バイトを親プロセスやオペレーティング システムのエラー レベルに渡します。 Windows 200x では、4 バイトの整数全体を渡します。 の構文は次のとおりです。  
  
 `:EXIT(query)`  
  
 次に例を示します。  
  
 `:EXIT(SELECT @@ROWCOUNT)`  
  
 バッチファイルの一部として、 **EXIT**パラメーターを含めることもできます。 たとえば、コマンド プロンプトで次のように入力します。  
  
 `sqlcmd -Q "EXIT(SELECT COUNT(*) FROM '%1')"`  
  
 ユーティリティ`sqlcmd`は、かっこ **()** の間にあるすべての情報をサーバーに送信します。 システム ストアド プロシージャで 1 つの値セットを選択し、値を返すように指定した場合、返されるのは選択した値のみです。 かっこ内に何も指定せずに EXIT **()** ステートメントを指定すると、バッチ内のそのステートメントより前にあるものすべてを実行し、戻り値を返さずに終了します。  
  
 不適切なクエリを指定すると、`sqlcmd` は戻り値を返さずに終了します。  
  
 EXIT の形式を次に示します。  
  
-   :EXIT  
  
 バッチを実行せずに直ちに終了し、値を返しません。  
  
-   :EXIT ( )  
  
 バッチを実行してから終了し、値を返しません。  
  
-   :EXIT (query)  
  
 クエリを含むバッチを実行し、クエリの結果を返して終了します。  
  
 RAISERROR を`sqlcmd`スクリプト内で使用し、状態127が発生した場合`sqlcmd` 、はを終了し、メッセージ ID をクライアントに返します。 次に例を示します。  
  
 `RAISERROR(50001, 10, 127)`  
  
 このエラーが発生すると、`sqlcmd` スクリプトは終了し、メッセージ ID 50001 がクライアントに返されます。  
  
 戻り値 -1 ～ -99 は [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] によって予約済みです。`sqlcmd` では次のような追加の戻り値を定義しています。  
  
|戻り値|[説明]|  
|-------------------|-----------------|  
|-100|戻り値を選択する前に、エラーが発生した。|  
|-101|戻り値を選択するときに、行が見つからなかった。|  
|-102|戻り値を選択するときに、変換エラーが発生した。|  
  
 **[** *カウント*]  
 GO は、バッチの終わりとキャッシュされた [!INCLUDE[tsql](../includes/tsql-md.md)] ステートメントの実行を知らせます。 
  *count* の値を指定すると、キャッシュされたステートメントが 1 つのバッチとして *count* の回数だけ実行されます。  
  
 **その他のコマンド**  
  **: r \< ** _ファイル名_**>**  
 によっ[!INCLUDE[tsql](../includes/tsql-md.md)] `sqlcmd` ** <て*`filename`*** 指定されたファイルから、ステートメントキャッシュに追加のステートメントとコマンドを解析します。  
  
 
  [!INCLUDE[tsql](../includes/tsql-md.md)]GO** が最後に記述されていない ** ステートメントがファイルに含まれている場合は、その行の **:r** の後に **GO** を入力する必要があります。  
  
> [!NOTE]  
>  **\<**_ファイル名_ **>** は、 `sqlcmd`が実行されたスタートアップディレクトリに対して相対的に読み取られます。  
  
 ファイルは、バッチ ターミネータが検出された後に読み取られ、実行されます。 
  **:r** コマンドは複数発行できます。 ファイルには、どのような `sqlcmd` コマンドでも含めることができます。 これには、バッチ ターミネータの **GO**も含まれます。  
  
> [!NOTE]  
>  対話モードで表示される行数は、 **:r** コマンドが検出されるたびに、1 行ずつ増えます。 
  **:r** コマンドは、リスト コマンドの出力に表示されます。  
  
 **: Serverlist**  
 ローカルに構成されたサーバーと、ネットワーク上でブロードキャストしているサーバー名の一覧を表示します。  
  
 **: Connect** _server_name_[**\\**_instance_name_] [-l *timeout*] [-U *user_name* [-P *password*]]  
 
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスに接続します。 また、現在の接続を終了します。  
  
 タイムアウト オプション :  
  
|||  
|-|-|  
|0|待機状態を維持|  
|n>0|n 秒間待機|  
  
 SQLCMDSERVER スクリプト変数により、現在のアクティブな接続が反映されます。  
  
 
  *timeout* を指定しないと、SQLCMDLOGINTIMEOUT 変数の値が既定値になります。  
  
 
  *user_name* のみを指定した場合 (オプションとして指定した場合も、環境変数として指定した場合も)、ユーザーはパスワードの入力を要求されます。 SQLCMDUSER 環境変数または SQLCMDPASSWORD 環境変数が設定されている場合は、この限りではありません。 オプションも環境変数も提供されない場合は、Windows 認証モードを使用してログインします。 たとえば、統合セキュリティを使用して、`instance1` である [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンス `myserver` に接続するには、次を使用します。  
  
 `:connect myserver\instance1`  
  
 スクリプト変数を使用して `myserver` の既定のインスタンスに接続するには、次を使用します。  
  
 `:setvar myusername test`  
  
 `:setvar myservername myserver`  
  
 `:connect $(myservername) $(myusername)`  
  
 [**:**]**!!**\< *コマンド*>  
 オペレーティング システムのコマンドを実行します。 オペレーティング システムのコマンドを実行するには、行頭に 2 つの感嘆符 (**!!**) を入力し、続けてオペレーティング システムのコマンドを入力します。 次に例を示します。  
  
 `:!! Dir`  
  
> [!NOTE]  
>  コマンドは `sqlcmd` を実行中のコンピューター上で実行されます。  
  
 **: XML** [**ON** | **OFF**]  
 詳細については、このトピックの「XML 出力形式」を参照してください。  
  
 **: ヘルプ**  
 
  `sqlcmd` コマンドと各コマンドの短い説明を一覧表示します。  
  
### <a name="sqlcmd-file-names"></a>sqlcmd のファイル名  
 `sqlcmd`入力ファイルは、 **-i**オプションまたは **: r**コマンドで指定できます。 出力ファイルは **-o** オプションまたは **:Error**、 **:Out** 、および **:Perftrace** コマンドで指定できます。 指定するファイルについてのガイドラインを次に示します。  
  
-   **: Error**、 **: Out**および **:P erftrace**では、 ** < *`filename`*** 別個のを使用する必要があります。 ** <同じ*`filename`* **が使用されている場合は、コマンドからの入力が混在している可能性があります。  
  
-   ローカル コンピューターの `sqlcmd` からリモート サーバー上の入力ファイルが呼び出され、ファイルに :out c:\OutputFile.txt のようにドライブ パスが含まれていると、 出力ファイルはリモート サーバーではなく、ローカル コンピューター上に作成されます。  
  
-   有効なファイルパスは次の\\**<*`filename`*** とおり\\ \\です:\> \\ C:、<\\ ** < *`filename`* ** Server<$>、\\**<*`file name`***"c:\ フォルダー" を共有します。 パスに空白が含まれる場合は、引用符を使用します。  
  
-   各新規 `sqlcmd` セッションは同じ名前の既存のファイルを上書きします。  
  
### <a name="informational-messages"></a>情報メッセージ  
 
  `sqlcmd` は、サーバーから送信されたすべての情報メッセージを出力します。 次の例では、[!INCLUDE[tsql](../includes/tsql-md.md)] ステートメントが実行された後、情報メッセージが出力されます。  
  
 コマンド プロンプトで、次のように入力します:  
  
 `sqlcmd`  
  
 `At the sqlcmd prompt type:`  
  
 `USE AdventureWorks2012;`  
  
 `GO`  
  
 Enter キーを押すと、"データベース コンテキストが 'AdventureWorks2012' に変更されました。" という情報メッセージが出力されます。  
  
### <a name="output-format-from-transact-sql-queries"></a>Transact-SQL クエリからの出力形式  
 まず、`sqlcmd` は SELECT リストで指定した列名を含む列ヘッダーを出力します。 列名は、SQLCMDCOLSEP で指定された文字を使用して分割されます。 既定では、空白です。 列名が列幅よりも短い場合は、出力は次の列まで空白で埋められます。  
  
 この行の次には区切り行が出力されます。区切り行は、連続したダッシュ文字です。 次に出力の例を示します。  
  
 `sqlcmd`を起動します。 
  `sqlcmd` コマンド プロンプトで次のように入力します。  
  
 `USE AdventureWorks2012;`  
  
 `SELECT TOP (2) BusinessEntityID, FirstName, LastName`  
  
 `FROM Person.Person;`  
  
 `GO`  
  
 Enter キーを押すと、次の結果セットが返されます。  
  
 `BusinessEntityID FirstName    LastName`  
  
 `---------------- ------------ ----------`  
  
 `285              Syed         Abbas`  
  
 `293              Catherine    Abel`  
  
 `(2 row(s) affected)`  
  
 
  `BusinessEntityID` 列には 4 文字分の幅しかありませんが、長い列名に合わせるため拡張されています。 既定では、出力は 80 文字で終了します。 この設定は、 **-w** オプションを使用するか、SQLCMDCOLWIDTH スクリプト変数を設定することで変更できます。  
  
### <a name="xml-output-format"></a>XML 出力形式  
 FOR XML 句からの結果である XML 出力は、連続するストリームでフォーマットされずに出力されます。  
  
 XML 出力を行うには、 `:XML ON`コマンドを使用します。  
  
> [!NOTE]  
>  
  `sqlcmd` は、通常の形式のエラー メッセージを返します。 エラー メッセージが XML 形式の XML テキスト ストリームで出力されることにも注意してください。 
  `:XML ON` を使用すると、`sqlcmd` は情報メッセージを表示しません。  
  
 XML モードをオフにするには、 `:XML OFF`コマンドを使用します。  
  
 XML OFF コマンドは `sqlcmd` を行指向の出力に切り替えるので、XML OFF コマンドの実行前に GO コマンドは指定しないでください。  
  
 XML (ストリーム入力) データと行セットのデータは、混在することはできません。 XML ストリームを出力する [!INCLUDE[tsql](../includes/tsql-md.md)] ステートメントの実行前に、XML ON コマンドが実行されていない場合は、正しく出力されません。 XML ON コマンドが実行されている場合は、通常の行セットを出力する [!INCLUDE[tsql](../includes/tsql-md.md)] ステートメントは実行できません。  
  
> [!NOTE]  
>  
  **:XML** コマンドは SET STATISTICS XML ステートメントをサポートしません。  
  
## <a name="sqlcmd-best-practices"></a>sqlcmd のベスト プラクティス  
 次の説明を参考にして、セキュリティと効率を最大にしてください。  
  
-   統合セキュリティを使用します。  
  
-   自動化された環境では `-X` を使用します。  
  
-   適切な NTFS ファイル システム権限を使用して、入力ファイルと出力ファイルのセキュリティを保護します。  
  
-   パフォーマンスを向上させるには、複数のセッションではなく、1 つの `sqlcmd` セッションの中で、できるだけ作業するようにします。  
  
-   バッチまたはクエリ実行のタイムアウト値を、推定所要時間よりも長めに設定します。  
  
## <a name="see-also"></a>参照  
 [sqlcmd ユーティリティの起動](../relational-databases/scripting/sqlcmd-start-the-utility.md)   
 [Sqlcmd を使用した Transact-sql スクリプトファイルの実行](../relational-databases/scripting/sqlcmd-run-transact-sql-script-files.md)   
 [Sqlcmd ユーティリティを使用する](../relational-databases/scripting/sqlcmd-use-the-utility.md)   
 [Sqlcmd をスクリプト変数と共に使用する](../relational-databases/scripting/sqlcmd-use-with-scripting-variables.md)   
 [Sqlcmd を使用してデータベースエンジンに接続する](../relational-databases/scripting/sqlcmd-connect-to-the-database-engine.md)   
 [クエリエディターを使用して SQLCMD スクリプトを編集する](../relational-databases/scripting/edit-sqlcmd-scripts-with-query-editor.md)   
 [ジョブステップの管理](../ssms/agent/manage-job-steps.md)   
 [CmdExec ジョブ ステップの作成](../ssms/agent/create-a-cmdexec-job-step.md)  
  
  

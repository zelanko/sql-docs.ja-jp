---
title: "Oracle パブリッシャーのトラブルシューティング | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Oracle パブリッシング [SQL Server レプリケーション]、トラブルシューティング"
  - "トラブルシューティング [SQL Server レプリケーション]、Oracle パブリッシング"
ms.assetid: be94f1c1-816b-4b1d-83f6-2fd6f5807ab7
caps.latest.revision: 62
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 62
---
# Oracle パブリッシャーのトラブルシューティング
  このトピックでは、Oracle パブリッシャーを構成および使用する際に発生する可能性のあるいくつかの問題を示します。  
  
## Oracle クライアントおよびネットワーキング ソフトウェアに関連するエラーが発生する  
 アカウントが [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ディストリビューターで実行されている必要があります読み取りし、付与する Oracle クライアント ネットワーク ソフトウェアがインストールされているディレクトリ (およびすべてのサブディレクトリ) に対するアクセス許可を実行します。 これらの権限が付与されていなかったり、Oracle クライアント コンポーネントが正しくインストールされていない場合は、次のエラー メッセージが表示されます。  
  
 "[Microsoft OLE DB Provider for Oracle] によるサーバーへの接続に失敗しました。 Oracle クライアントおよびネットワーク コンポーネントが見つかりません。 これらのコンポーネントは、Oracle Corporation によって提供され、Oracle バージョン 7.3.3 以降のクライアント ソフトウェエア インストールの一部です。 これらのコンポーネントがインストールされるまで、プロバイダーは機能しません。"  
  
 適切な Oracle クライアントがディストリビューターにインストールされている場合は、そのクライアントのインストールが完了した後に、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] をいったん停止して再起動したか確認してください。 これは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] でクライアント コンポーネントを認識するために必要です。  
  
 権限が付与されていること、およびコンポーネントが正しくインストールされていることを確認したにもかかわらず、このエラーが継続して発生する場合は、HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDTC\MTxOCI のレジストリ設定が正しいかどうかを確認してください。  
  
-   Oracle 10g の場合、正しい設定は次のようになります。  
  
    -   OracleOciLib = oci.dll  
  
    -   OracleSqlLib = orasql10.dll  
  
    -   OracleXaLib = oraclient10.dll  
  
-   Oracle 9i の場合、正しい設定は次のようになります。  
  
    -   OracleOciLib = oci.dll  
  
    -   OracleSqlLib = orasql9.dll  
  
    -   OracleXaLib = oraclient9.dll  
  
## SQL Server ディストリビューターが Oracle データベース インスタンスに接続できない  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ディストリビューターが Oracle パブリッシャーに接続できない場合は、次の点を確認してください。  
  
-   必要な Oracle ソフトウェアがディストリビューターにインストールされているかどうか。  
  
-   Oracle データベースがオンラインになっており、SQL*Plus などのツールを使用して Oracle データベースに接続できるかどうか。  
  
-   レプリケーションが Oracle パブリッシャーに接続する際に使用するログインに十分な権限があるかどうか。 詳細については、次を参照してください。 [Oracle パブリッシャーを構成する](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)です。  
  
-   Oracle パブリッシャーの構成中に定義された TNS 名が tnsnames.ora ファイルに記載されているかどうか。  
  
-   正しい Oracle ホームおよびパスが使用されているかどうか。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ディストリビューターに Oracle バイナリのセットが 1 つしかインストールされていない場合でも、Oracle ホーム関連の環境変数が正しく設定されていることを確認してください。 環境変数の値を変更した場合は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を停止してから再起動して、変更を有効にする必要があります。  
  
 構成および接続のテストに関する詳細については、次を参照してください。"をインストールおよび構成する Oracle クライアント ネットワーク ソフトウェアを、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ディストリビューター"で [Oracle パブリッシャーを構成する](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)です。  
  
## Oracle パブリッシャーが別のディストリビューターに関連付けられている  
 Oracle パブリッシャーは、1 つの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ディストリビューターにのみ関連付けることができます。 別のディストリビューターを Oracle パブリッシャーに関連付ける場合は、関連付けられているディストリビューターを削除してから、別のディストリビューターを使用する必要があります。 ディストリビューターを最初に削除しない場合、次のエラー メッセージのいずれかが表示されます。  
  
-   "Oracle サーバー インスタンス '\<*OraclePublisherName*>' を使用する以前に構成されている' \<*SQLServerDistributorName*>' のディストリビューターとして。 使用を開始する ' \<*NewSQLServerDistributorName*>' のディストリビューターとしては、そのサーバー インスタンスのすべてのパブリケーションを削除、Oracle サーバー インスタンスの現在のレプリケーション構成を削除する必要があります"。  
  
-   "Oracle サーバー '\<*OracleServerName*>' は既にパブリッシャーとして定義されている' \<*OraclePublisherName*>' ディストリビューター側の ' \<*SQLServerDistributorName*>.*\< DistributionDatabaseName>*' です。 パブリッシャーを削除するか、パブリック シノニム '*\< SynonymName>*' を再作成します"。  
  
 Oracle パブリッシャーが削除されると、Oracle データベース内のレプリケーション オブジェクトが自動的にクリーンアップされます。 ただし、Oracle レプリケーション オブジェクトを手動でクリーンアップすることが必要な場合もあります。 レプリケーションで作成した Oracle レプリケーション オブジェクトを手動でクリーン アップするには、次の手順を実行します。  
  
1.  DBA 権限で Oracle パブリッシャーに接続します。  
  
2.  SQL コマンド `DROP PUBLIC SYNONYM MSSQLSERVERDISTRIBUTOR;` を実行します。  
  
3.  SQL コマンド `DROP USER <replication_administrative_user_schema>``CASCADE;` を実行します。  
  
## 主キーの欠如に関する SQL Server エラー 21663 が発生する  
 トランザクション パブリケーションのアーティクルには、有効な主キーが必要です。 有効な主キーがない場合は、アーティクルを追加しようとすると、次のエラー メッセージが表示されます。  
  
 "ソース テーブルの有効な主キーが見つかりません [\<*TableOwner*>]. [\<*TableName*>]"  
  
 主キーの要件については、「」のセクション「一意のインデックスおよび制約」を参照してください。 [設計に関する考慮事項と Oracle パブリッシャーに対して制限](../../../relational-databases/replication/non-sql/design-considerations-and-limitations-for-oracle-publishers.md)します。  
  
## リンク サーバー ログインの重複に関する SQL Server エラー 21642 が発生する  
 Oracle パブリッシャーを最初に構成するときに、パブリッシャーとディストリビューター間の接続用にリンク サーバー エントリが作成されます。 リンク サーバーには、Oracle TNS サービスと同じ名前が付けられます。 同じ名前でリンク サーバーを作成しようとすると、次のエラー メッセージが表示されます。  
  
 "異種パブリッシャーにはリンク サーバーが必要です。 というリンク サーバー '*\< LinkedServerName>*' は既に存在します。 リンク サーバーを削除するか、または別のパブリッシャー名を選択してください。"  
  
 このエラーは、リンク サーバーを直接作成しようとしたり、Oracle パブリッシャーと [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ディストリビューター間のリレーションシップを以前に削除し、再構成しようとしている場合に発生する可能性があります。 パブリッシャーを再構成しようとしています。 このエラーが発生した場合は、リンク サーバーを削除 [sp_dropserver & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-dropserver-transact-sql.md)します。  
  
 リンク サーバー接続を介して、Oracle パブリッシャーに接続する場合は、別の TNS サービス名を作成しを呼び出すときにこの名前を使用して [sp_addlinkedserver & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)します。 TNS サービス名の作成の詳細については、Oracle のマニュアルを参照してください。  
  
## SQL Server エラー 21617 が発生する  
 Oracle パブリッシングでは、Oracle アプリケーション SQL*PLUS を使用して、パブリッシャー サポートコードのパッケージを Oracle データベースにダウンロードします。 Oracle パブリッシャーを構成する前に [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 検証によって、SQL\*さらに、ディストリビューター側のシステム パスを通じてアクセスします。 場合 SQL\*と読み込まれた場合、次のエラー メッセージが表示することはできません。  
  
 "SQL*PLUS を実行できません。 ディストリビューターに Oracle クライアント コードの現在のバージョンがインストールされていることを確認してください。"  
  
 SQL 配置しようとしています。\*に加えて、ディストリビューター側のです。 Oracle 10g クライアント インストールの場合、この実行可能ファイルの名前は sqlplus.exe です。 通常は %ORACLE_HOME%/bin にインストールされています。 確認する SQL のパス\*PLUS システム パスに、システム変数の値を調べて **パス**:  
  
1.  右クリック **マイ コンピューター**, 、クリックして **プロパティ**します。  
  
2.  クリックして、 **詳細** タブをクリックし、をクリックして **環境変数**します。  
  
3.   **環境変数** ダイアログ ボックスで、 **システム変数** 一覧で、[、 **パス** 変数、およびクリック **編集**します。  
  
4.   **システム変数の編集** ] ダイアログ ボックス: sqlplus.exe を含むフォルダーへのパスがにないかどうかは、 **変数値** テキスト ボックスに、それを含む文字列を編集します。  
  
5.  クリックして **OK** を終了し、変更を保存するには、各 [開く] ダイアログ ボックス。  
  
 ディストリビューターで sqlplus.exe が見つからない場合は、Oracle クライアント ソフトウェアの現在のバージョンをディストリビューターにインストールします。 詳細については、次を参照してください。 [Oracle パブリッシャーを構成する](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)です。  
  
## SQL Server エラー 21620 が発生する  
 Oracle データベースのバージョン 8.1 よりも前のバージョンに接続している場合、Oracle パブリッシングでは、ディストリビューターにインストールされている Oracle クライアント ソフトウェアが、バージョン 9 からのものである必要があります。 Oracle データベースのバージョン 8.1 以降に接続している場合は、Oracle クライアント ソフトウェアのバージョン 10 以降を使用することをお勧めします。  
  
 Oracle パブリッシャーを構成する前に、Oracle パブリッシングはディストリビューターのシステム パスを介してアクセスできる SQL*PLUS のバージョンが、バージョン 9 以降であることを確認します。 バージョン 9 以降でない場合、次のエラー メッセージが表示されます。  
  
 "システムの Path 変数からアクセスできる SQL*PLUS のバージョンが古いため、Oracle パブリッシングをサポートできません。 ディストリビューターに Oracle クライアント コードの現在のバージョンがインストールされていることを確認してください。"  
  
 ディストリビューターに Oracle クライアント ソフトウェアの複数のバージョンがインストールされている場合は、最新のバージョンが少なくともバージョン 9 であり、システム パス変数でそのバージョンが最初に参照されていることを確認します (最新のバージョンが最初に参照されていれば、他のバージョンが参照されていてもかまいません)。 システム パス変数の編集に関する詳細については、このトピックで既に説明した「SQL Server エラー 21617 が発生する」を参照してください。  
  
## SQL Server エラー 21624 または SQL Server エラー 21629 が発生する  
 64 ビット ディストリビューターの場合、Oracle パブリッシングでは、Oracle OLEDB Provider for Oracle (OraOLEDB.Oracle) が使用されます。 ディストリビューターに Oracle OLEDB プロバイダーがインストールおよび登録されていることを確認してください。 このプロバイダーがインストールおよび登録されていない場合、次のエラー メッセージのいずれかまたは両方が表示されます。  
  
-   "ディストリビューター '%s' に登録済みの Oracle OLEDB プロバイダー OraOLEDB.Oracle が見つかりません。 ディストリビューターに現在のバージョンの Oracle OLEDB プロバイダーがインストールおよび登録されていることを確認してください。"  
  
-   "Oracle 用の Oracle OLEDB プロバイダー OraOLEDB.Oracle が登録されていることを示す CLSID レジストリ キーがディストリビューターに存在しません。 ディストリビューターに Oracle OLEDB プロバイダーがインストールおよび登録されていることを確認してください。"  
  
 Oracle クライアント ソフトウェア バージョン 10g を使用している場合、プロバイダーは OraOLEDB10.dll です。バージョン 9i の場合、プロバイダーは OraOLEDB.dll です。 プロバイダーは %ORACLE_HOME%\BIN (たとえば、C:\oracle\product\10.1.0\Client_1\bin) にインストールされます。 ディストリビューターに Oracle OLEDB プロバイダーがインストールされていない場合は、Oracle が提供する Oracle クライアント ソフトウェア インストール ディスクからインストールしてください。 詳細については、次を参照してください。 [Oracle パブリッシャーを構成する](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)です。  
  
 Oracle OLEDB プロバイダーがインストールされている場合は、そのプロバイダーが登録されていることを確認してください。 プロバイダーの DLL を登録するには、DLL がインストールされているディレクトリから次のコマンドを実行し、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスを停止して再起動します。  
  
1.  `regsvr32 OraOLEDB10.dll` または `regsvr32 OraOLEDB.dll`です。  
  
## SQL Server エラー 21626 または SQL Server エラー 21627 が発生する  
 Oracle パブリッシング環境が正しく構成されていることを確認するために、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] により、構成時に指定したログイン資格情報を使用して、Oracle パブリッシャーへの接続が試行されます。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ディストリビューターが Oracle パブリッシャーに接続できない場合、次のエラー メッセージが表示されます。  
  
-   "Oracle OLEDB プロバイダー OraOLEDB.Oracle を使用して Oracle データベース サーバー '%s' に接続できません。"  
  
 このエラー メッセージが表示された場合は、Oracle パブリッシャーの構成時に指定したのと同じログインとパスワードを使用して SQL*PLUS を直接実行することにより、Oracle データベースへの接続を確認してください。 詳細については、このトピックで既に説明した「SQL Server ディストリビューターが Oracle データベース インスタンスに接続できない」を参照してください。  
  
## SQL Server エラー 21628 が発生する  
 64 ビット ディストリビューターの場合、Oracle パブリッシングでは、Oracle OLEDB Provider for Oracle (OraOLEDB.Oracle) が使用されます。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] プロセスで実行する Oracle プロバイダーを許可するようにレジストリ エントリが作成 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]します。 このレジストリ エントリの読み取りまたは書き込みに問題がある場合、次のエラー メッセージが表示されます。  
  
 "ディストリビューター '%s' のレジストリを更新し、Oracle OLEDB プロバイダー OraOLEDB.Oracle を [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] と同じプロセスで実行可能にすることができません。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] が所有しているレジストリ キーの変更が現在のログインに許可されていることを確認してください。"  
  
 Oracle のパブリッシングでは、レジストリ エントリが存在しに設定されている **1** 64 ビット ディストリビューターです。 このエントリが存在しない場合は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] によって作成されます。 エントリが存在する場合に設定されている **0**, 、この設定は変更できません。 Oracle パブリッシャーの構成が失敗します。  
  
 レジストリ設定を表示および変更するには、次の手順を実行します。  
  
1.  クリックして **開始**, 、順にクリック **実行**します。  
  
2.   **実行** ] ダイアログ ボックスで、「 **regedit**, 、順にクリック **OK**します。  
  
3.  Hkey_local_machine \software\microsoft\microsoft SQL Server に移動\\*\< InstanceName>*\Providers します。  
  
     [Providers] の下に、[OraOLEDB.Oracle] という名前のフォルダーがあります。 このフォルダー内の名前の DWORD 値とする必要があります **AllowInProcess**, の値を持つ **1**します。  
  
4.  わかった場合 **AllowInProcess** に設定されている **0**, にレジストリ エントリを更新する **1**:  
  
    1.  クリックして、エントリを右クリックして **変更**します。  
  
    2.   **文字列の編集** ] ダイアログ ボックスで、「 **1** で、 **データ** フィールドです。  
  
## SQL Server エラー 21684 が発生する  
 管理ユーザー アカウントに十分な権限がない場合は、次のエラー メッセージが表示されます。  
  
 "Oracle パブリッシャー '%s' の管理者ログインに関連付けられた権限が不十分です。"  
  
 ユーザーに与えられた権限を確認するには、クエリ `SELECT * from session_privs` を実行します。 出力は次のようになります。  
  
 `PRIVILEGE`  
  
 `------------------`  
  
 `CREATE SESSION`  
  
 `CREATE TABLE`  
  
 `CREATE PUBLIC SYNONYM`  
  
 `DROP PUBLIC SYNONYM`  
  
 `CREATE VIEW`  
  
 `CREATE SEQUENCE`  
  
 `CREATE PROCEDURE`  
  
 `CREATE TRIGGER`  
  
## レプリケーション ユーザー スキーマの権限に関する問題が発生する  
 レプリケーション ユーザー スキーマには、「を作成する、手動によるユーザー スキーマ」で説明したアクセス許可が必要 [Oracle パブリッシャーを構成する](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)です。  
  
## Oracle エラー ORA-01000  
 パブリケーションへアーティクルを追加処理中に、レプリケーションは Oracle パブリッシャーでカーソルを使用します。 この処理中にパブリッシャーで使用できるカーソルの最大数を超える可能性があります。 最大数を超えると、次のエラーが発生します。  
  
 "ORA-01000: maximum open cursors exceeded"  
  
 この問題を回避することを確認、 **max_open_cursors** Oracle データベースでの設定が十分に高い値 (1000 以上) に設定します。 この設定の詳細については Oracle のマニュアルを参照してください。  
  
## Oracle エラー ORA-01555  
 次の Oracle データベース エラーは、スナップショット レプリケーションに関連するものではありません。このエラーは、Oracle でのデータの読み取り一貫性ビューの構築方法に関連します。  
  
 "ORA-01555: Snapshot too old"  
  
 Oracle では、ロールバック セグメントと呼ばれるオブジェクトを使用して、SQL ステートメントの発行時点のデータの読み取り一貫性ビューを構築します。 "Snapshot too old" エラーは、ロールバック情報が他の同時接続セッションによって上書きされた場合に発生する可能性があります。 Oracle 9i よりも前のバージョンでは、このエラーの発生頻度を減らす方法として、ロールバック セグメントのサイズや数を増やしたり、大きいトランザクションを特定のロールバック セグメントに割り当てる方法が推奨されていました。  
  
 Oracle 9i では、ロールバック セグメントに代わる、UNDO テーブルスペースの概念が導入されました。 Oracle 9i で "Snapshot too old" エラーを回避するには、次の方法をお勧めします。  
  
-   十分な空き領域を持つ UNDO テーブルスペースを作成する。  
  
-   作成したテーブルスペースに保証される保有期間を設定する (Oracle 10G 以上)。  
  
-   Oracle の初期化パラメーター UNDO_MANAGEMENT および UNDO_RETENTION を構成する。  
  
 "Snapshot too old" エラーを回避する方法の詳細については、Oracle のマニュアルを参照してください。  
  
## Oracle エラー ORA-22285  
 テーブルに BFILE 列が含まれている場合、この列のデータはファイル システムに格納されます。 レプリケーション管理ユーザー アカウントには、次の構文を使用して、このデータが格納されているディレクトリへのアクセスを許可する必要があります。  
  
 `GRANT READ ON DIRECTORY <directory_name> TO <replication_administrative_user_schema>`  
  
 アクセスが許可されていない場合は、ログ リーダー エージェントにより次のエラーが発生します。  
  
 "ORA-22285: non-existent directory or file for FILEOPEN operation"  
  
## パブリッシャーの再構成が必要になる変更  
 レプリケーション メタデータ テーブルまたはプロシージャを変更した場合は、パブリッシャーを削除して再構成する必要があります。 パブリッシャーを再構成するには、パブリッシャーを削除し、[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、Transact-SQL、または RMO を使用してパブリッシャーを再構成する必要があります。 パブリッシャーの構成については、次を参照してください。 [Oracle パブリッシャーを構成する](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)です。  
  
 **Oracle パブリッシャーを削除する (**SQL Server Management Studio**)**  
  
1.  [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] の Oracle パブリッシャーのディストリビューターに接続し、サーバー ノードを展開します。  
  
2.  右クリック **レプリケーション**, 、クリックして **ディストリビューターのプロパティ**します。  
  
3.   **パブリッシャー** のページ、 **ディストリビューターのプロパティ** ] ダイアログ ボックスで、チェック ボックスをクリア Oracle パブリッシャーのです。  
  
4.  クリックして **OK**です。  
  
 **Oracle パブリッシャーを削除するには (Transact-SQL)**  
  
-   実行 **sp_dropdistpublisher**します。 詳細については、次を参照してください。 [sp_dropdistpublisher & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md)します。  
  
## 参照  
 [Oracle パブリッシャーの構成](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)   
 [Oracle パブリッシングの概要](../../../relational-databases/replication/non-sql/oracle-publishing-overview.md)  
  
  
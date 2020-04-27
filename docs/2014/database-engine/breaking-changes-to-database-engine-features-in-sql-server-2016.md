---
title: SQL Server 2014 | のデータベースエンジン機能の重大な変更Microsoft Docs
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: release-landing
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server], what's new
- breaking changes [SQL Server]
ms.assetid: 47edefbd-a09b-4087-937a-453cd5c6e061
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d7b5bf6ff2324c8e63b030d03e36794faf0ec9d4
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "67419038"
---
# <a name="breaking-changes-to-database-engine-features-in-sql-server-2014"></a>SQL Server 2014 におけるデータベース エンジン機能の重大な変更
  このトピックでは[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] 、以前のバージョンのにおける[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]重大な変更について説明します。 これらの変更によって、以前のバージョンの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]に基づくアプリケーション、スクリプト、または機能が使用できなくなる場合があります。 この問題は、アップグレードするときに発生することがあります。 詳細については、「 [Use Upgrade Advisor to Prepare for Upgrades](../sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md)」を参照してください。  
  
##  <a name="breaking-changes-in-sssql14"></a><a name="SQL14"></a>[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] における重大な変更  
 新しい事項はありません。  
  
##  <a name="breaking-changes-in-sssql11"></a><a name="Denali"></a>における重大な変更[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]  
  
### <a name="transact-sql"></a>Transact-SQL  
  
|機能|説明|  
|-------------|-----------------|  
|NEXT という名前の列またはテーブルから選択している|シーケンスでは、ANSI 標準の NEXT VALUE FOR 関数が使用されます。 テーブルまたは列の名前が NEXT で、テーブルまたは列に値が指定されていて、ANSI 標準の AS が省略されている場合は、結果のステートメントによってエラーが発生する可能性があります。 問題を回避するには、ANSI 標準の AS キーワードを含めます。 たとえば、`SELECT NEXT VALUE FROM Table` は `SELECT NEXT AS VALUE FROM Table` に書き直す必要があり、`SELECT Col1 FROM NEXT VALUE` は `SELECT Col1 FROM NEXT AS VALUE` に書き直す必要があります。|  
|PIVOT 演算子|PIVOT 演算子は、データベースの互換性レベルが 110 に設定されている場合、再帰共通テーブル式 (CTE) クエリでは許可されません。 クエリを書き直すか、または互換性レベルを 100 以下に変更してください。 再帰 CTE クエリで PIVOT を使用すると、グループごとに複数の行がある場合に、誤った結果が返されます。|  
|sp_setapprole と sp_unsetapprole|の`OUTPUT` `sp_setapprole` cookie パラメーターは現在、正しい最大`varbinary(8000)`長であるとしてドキュメントに記載されています。 ただし、現在の実装では `varbinary(50)` を返します。 将来のリリースでクッキー `varbinary(8000)`の戻り値のサイズが増加してもアプリケーションが正常に動作するように、アプリケーションの予約を続行する必要があります。 詳細については、「[sp_setapprole &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-setapprole-transact-sql)」を参照してください。|  
|EXECUTE AS|EXECUTE AS のクッキーの OUTPUT パラメーターは現在、適切な最大長である `varbinary(8000)` としてドキュメントに記載されています。 ただし、現在の実装では `varbinary(100)` を返します。 将来のリリースでクッキー `varbinary(8000)`の戻り値のサイズが増加してもアプリケーションが正常に動作するように、アプリケーションの予約を続行する必要があります。 詳細については、「[EXECUTE AS &#40;Transact-SQL&#41;](/sql/t-sql/statements/execute-as-transact-sql)」を参照してください。|  
|sys.fn_get_audit_file 関数|ユーザー定義の監査イベントをサポートするために、2つの列 (**user_defined_event_id**と**user_defined_information**) が追加されました。 名前で列を選択しないアプリケーションは、予想よりも多くの列を返す場合があります。 名前で列を選択するか、これらの追加列を受け入れるようにアプリケーションを調整してください。|  
|WITHIN 予約キーワード|WITHIN は予約キーワードになりました。 "within" という名前のオブジェクトまたは列への参照は失敗します。 オブジェクトまたは列の名前を変更するか、または角かっこや引用符を使用して名前を区切ってください。  たとえば、`SELECT * FROM [within]` のようにします。|  
|`time` または `datetime2` 型の計算列に対する CAST および CONVERT 操作|以前のバージョンの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] では、`time` および `datetime2` データ型に対する CAST および CONVERT 操作の既定のスタイルは、いずれかの型が計算列の式で使用されている場合を除き、121 です。 計算列の場合、既定のスタイルは 0 です。 この動作は、計算列が作成されるとき、自動パラメーター化を含むクエリで使用されるとき、または制約の定義で使用されるときに、計算列に影響を与えます。<br /><br /> 互換性レベル 110 では、`time` および `datetime2` データ型に対する CAST および CONVERT 操作の既定のスタイルは常に 121 です。 クエリが古い動作に依存する場合は、110 より小さい互換性レベルを使用するか、または影響を受けるクエリで 0 スタイルを明示的に指定してください。<br /><br /> データベースを互換性レベル 110 にアップグレードしても、ディスクに格納されているユーザー データは変更されません。 このようなデータは手動で適切に修正する必要があります。 たとえば、SELECT INTO を使用して、前に説明した計算列の式を含むソースからテーブルを作成した場合は、計算列の定義自体ではなく、(スタイル 0 を使用する) データが格納されます。 このようなデータは、手動で更新してスタイル 121 に一致させる必要があります。|  
|ALTER TABLE|ALTER TABLE ステートメントでは、2 部構成 (schema.object) のテーブル名だけを使用できます。 次の形式を使用してテーブル名を指定すると、コンパイル時にエラー117が発生して失敗します。<br /><br /> server.database.schema.table<br /><br /> .database.schema.table<br /><br /> ..schema.table<br /><br /> 以前のバージョンでは、server.database.schema.table という形式を指定すると、エラー 4902 が返されました。 .database.schema.table または ..schema.table という形式を指定すると、成功しました。 問題を解決するには、4 部構成のプレフィックスの使用を削除してください。|  
|メタデータの参照|FOR BROWSE または SET NO_BROWSETABLE ON を使用してビューをクエリすると、基になるオブジェクトのメタデータではなく、ビューのメタデータが返されるようになりました。 この動作は現在、他のメタデータ参照方法と一致します。|  
|SOUNDEX|データベース互換性レベル 110 では、SOUNDEX 関数は新しいルールを実装します。このため、この関数により計算される値が、110 未満の互換性レベルで計算された値と異なる結果になる場合があります。 互換性レベル 110 へのアップグレード後に、SOUNDEX 関数を使用するインデックス、ヒープ、または CHECK 制約の再構築が必要になる場合があります。 詳細については、「[SOUNDEX (Transact-SQL)](/sql/t-sql/functions/soundex-transact-sql)」を参照してください。
|失敗した DML ステートメントの行数メッセージ|[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] では、DML ステートメントが失敗した場合、[!INCLUDE[ssDE](../includes/ssde-md.md)] は一貫して RowCount: 0 の TDS DONE トークンをクライアントに送信します。 以前のバージョンの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] では、失敗する DML ステートメントが TRY-CATCH ブロックに含まれていて、それが [!INCLUDE[ssDE](../includes/ssde-md.md)] によって自動パラメーター化されるか、または TRY-CATCH ブロックが失敗したステートメントと同じレベルにない場合、-1 という間違った値がクライアントに送信されます。 たとえば、TRY-CATCH ブロックがストアド プロシージャを呼び出し、そのプロシージャ内の DML ステートメントが失敗した場合、クライアントは -1 という間違った値を受け取ります。<br /><br /> この不適切な動作に依存するアプリケーションは失敗します。|  
|SERVERPROPERTY (' Edition ')|[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] インスタンスのインストールされている製品のエディション。 このプロパティの値を使用すると、インストールされている製品でサポートされている CPU の最大数など、機能や制限を確認できます。<br /><br /> インストールされている Enterprise edition に基づいて、"Enterprise Edition" または "Enterprise Edition: コアベースのライセンス" が返される場合があります。 Enterprise のエディションは、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の単一のインスタンスによる最大計算容量に基づいて区別されます。 の[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]計算容量制限の詳細については、「 [SQL Server のエディション別の計算容量制限](../sql-server/compute-capacity-limits-by-edition-of-sql-server.md)」を参照してください。|  
|CREATE LOGIN|`CREATE LOGIN WITH PASSWORD = '` *password*パスワード`' HASHED`オプションは、7以前で[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]作成されたハッシュでは使用できません。|  
|`datetimeoffset` の CAST 操作と CONVERT 操作|日付型と時刻型を `datetimeoffset` に変換するときにサポートされているスタイルは、0 または 1 のみです。 他のすべての変換スタイルでは 9809 が返されます。 たとえば、次のコードではエラー 9809 が返されます。<br /><br /> `SELECT CONVERT(date, CAST('7070-11-25 16:25:01.00986 -02:07' as datetimeoffset(5)), 107);`|  
  
### <a name="dynamic-management-views"></a>動的管理ビュー  
  
|表示|説明|  
|----------|-----------------|  
|sys.dm_exec_requests|command 列が `nvarchar(16)` から `nvarchar(32)` に変更されました。|  
|sys.dm_os_memory_cache_counters|次の列の名前が変更されました。<br /><br /> single_pages_kb は次のようになります。 <br />                          pages_kb<br /><br /> multi_pages_kb<br />                           次のようになりました: pages_in_use_kb|  
|sys.dm_os_memory_cache_entries|列 pages_allocated_count 列の名前が pages_kb に変更されました。|  
|sys.dm_os_memory_clerks|列 multi_pages_kb が削除されました。<br /><br /> 列 single_pages_kb 列の名前が pages_kb に変更されました。|  
|sys.dm_os_memory_nodes|次の列の名前が変更されました。<br /><br /> single_pages_kb は次のようになります。 <br />                            pages_kb<br /><br /> multi_pages_kb は次のようになります。 <br />                            foreign_committed_kb|  
|sys.dm_os_memory_objects|以下の列の名前が変更されました。<br /><br /> pages_allocated_count は次のようになります。<br />                            pages_in_bytes<br /><br /> max_pages_allocated_count は次のようになりました: max_pages_in_bytes|  
|sys.dm_os_sys_info|次の列の名前が変更されました。<br /><br /> physical_memory_in_bytes は次のようになります。 <br />                            physical_memory_kb<br /><br /> bpool_commit_target は次のようになります。 <br />                            committed_target_kb<br /><br /> bpool_visible は次のようになります。 <br />                            visible_target_kb<br /><br /> virtual_memory_in_bytes は次のようになります。 <br />                            virtual_memory_kb<br /><br /> bpool_commited は次のようになります。<br />                            committed_kb|  
|sys.dm_os_workers|ロケール列は削除されました。|  
  
### <a name="catalog-views"></a>カタログ ビュー  
  
|表示|説明|  
|----------|-----------------|  
|sys.data_spaces<br /><br /> sys.partition_schemes<br /><br /> sys.filegroups<br /><br /> sys.partition_functions|sys.data_spaces と sys.partition_functions に、新しい列 (is_system) が追加されました  (sys.partition_schemes と sys.filegroups は、sys.data_spaces の列を継承します)。<br /><br /> この列では、値 1 は、そのオブジェクトがフルテキスト インデックス フラグメントに使用されることを示します。<br /><br /> sys.partition_functions、sys.partition_schemes、および sys.filegroups では、この新しい列は末尾の列ではありません。 これらのカタログ ビューから返される列の順序に依存する既存のクエリを修正してください。|  
  
### <a name="sql-clr-data-types-geometry-geography-and-hierarchyid"></a>SQL CLR データ型 (geometry、geography、および hierarchyid)  
 空間データ型および hierarchyid 型を含むアセンブリ**Microsoft. SqlServer. .dll**は、バージョン10.0 からバージョン11.0 にアップグレードされました。 このアセンブリを参照するカスタム アプリケーションは、次の条件に該当する場合に失敗します。  
  
-   がインストールされているコンピューター [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]から、がインストールされているコンピューターにカスタムアプリケーションを移動すると、参照されているバージョン10.0 の**SqlTypes**アセンブリが存在しないため、アプリケーションは失敗します。 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] この場合、次のエラー メッセージが返されることがあります: `"Could not load file or assembly 'Microsoft.SqlServer.Types, Version=10.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91' or one of its dependencies. The system cannot find the file specified."`  
  
-   **SqlTypes**アセンブリバージョン11.0 を参照するときに、バージョン10.0 もインストールされていると、次のエラーメッセージが表示されることがあります。`"System.InvalidCastException: Unable to cast object of type 'Microsoft.SqlServer.Types.SqlGeometry' to type 'Microsoft.SqlServer.Types.SqlGeometry'."`  
  
-   .NET 3.5、4、または4.5 を対象とするカスタムアプリケーションから**SqlTypes**アセンブリバージョン11.0 を参照する場合、アプリケーションは失敗します。これは、の仕様では、アセンブリのバージョン10.0 が読み込まれるためです。 このエラーは、アプリケーションが次のいずれかのメソッドを呼び出したときに発生します。  
  
    -   `GetValue` クラスの `SqlDataReader` メソッド  
  
    -   `GetValues` クラスの `SqlDataReader` メソッド  
  
    -   `SqlDataReader` クラスの角かっこインデックス演算子 []  
  
    -   `ExecuteScalar` クラスの `SqlCommand` メソッド  
  
 この問題は、次のいずれかの方法を使用して回避できます。  
  
-   この問題を回避するには、コード内で、上にリストされている Get メソッドの代わりに `GetSqlBytes` メソッドを呼び出して、CLR [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] システム型を取得します。次に例を示します。  
  
    ```csharp  
    string query = "SELECT [SpatialColumn] FROM [SpatialTable]";  
          using (SqlConnection conn = new SqlConnection("..."))  
          {  
                SqlCommand cmd = new SqlCommand(query, conn);  
  
                conn.Open();  
                SqlDataReader reader = cmd.ExecuteReader();  
  
                while (reader.Read())  
                {  
                      // In version 11.0 only  
                      SqlGeometry g =   
    SqlGeometry.Deserialize(reader.GetSqlBytes(0));  
  
                      // In version 10.0 or 11.0  
                      SqlGeometry g2 = new SqlGeometry();  
                      g.Read(new BinaryReader(reader.GetSqlBytes(0).Stream));  
                }  
          }  
    ```  
  
-   この問題を回避するには、アプリケーション構成ファイル内でアセンブリのリダイレクトを使用します。次に例を示します。  
  
    ```xml  
    <runtime>  
    <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
        ...  
        <dependentAssembly>  
            <assemblyIdentity name="Microsoft.SqlServer.Types" publicKeyToken="89845dcd8080cc91" culture="neutral" />  
            <bindingRedirect oldVersion="10.0.0.0" newVersion="11.0.0.0" />  
        </dependentAssembly>  
        ...  
    </assemblyBinding>  
    <runtime>  
    ```  
  
-   この問題を回避するには、接続文字列内で、"Type System Version" 属性の値を "SQL Server 2012" と指定することにより、SqlClient がバージョン 11.0 のアセンブリを読み込むようにします。 この接続文字列属性は、.NET 4.5 以上でのみ使用可能です。  
  
-   `assemblyBinding` タグは `runtime` タグの下に含める必要があります。  
  
### <a name="support-for-awe"></a>AWE のサポート  
 32 ビット Address Windowing Extensions (AWE) のサポートは廃止されました。 これにより、32 ビット オペレーティング システム上でのパフォーマンスが低下する可能性があります。 大量のメモリを使用するインストールについては、64 ビット オペレーティング システムに移行してください。  
  
### <a name="xquery-functions-are-surrogate-aware"></a>サロゲート対応の XQuery 関数  
 W3C 勧告では、XQuery 関数および演算子は、上位 Unicode 文字を表すサロゲート ペアを UTF-16 エンコードの単一グリフとしてカウントするよう要求されています。 しかし、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 以前のバージョンの [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] では、文字列関数はサロゲート ペアを単一の文字として認識しません。 文字列操作 (文字列長の計算、部分文字列の抽出など) では、正しくない結果が返されました。 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] では、UTF-16 と、サロゲート ペアの正しい処理が完全にサポートされるようになりました。  
  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の XML データ型では、整形式のサロゲート ペアのみが許可されます。 ただし、一部の関数では、一定の状況下において、未定義または予期しない結果が依然として返されることがあります。これは、無効または部分的なサロゲート ペアが XQuery 関数に文字列値として渡される可能性があるためです。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] で XQuery を使用する場合は、次の方法で文字列値を生成することを検討してください。  
  
-   定数文字列値をバイナリ値として提供する。 この方法を使用した場合、無効または部分的なサロゲート ペアが渡される可能性は残ります。  
  
-   定数文字列値を、文字エンティティを提供することによって提供する。 この方法を使用した場合、無効なサロゲート ペアを渡すことはできなくなります。 XQuery 関数では、高レベルの文字に単一の文字エンティティを使用する必要があります。 これらの関数では、サロゲート ペア文字用の文字エンティティが提供された場合にエラーが発生します。  
  
-   **Sql: column**または**sql: variable**を使用して外部の値をインポートします。 これらの方法を使用した場合、無効または部分的なサロゲート ペアが使用される可能性は残ります。  
  
#### <a name="affected-xquery-functions-and-operators"></a>影響を受ける XQuery 関数と演算子  
 次の XQuery 関数および演算子は、[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] では UTF-16 のサロゲート ペアを正しく処理するようになりました。  
  
-   **fn: 文字列の長さ**。 ただし、無効または部分的なサロゲートペアが引数として渡された場合、**文字列長**の動作は未定義になります。  
  
-   **fn: substring**。  
  
-   **fn: contains が含まれて**います。 ただし、部分的なサロゲートペアが値として渡された場合、 **contains**は、適切な形式のサロゲートペアに含まれる部分的なサロゲートペアを見つけることがあるため、予期しない結果が返されることがあります。  
  
-   **fn: concat**。 ただし、部分的なサロゲートペアが値として渡された場合、 **concat**では正しくないサロゲートペアまたは部分的なサロゲートペアが生成されます。  
  
-   比較演算子と**order by**句。 比較演算子には、 \<+、、 \<>、=、>`eq`= `lt`、 `gt`、 `le`、、 `ge`、およびがあります。  
  
#### <a name="distributed-query-calls-to-a-system-procedure"></a>システムプロシージャに対する分散クエリ呼び出し  
 `OPENQUERY` を通じた一部のシステム プロシージャへの分散クエリ呼び出しは、[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] から別のサーバーへの呼び出しである場合に失敗します。 これは、[!INCLUDE[ssDE](../includes/ssde-md.md)]がプロシージャのメタデータを検出できない場合に発生します。 たとえば、`SELECT * FROM OPENQUERY(..., 'EXEC xp_loginfo')` のようにします。  
  
#### <a name="isolation-level-and-sp_reset_connection"></a>分離レベルと sp_reset_connection  
 接続の分離レベルは、クライアント ドライバーによって次のように処理されます。  
  
-   すべてのネイティブのドライバー (SNAC、MDAC、ODBC) では、sp_reset_connection において (アプリケーション設定に基づいて) 分離レベルが設定されます。  
  
-   ADO.NET では、実際にはプールから取得する接続によって (かつアプリケーションが異なる分離レベルを使用するかに応じて)、ランダムな分離レベルが得られます。 ADO.NET のプールは、内部的かつ透過的に接続をリサイクルできます。プールから何が出てくるかを予測することはできません。  
  
-   JDBC Driver では、動作は ADO.NET と同じになります。  
  
     アプリケーションは、必要なものを取得するために接続を開いた後、常に明示的に分離レベルを設定する必要があります。  
  
     JDBC の接続はプールすることができます。そのため、アプリケーションがランダムな分離レベルを取得しても、それについて認識されていない場合があります。  
  
 下位互換性を保持するため、この新しい動作は TDS 7.4 以降の最近使用したクライアントに対してのみ適用されます。  
  
#### <a name="backward-compatibility"></a>Backward Compatibility  
 **新しい動作は互換性レベルに依存します**  
  
 次の関数と演算子は、互換性レベルが 110 以上の場合にのみ、上記の新しい動作を示します。  
  
-   **fn: contains が含まれて**います。  
  
-   **fn: concat**。  
  
-   比較演算子と**order by**句  
  
 **新しい動作は、関数の既定の名前空間 URI に依存します**  
  
 次の関数は、既定の名前空間 URI が最終的な推奨設定の名前空間に対応する場合にのみ、上記の[http://www.w3.org/2005/xpath-functions](http://www.w3.org/2005/xpath-functions)新しい動作を示しています。 互換性レベルが 110 以上の場合、既定では、[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] は既定の関数名前空間をこの名前空間にバインドします。 ただし、これらの関数は、この名前空間が互換性レベルにかかわらず使用される場合にのみ、新しい動作を示します。  
  
-   **fn: 文字列の長さ**  
  
-   **fn: substring**  
  
##  <a name="breaking-changes-in-sql-server-2008sql-server-2008r2"></a><a name="KJKatmai"></a>SQL Server 2008/SQL Server 2008R2 での重大な変更  
 このセクションでは、[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] で導入された重大な変更について説明します。 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] で導入された変更はありません。  
  
### <a name="collations"></a>照合順序  
  
|機能|説明|  
|-------------|-----------------|  
|新しい照合順序|[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] では、Windows Server 2008 が提供する照合順序に完全に対応する新しい照合順序が導入されています。 この 80 個の新しい照合順序は、言語面での精度が向上しており、*_100 というバージョン参照で示されます。 サーバーまたはデータベースに新しい照合順序を選択する場合は、古いクライアント ドライバーを使用するクライアントではその照合順序が認識されない可能性があることに注意してください。 照合順序が認識されないと、アプリケーションはエラーを返して失敗する場合があります。 次の解決策を検討してください。<br /><br /> クライアント オペレーティング システムをアップグレードして、基になるシステムの照合順序を更新する。<br /><br /> クライアントにデータベース クライアント ソフトウェアがインストールされている場合、データベース クライアント ソフトウェアにサービスの更新プログラムを適用する。<br /><br /> クライアントのコード ページにマップする既存の照合順序を選択する。|  
  
### <a name="common-language-runtime-clr"></a>共通言語ランタイム (CLR)  
  
|機能|説明|  
|-------------|-----------------|  
|CLR アセンブリ|データベースを [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] にアップグレードすると、新しいデータ型をサポートする `Microsoft.SqlServer.Types` アセンブリが自動的にインストールされます。 アップグレードアドバイザールールでは、名前が競合するユーザーの種類またはアセンブリが検出されます。 アップグレードアドバイザーは、競合しているアセンブリの名前を変更し、競合している型の名前を変更するか、コード内の2つの部分で構成される名前を使用して、既存のユーザーの種類を参照します。<br /><br /> データベースのアップグレードによって、競合する名前を持つユーザーアセンブリが検出されると、そのアセンブリの名前が自動的に変更され、データベースが問題のあるモードになります。<br /><br /> アップグレード時に競合する名前を持つユーザー型が検出された場合、特別な処理は実行されません。 アップグレード後は、古いユーザー型と新しいシステム型の両方が存在することになります。 ユーザー型は、2 つの部分から構成される名前を介してのみ使用できます。|  
|CLR アセンブリ|[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] では .NET Framework 3.5 SP1 がインストールされ、グローバル アセンブリ キャッシュ (GAC) 内のライブラリが更新されます。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] データベースにサポートされていないライブラリが登録されている場合、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] にアップグレードすると、[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] アプリケーションの動作が停止する可能性があります。 これは、GAC でライブラリを提供またはアップグレードしても [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 内でアセンブリが更新されないためです。 アセンブリが [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] データベースと GAC の両方に存在する場合、アセンブリの 2 つのコピーが完全に一致する必要があります。 一致しない場合、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] CLR 統合によってアセンブリが使用されたときにエラーが発生します。 詳細については、「[サポートされている .NET Framework ライブラリ](../relational-databases/clr-integration/database-objects/supported-net-framework-libraries.md)」を参照してください。<br /><br /> データベースをアップグレードした後、ALTER ASSEMBLY ステートメントを使用して、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] データベース内でアセンブリのコピーを提供またはアップグレードします。 詳細については、[サポート技術情報の記事 949080](https://go.microsoft.com/fwlink/?LinkId=154563)を参照してください。<br /><br /> サポートされていない .NET Framework ライブラリをアプリケーションで使用しているかどうかを検出するには、データベースで次のクエリを実行します。<br /><br /> `SELECT name FROM sys.assemblies WHERE clr_name LIKE '%publickeytoken=b03f5f7f11d50a3a,%';`|  
|CLR ルーチン|CLR のユーザー定義関数、ユーザー定義集計、またはユーザー定義型 (UDT) 内で権限借用を使用すると、[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] にアップグレードした後に、アプリケーションがエラー 6522 で失敗する可能性があります。 次のシナリオは、[!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] では成功しますが、[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] では失敗します。 それぞれのシナリオに解決策があります。<br /><br /> `nvarchar(max)`権限借用を使用する CLR ユーザー定義関数、ユーザー定義集計、または udt メソッドに、型、 `varchar(max)` `varbinary(max)` `ntext` `text`、、、、 `image`、または大きな udt のパラメーターがあり、このメソッドに**dataaccesskind. Read**属性がありません。 この問題を解決するには、メソッドに**Dataaccesskind. Read**属性を追加し、アセンブリを再コンパイルして、ルーチンとアセンブリを再配置します。<br /><br /> 権限借用を実行する**Init**メソッドを持つ CLR テーブル値関数。 この問題を解決するには、メソッドに**Dataaccesskind. Read**属性を追加し、アセンブリを再コンパイルして、ルーチンとアセンブリを再配置します。<br /><br /> 権限借用を実行する**Fillrow**メソッドを持つ CLR テーブル値関数。 この問題を解決するには、 **Fillrow**メソッドから権限借用を削除します。 **Fillrow**メソッドを使用して外部リソースにアクセスしないでください。 代わりに、 **Init**メソッドから外部リソースにアクセスします。|  
  
### <a name="dynamic-management-views"></a>動的管理ビュー  
  
|表示|説明|  
|----------|-----------------|  
|sys.dm_os_sys_info|cpu_ticks_in_ms 列と sqlserver_start_time_cpu_ticks 列を削除しました。|  
|dm_exec_query_resource_semaphoressys。 dm_exec_query_memory_grants|[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] では、resource_semaphore_id 列は一意な ID ではありません。 この変更は、クエリの実行のトラブルシューティングに影響する可能性があります。 詳細については、「 [sys. dm_exec_query_resource_semaphores &#40;transact-sql&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-resource-semaphores-transact-sql)」を参照してください。|  
  
### <a name="errors-and-events"></a>エラーとイベント  
  
|機能|説明|  
|-------------|-----------------|  
|ログイン エラー|[!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] では、Windows 認証のみを使用するように構成されたサーバーに接続する際に SQL ログインを使用すると、エラー 18452 が返されます。 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] では、代わりに、エラー 18456 が返されます。|  
  
### <a name="showplan"></a>Showplan  
  
|機能|説明|  
|-------------|-----------------|  
|プラン表示の XML スキーマ|新しい**SeekPredicateNew**要素が Showplan XML スキーマに追加され、それを囲む xsd シーケンス (**SqlPredicatesType**) が** \<xsd: choice>** item に変換されます。 1つ以上の**Seekpredicate**要素の代わりに、Showplan XML に1つ以上の**SeekPredicateNew**要素が表示されるようになりました。 この 2 つの要素を同時に指定することはできません。 **Seekpredicate**は、旧バージョンとの互換性のために Showplan XML スキーマで保持されます。ただし、で[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]作成されたクエリプランには、 **SeekPredicateNew**要素が含まれている場合があります。 ノード Showplan Xml/BatchSequence/Batch/ステートメント/StmtSimple/QueryPlan/RelOp/IndexScan/Seekpredicate からの**seekpredicate**子のみを取得するアプリケーションは、 **seekpredicate**要素が存在しない場合に失敗することがあります。 このノードの**Seekpredicate**要素または**SeekPredicateNew**要素のいずれかを想定するようにアプリケーションを書き直してください。 詳細については、「」を参照してください。|  
|プラン表示の XML スキーマ|新しい**Indexkind**属性が Showplan XML スキーマの**ObjectType**複合型に追加されます。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] プランを [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] スキーマに対して厳密に検証するアプリケーションは失敗します。|  
  
### <a name="transact-sql"></a>Transact-SQL  
  
|機能|説明|  
|-------------|-----------------|  
|ALTER_AUTHORIZATION_DATABASE DDL イベント|で[!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]は、ddl イベント ALTER_AUTHORIZATION_DATABASE が発生すると、データ定義言語 (DDL) 操作でセキュリティ保護可能なエンティティ型がオブジェクトである場合に、このイベントの**ObjectType**要素に値 ' object ' が返されます。 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] では、実際の種類 (たとえば 'table' や 'function') が返されます。|  
|CONVERT|CONVERT 関数に無効なスタイルが渡されると、変換の種類がバイナリから文字、または文字からバイナリの場合にエラーが返されます。 以前のバージョンの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] では、バイナリから文字への変換および文字からバイナリへの変換の既定のスタイルに無効なスタイルが設定されます。|  
|アセンブリに対する EXECUTE の GRANT/DENY/REVOKE|アセンブリに対する EXECUTE 権限の許可、拒否、および取り消しを行うことはできません。 この権限を設定しても効果がなく、エラーが発生します。 代わりに、アセンブリ メソッドを参照するストアド プロシージャまたは関数に対して EXECUTE 権限の許可、拒否、および取り消しを行ってください。|  
|システム型に対する GRANT/DENY/REVOKE 権限|システム型に対する権限の許可、拒否、および取り消しを行うことはできません。 以前のバージョンの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] では、このステートメントは正常に実行されますが、効果はありません。 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] では、エラーが返されます。|  
|GROUP BY|GROUP BY 句では、GROUP BY リストに使用される式にサブクエリを含めることはできません。 以前のバージョンの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] では、この処理は可能でした。 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] では、エラー 144 が返されます。<br /><br /> たとえば、次のコードは、SQL Server 2005 では正常に実行されますが、SQL Server 2008 では実行に失敗します。<br /><br /> `DECLARE @Test TABLE(a int NOT NULL);` <br /> `INSERT INTO @Test SELECT 1 union ALL SELECT 2;` <br /> `SELECT COUNT(*)` <br /> `FROM @Test` <br /> `GROUP BY CASE WHEN a IN (SELECT t.a FROM @Test AS t)` <br /> `THEN 1 ELSE 0` <br /> `END;`|  
|OUTPUT 句|非決定的な動作を防ぐために、ビューまたはインライン テーブル値関数から返される列が次のいずれかの方法で定義されている場合、OUTPUT 句ではその列を参照できません。<br /><br /> サブクエリ。<br /><br /> ユーザーまたはシステムデータへのアクセスを実行するユーザー定義関数、またはこのようなアクセスを実行することを前提としています。<br /><br /> ユーザー データまたはシステム データにアクセスするユーザー定義関数を定義に含む計算列<br /><br /> <br /><br /> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] が OUTPUT 句でそのような列を検出すると、エラー 4186 が発生します。 詳細については、「 [MSSQLSERVER_4186](../relational-databases/errors-events/mssqlserver-4186-database-engine-error.md)」を参照してください。|  
|OUTPUT INTO 句|OUTPUT INTO 句の対象のテーブルに有効なトリガーを指定することはできません。|  
|precompute rank サーバー レベル オプション|このオプションは、[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] ではサポートされていません。 この機能を現在使用しているアプリケーションはできるだけ早く変更してください。|  
|READPAST テーブル ヒント|スナップショット分離で READPAST ヒントを指定することはできません。<br /><br /> READ_COMMITED_SNAPSHOT データベース オプションまたは ALLOW_SNAPSHOT_ISOLATION データベース オプションのいずれかが ON に設定されている場合、READPAST ヒントは無視されます。 ただし、READPAST ヒントを READCOMMITTEDLOCK と組み合わせた場合、READPAST の動作は READCOMMITTED ヒントをブロックするのと同じになります。|  
|sp_helpuser|Sp_helpuser ストアドプロシージャの結果セットに返される次の列名が変更されました。<br /><br /> GroupName は次のようになりました。<br />                            RoleName<br /><br /> Group_name は次のようになります。<br />                            Role_name<br /><br /> Group_id は次のようになります。<br />                            Role_id<br /><br /> Users_in_group は次のようになります。<br />                            Users_in_role|  
|透過的なデータ暗号化|透過的なデータ暗号化 (TDE) は I/O レベルで実行されます。そのため、ページ構造は、メモリ内では暗号化されず、ページがディスクに書き込まれるときだけ暗号化されます。 データベース ファイルとログ ファイルの両方が暗号化されます。 通常の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] メカニズムを使用せずに (たとえば、データ ファイルやログ ファイルを直接スキャンして) ページにアクセスするサードパーティのアプリケーションは、ファイル内のデータが暗号化されているため、データベースで TDE を使用すると失敗します。 このようなアプリケーションでは、Window Cryptographic API を使用すると、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 以外のデータの暗号化を解除するためのソリューションを開発できます。|  
  
### <a name="xquery"></a>XQuery  
  
|機能|説明|  
|-------------|-----------------|  
|Datetime のサポート|で[!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]は、、 `xs:time` `xs:date`、および`xs:dateTime`の各データ型には、タイムゾーンのサポートはありません。 タイム ゾーン データは UTC タイム ゾーンにマップされます。 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] では、標準に準拠した動作を提供するため、次のように変更されました。<br /><br /> タイム ゾーンを使用しない値の検証<br /><br /> タイム ゾーン指定の有無の保持<br /><br /> 内部ストレージ表現の変更<br /><br /> 格納された値の解決を増加<br /><br /> 負の年の使用禁止<br /><br /> <br /><br /> 注: 新しい型の値を考慮するようにアプリケーションと XQuery 式を変更します。|  
|XQuery 式と Xpath 式|で[!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]は、コロン (': ') で始まる XQuery 式または XPath 式のステップが許可されます。 たとえば、次のステートメントのパス式には、コロンで始まる名前テスト (`CTR02)`) が含まれています。<br /><br /> `SELECT FileContext.query('for n$ in //CTR return <C>{data )(n$/:CTR02)} </C>) AS Files FROM dbo.MyTable;`<br /><br /> この使用法は XML 標準に準拠していないため、[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] では許可されません。 エラー9341が返されます。 先頭のコロンを削除するか、名前テストにプレフィックスを指定してください (n$/CTR02 や n$/p1:CTR02 など)。|  
  
### <a name="connecting"></a>接続  
  
|機能|説明|  
|-------------|-----------------|  
|SSL を使用した [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client からの接続|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client を使用して接続するとき、以前は、緩和された検証により、サブジェクトに完全修飾ドメイン名 (FQDN) が指定されている証明書で "SERVER=shortname; FORCE ENCRYPTION=true" を使用するアプリケーションでも接続できましたが、 SQL Server 2008 R2 では、セキュリティ強化のために証明書で FQDN のサブジェクトが強制されるようになりました。 緩和された検証に依存しているアプリケーションでは次のいずれかの対処が必要になります。<br /><br /> 接続文字列で FQDN を使用する。<br /><br /> -接続文字列の SERVER キーワードがアプリケーションの外部で構成されている場合、このオプションではアプリケーションを再コンパイルする必要はありません。<br /><br /> -接続文字列がハードコードされているアプリケーションでは、このオプションは機能しません。<br /><br /> -ミラーサーバーが簡易名で応答するため、データベースミラーリングを使用するアプリケーションでは、このオプションは機能しません。|  
||shortname の別名を追加して FQDN にマップする。<br /><br /> -このオプションは、接続文字列がハードコードされているアプリケーションでも機能します。<br /><br /> -このオプションは、データベースミラーリングを使用するアプリケーションに対しては機能しません。これは、プロバイダーが受信したフェールオーバーパートナー名のエイリアスを参照しないためです。|  
||shortname に対して発行された証明書を使用する。<br /><br /> -このオプションは、すべてのアプリケーションで使用できます。|  

## <a name="breaking-changes-in-sql-server-2005"></a><a name="Yukon"></a>SQL Server 2005 での重大な変更  

[!INCLUDE[Archived documentation for very old versions of SQL Server](../includes/paragraph-content/previous-versions-archive-documentation-sql-server.md)]

## <a name="see-also"></a>参照  
 [SQL Server 2014 の非推奨のデータベースエンジン機能](deprecated-database-engine-features-in-sql-server-2016.md?view=sql-server-2014)   
 [SQL Server 2014 のデータベースエンジン機能の動作の変更](../../2014/database-engine/behavior-changes-to-database-engine-features-in-sql-server-2014.md?view=sql-server-2014)   
 [SQL Server 2014 で廃止されたデータベースエンジン機能](discontinued-database-engine-functionality-in-sql-server-2016.md?view=sql-server-2014)   
 [SQL Server データベース エンジンの旧バージョンとの互換性](sql-server-database-engine-backward-compatibility.md)   
 [ALTER DATABASE 互換性レベル &#40;TRANSACT-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)  
 [SQL Server 2014 の管理ツール機能における重大な変更](breaking-changes-to-management-tools-features-in-sql-server-2014.md?view=sql-server-2014)  
  

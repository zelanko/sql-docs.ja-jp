---
title: SQLServerDatabaseMetaData のメンバー |Microsoft ドキュメント
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
ms.assetid: 327ba0bc-438a-494c-b119-1cd4a096bb58
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d8552b0a4e59e1eed892dae11b37daa18e85288b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sqlserverdatabasemetadata-members"></a>SQLServerDatabaseMetaData のメンバー
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  次の表に、によって公開されるメンバー、 [SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)クラスです。  
  
## <a name="constructors"></a>コンス トラクター  
 [なし] :  
  
## <a name="fields"></a>フィールド  
 [なし] :  
  
## <a name="inherited-fields"></a>継承されたフィールド  
  
|名前|Description|  
|----------|-----------------|  
|java.sql.DatabaseMetaData|attributeNoNulls、attributeNullable、attributeNullableUnknown、bestRowNotPseudo、bestRowPseudo、bestRowSession、bestRowTemporary、bestRowTransaction、bestRowUnknown、columnNoNulls、columnNullable、columnNullableUnknown、importedKeyCascade、importedKeyInitiallyDeferred、importedKeyInitiallyImmediate、importedKeyNoAction、importedKeyNotDeferrable、importedKeyRestrict、importedKeySetDefault、importedKeySetNull、procedureColumnIn、procedureColumnInOut、procedureColumnOut、procedureColumnResult、procedureColumnReturn、procedureColumnUnknown、procedureNoNulls、procedureNoResult、procedureNullable、procedureNullableUnknown、procedureResultUnknown、procedureReturnsResult、sqlStateSQL、sqlStateSQL99、sqlStateXOpen、tableIndexClustered、tableIndexHashed、tableIndexOther、tableIndexStatistic、typeNoNulls、typeNullable、typeNullableUnknown、typePredBasic、typePredChar、typePredNone、typeSearchable、versionColumnNotPseudo、versionColumnPseudo、versionColumnUnknown|  
  
## <a name="methods"></a>メソッド  
  
|名前|Description|  
|----------|-----------------|  
|[allProceduresAreCallable](../../../connect/jdbc/reference/allproceduresarecallable-method-sqlserverdatabasemetadata.md)|現在のユーザーがによって返されるすべてのプロシージャを呼び出すアクセス許可を持っているかどうかを取得、 [getProcedures](../../../connect/jdbc/reference/getprocedures-method-sqlserverdatabasemetadata.md)メソッドです。|  
|[allTablesAreSelectable](../../../connect/jdbc/reference/alltablesareselectable-method-sqlserverdatabasemetadata.md)|現在のユーザーがによって返されるすべてのテーブルを使用するアクセス許可を持っているかどうかを取得、 [getTables](../../../connect/jdbc/reference/gettables-method-sqlserverdatabasemetadata.md) SELECT ステートメント内のメソッドです。|  
|[autoCommitFailureClosesAllResultSets](../../../connect/jdbc/reference/autocommitfailureclosesallresultsets-method-sqlserverdatabasemetadata.md)|自動コミットが有効である場合に例外が発生したとき、保持可能な結果セットも含め、開いているすべての結果セットを JDBC ドライバーで閉じるかどうかを示します。|  
|[dataDefinitionCausesTransactionCommit](../../../connect/jdbc/reference/datadefinitioncausestransactioncommit-method-sqlserverdatabasemetadata.md)|トランザクション内のデータ定義ステートメントがトランザクションを強制的にコミットさせるかどうかを取得します。|  
|[dataDefinitionIgnoredInTransactions](../../../connect/jdbc/reference/datadefinitionignoredintransactions-method-sqlserverdatabasemetadata.md)|データベースがトランザクション内のデータ定義ステートメントを無視するかどうかを取得します。|  
|[deletesAreDetected](../../../connect/jdbc/reference/deletesaredetected-method-sqlserverdatabasemetadata.md)|表示されている行を削除するかどうかを取得しますを呼び出すことによって検出できる、 [rowDeleted](../../../connect/jdbc/reference/rowdeleted-method-sqlserverresultset.md)のメソッド、 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)クラスです。|  
|[doesMaxRowSizeIncludeBlobs](../../../connect/jdbc/reference/doesmaxrowsizeincludeblobs-method-sqlserverdatabasemetadata.md)|取得の場合、戻り値の値かどうか、 [getMaxRowSize](../../../connect/jdbc/reference/getmaxrowsize-method-sqlserverdatabasemetadata.md)メソッドには、SQL データ型 LONGVARCHAR と LONGVARBINARY が含まれています。|  
|[GetAttributes](../../../connect/jdbc/reference/getattributes-method-sqlserverdatabasemetadata.md)|渡されたスキーマおよびカタログで使用できる、ユーザー定義型である渡された型の渡された属性の記述を取得します。|  
|[getBestRowIdentifier](../../../connect/jdbc/reference/getbestrowidentifier-method-sqlserverdatabasemetadata.md)|行を一意に識別する、テーブルの最適な列のセットの記述を取得します。|  
|[getCatalogs](../../../connect/jdbc/reference/getcatalogs-method-sqlserverdatabasemetadata.md)|接続されたサーバーで使用できるカタログ名を取得します。|  
|[getCatalogSeparator](../../../connect/jdbc/reference/getcatalogseparator-method-sqlserverdatabasemetadata.md)|取得、**文字列**カタログとテーブル名の間の区切り記号としてこのデータベースを使用します。|  
|[getCatalogTerm](../../../connect/jdbc/reference/getcatalogterm-method-sqlserverdatabasemetadata.md)|データベース ベンダーが "カタログ" の代わりに使用している用語を取得します。|  
|[getClientInfoProperties](../../../connect/jdbc/reference/getclientinfoproperties-method-sqlserverdatabasemetadata.md)|ドライバーがサポートしているクライアント情報のプロパティの一覧を取得します。|  
|[getColumnPrivileges](../../../connect/jdbc/reference/getcolumnprivileges-method-sqlserverdatabasemetadata.md)|テーブルの列に対するアクセス権の記述を取得します。|  
|[getColumns](../../../connect/jdbc/reference/getcolumns-method-sqlserverdatabasemetadata.md)|指定されたカタログで使用できるテーブル列の記述を取得します。|  
|[getConnection](../../../connect/jdbc/reference/getconnection-method-sqlserverdatabasemetadata.md)|メタデータ オブジェクトを生成した接続を取得します。|  
|[getCrossReference](../../../connect/jdbc/reference/getcrossreference-method-sqlserverdatabasemetadata.md)|主キー テーブルの主キー列を参照する外部キー テーブルの外部キー列の記述を取得します。|  
|[getDatabaseMajorVersion](../../../connect/jdbc/reference/getdatabasemajorversion-method-sqlserverdatabasemetadata.md)|基本データベースのメジャー バージョン番号を取得します。|  
|[getDatabaseMinorVersion](../../../connect/jdbc/reference/getdatabaseminorversion-method-sqlserverdatabasemetadata.md)|基本データベースのマイナー バージョン番号を取得します。|  
|[getDatabaseProductName](../../../connect/jdbc/reference/getdatabaseproductname-method-sqlserverdatabasemetadata.md)|データベース製品の名前を取得します。|  
|[getDatabaseProductVersion](../../../connect/jdbc/reference/getdatabaseproductversion-method-sqlserverdatabasemetadata.md)|データベース製品のバージョン番号を取得します。|  
|[getDefaultTransactionIsolation](../../../connect/jdbc/reference/getdefaulttransactionisolation-method-sqlserverdatabasemetadata.md)|データベースの既定のトランザクション分離レベルを取得します。|  
|[getDriverMajorVersion](../../../connect/jdbc/reference/getdrivermajorversion-method-sqlserverdatabasemetadata.md)|JDBC ドライバーのメジャー バージョン番号を取得します。|  
|[getDriverMinorVersion](../../../connect/jdbc/reference/getdriverminorversion-method-sqlserverdatabasemetadata.md)|JDBC ドライバーのマイナー バージョン番号を取得します。|  
|[getDriverName](../../../connect/jdbc/reference/getdrivername-method-sqlserverdatabasemetadata.md)|JDBC ドライバーの名前を取得します。|  
|[getDriverVersion](../../../connect/jdbc/reference/getdriverversion-method-sqlserverdatabasemetadata.md)|JDBC ドライバーのバージョン番号を取得します。|  
|[getExportedKeys](../../../connect/jdbc/reference/getexportedkeys-method-sqlserverdatabasemetadata.md)|渡されたテーブルの主キー列を参照する外部キー列の記述を取得します。|  
|[getExtraNameCharacters](../../../connect/jdbc/reference/getextranamecharacters-method-sqlserverdatabasemetadata.md)|A ~ z、A ~ Z、0 ~ 9、および _ 以外、たとえば、囲まれていない識別子名に使用できるすべての余分な文字を取得します。|  
|[getFunctions](../../../connect/jdbc/reference/getfunctions-method-sqlserverdatabasemetadata.md)|システム関数およびユーザー関数の記述を取得します。|  
|[getFunctionColumns](../../../connect/jdbc/reference/getfunctioncolumns-method-sqlserverdatabasemetadata.md)|指定されたカタログのシステム関数またはユーザー関数のパラメーターと戻り値の型に関する記述を取得します。|  
|[getIdentifierQuoteString](../../../connect/jdbc/reference/getidentifierquotestring-method-sqlserverdatabasemetadata.md)|取得、**文字列**SQL 識別子を引用するために使用されます。|  
|[getImportedKeys](../../../connect/jdbc/reference/getimportedkeys-method-sqlserverdatabasemetadata.md)|テーブルの外部キー列によって参照される、主キー列の記述を取得します。|  
|[getIndexInfo](../../../connect/jdbc/reference/getindexinfo-method-sqlserverdatabasemetadata.md)|渡されたテーブルのインデックスと統計情報の記述を取得します。|  
|[getJDBCMajorVersion](../../../connect/jdbc/reference/getjdbcmajorversion-method-sqlserverdatabasemetadata.md)|ドライバーの JDBC メジャー バージョン番号を取得します。|  
|[getJDBCMinorVersion](../../../connect/jdbc/reference/getjdbcminorversion-method-sqlserverdatabasemetadata.md)|ドライバーの JDBC マイナー バージョン番号を取得します。|  
|[getMaxBinaryLiteralLength](../../../connect/jdbc/reference/getmaxbinaryliterallength-method-sqlserverdatabasemetadata.md)|データベースでインラインのバイナリ リテラルに許容される 16 進文字の最大数を取得します。|  
|[getMaxCatalogNameLength](../../../connect/jdbc/reference/getmaxcatalognamelength-method-sqlserverdatabasemetadata.md)|データベースでカタログ名に許容される最大文字数を取得します。|  
|[getMaxCharLiteralLength](../../../connect/jdbc/reference/getmaxcharliterallength-method-sqlserverdatabasemetadata.md)|データベースで文字リテラルに許容される最大文字数を取得します。|  
|[getMaxColumnNameLength](../../../connect/jdbc/reference/getmaxcolumnnamelength-method-sqlserverdatabasemetadata.md)|データベースで列名に許容される最大文字数を取得します。|  
|[getMaxColumnsInGroupBy](../../../connect/jdbc/reference/getmaxcolumnsingroupby-method-sqlserverdatabasemetadata.md)|データベースで GROUP BY 句に許容される最大の列数を取得します。|  
|[getMaxColumnsInIndex](../../../connect/jdbc/reference/getmaxcolumnsinindex-method-sqlserverdatabasemetadata.md)|データベースでインデックスに許容される最大の列数を取得します。|  
|[getMaxColumnsInOrderBy](../../../connect/jdbc/reference/getmaxcolumnsinorderby-method-sqlserverdatabasemetadata.md)|データベースで ORDER BY 句に許容される最大の列数を取得します。|  
|[getMaxColumnsInSelect](../../../connect/jdbc/reference/getmaxcolumnsinselect-method-sqlserverdatabasemetadata.md)|データベースで SELECT リストに許容される最大の列数を取得します。|  
|[getMaxColumnsInTable](../../../connect/jdbc/reference/getmaxcolumnsintable-method-sqlserverdatabasemetadata.md)|データベースでテーブルに許容される最大の列数を取得します。|  
|[getMaxConnections](../../../connect/jdbc/reference/getmaxconnections-method-sqlserverdatabasemetadata.md)|データベースへの可能な同時接続の最大数を取得します。|  
|[getMaxCursorNameLength](../../../connect/jdbc/reference/getmaxcursornamelength-method-sqlserverdatabasemetadata.md)|データベースで許容されるカーソル名の最大文字数を取得します。|  
|[getMaxIndexLength](../../../connect/jdbc/reference/getmaxindexlength-method-sqlserverdatabasemetadata.md)|データベースで、インデックスのすべての部分を含めて、インデックスに許容される最大バイト数を取得します。|  
|[getMaxProcedureNameLength](../../../connect/jdbc/reference/getmaxprocedurenamelength-method-sqlserverdatabasemetadata.md)|データベースでプロシージャ名に許容される最大文字数を取得します。|  
|[getMaxRowSize](../../../connect/jdbc/reference/getmaxrowsize-method-sqlserverdatabasemetadata.md)|データベースで許容される 1 行の最大バイト数を取得します。|  
|[getMaxSchemaNameLength](../../../connect/jdbc/reference/getmaxschemanamelength-method-sqlserverdatabasemetadata.md)|データベースでテーブル名に許容される最大文字数を取得します。|  
|[getMaxStatementLength](../../../connect/jdbc/reference/getmaxstatementlength-method-sqlserverdatabasemetadata.md)|このデータベースで SQL ステートメントに許容される文字の最大数を取得します。|  
|[getMaxStatements](../../../connect/jdbc/reference/getmaxstatements-method-sqlserverdatabasemetadata.md)|データベースの同時に開くことができるアクティブなステートメントの最大数を取得します。|  
|[getMaxTableNameLength](../../../connect/jdbc/reference/getmaxtablenamelength-method-sqlserverdatabasemetadata.md)|このデータベースでテーブル名に許容される文字の最大数を取得します。|  
|[getMaxTablesInSelect](../../../connect/jdbc/reference/getmaxtablesinselect-method-sqlserverdatabasemetadata.md)|このデータベースで SELECT ステートメントに許容されるテーブルの最大数を取得します。|  
|[getMaxUserNameLength](../../../connect/jdbc/reference/getmaxusernamelength-method-sqlserverdatabasemetadata.md)|データベースでユーザー名に許容される最大文字数を取得します。|  
|[getNumericFunctions](../../../connect/jdbc/reference/getnumericfunctions-method-sqlserverdatabasemetadata.md)|データベースで使用できる、数学関数のコンマ区切りの一覧を取得します。|  
|[getPrimaryKeys](../../../connect/jdbc/reference/getprimarykeys-method-sqlserverdatabasemetadata.md)|渡されたテーブルの主キー列の記述を取得します。|  
|[getProcedureColumns](../../../connect/jdbc/reference/getprocedurecolumns-method-sqlserverdatabasemetadata.md)|ストアド プロシージャのパラメーターと結果列の記述を取得します。|  
|[getProcedures](../../../connect/jdbc/reference/getprocedures-method-sqlserverdatabasemetadata.md)|渡されたカタログ、スキーマ、またはストアド プロシージャ名のパターンで使用可能なストアド プロシージャの記述を取得します。|  
|[getProcedureTerm](../../../connect/jdbc/reference/getprocedureterm-method-sqlserverdatabasemetadata.md)|データベースで "プロシージャ" の代わりに使用している用語を取得します。|  
|[getResultSetHoldability](../../../connect/jdbc/reference/getresultsetholdability-method-sqlserverdatabasemetadata.md)|データベースに対する結果セットの既定の保持機能を取得します。|  
|[getRowIdLifetime](../../../connect/jdbc/reference/getrowidlifetime-method-sqlserverdatabasemetadata.md)|SQL RowId データ型がサポートされているかどうかを示す状態を返します。 サポートされている場合は、RowId オブジェクトの有効期間を返します。|  
|[getSchemas](../../../connect/jdbc/reference/getschemas-method.md)|現在のデータベースで使用できるスキーマ名を取得します。|  
|[getSchemaTerm](../../../connect/jdbc/reference/getschematerm-method-sqlserverdatabasemetadata.md)|データベースで "スキーマ" の代わりに使用している用語を取得します。|  
|[getSearchStringEscape](../../../connect/jdbc/reference/getsearchstringescape-method-sqlserverdatabasemetadata.md)|取得、**文字列**ワイルドカード文字をエスケープするために使用できます。|  
|[getSQLKeywords](../../../connect/jdbc/reference/getsqlkeywords-method-sqlserverdatabasemetadata.md)|データベースの SQL キーワードであって、SQL92 キーワードではない、すべてのキーワードのコンマ区切りの一覧を取得します。|  
|[getSQLStateType](../../../connect/jdbc/reference/getsqlstatetype-method-sqlserverdatabasemetadata.md)|SQLException.getSQLState メソッドによって返される SQLSTATE が X であるかどうかを示す開きます (今すぐと呼ばれる Open Group)、SQL CLI、SQL99 (JDBC 3.0)、sql:2003 (JDBC 4.0)。|  
|[getStringFunctions](../../../connect/jdbc/reference/getstringfunctions-method-sqlserverdatabasemetadata.md)|コンマ区切りの一覧を取得**文字列**データベースで使用される関数。|  
|[getSuperTables](../../../connect/jdbc/reference/getsupertables-method-sqlserverdatabasemetadata.md)|データベース内の特定のスキーマで定義されたテーブルの階層の記述を取得します。|  
|[getSuperTypes](../../../connect/jdbc/reference/getsupertypes-method-sqlserverdatabasemetadata.md)|データベース内の特定のスキーマで定義されたユーザー定義型の階層の記述を取得します。|  
|[getSystemFunctions](../../../connect/jdbc/reference/getsystemfunctions-method-sqlserverdatabasemetadata.md)|データベースで使用できる、システム関数のコンマ区切りの一覧を取得します。|  
|[getTablePrivileges](../../../connect/jdbc/reference/gettableprivileges-method-sqlserverdatabasemetadata.md)|渡されたカタログ、スキーマ、またはテーブル名のパターンで使用可能な、各テーブルのアクセス権の記述を取得します。|  
|[getTables](../../../connect/jdbc/reference/gettables-method-sqlserverdatabasemetadata.md)|渡されたカタログ、スキーマ、またはテーブル名のパターンで使用可能なテーブルの記述を取得します。|  
|[getTableTypes](../../../connect/jdbc/reference/gettabletypes-method-sqlserverdatabasemetadata.md)|現在のデータベースで使用できるテーブルの型を取得します。|  
|[getTimeDateFunctions](../../../connect/jdbc/reference/gettimedatefunctions-method-sqlserverdatabasemetadata.md)|データベースで使用可能な時間関数および日付関数のコンマ区切りの一覧を取得します。|  
|[GetTypeInfo](../../../connect/jdbc/reference/gettypeinfo-method-sqlserverdatabasemetadata.md)|現在のデータベースによってサポートされる、すべての標準 SQL 型に関する記述を取得します。|  
|[getUDTs](../../../connect/jdbc/reference/getudts-method-sqlserverdatabasemetadata.md)|特定のスキーマで定義されているユーザー定義型の記述を取得します。|  
|[getURL](../../../connect/jdbc/reference/geturl-method-sqlserverdatabasemetadata.md)|データベースの URL を取得します。|  
|[GetUserName](../../../connect/jdbc/reference/getusername-method-sqlserverdatabasemetadata.md)|データベースに対する既知のユーザー名を取得します。|  
|[getVersionColumns](../../../connect/jdbc/reference/getversioncolumns-method-sqlserverdatabasemetadata.md)|行の任意の値が更新された場合に自動的に更新されるテーブルの列の記述を取得します。|  
|[insertsAreDetected](../../../connect/jdbc/reference/insertsaredetected-method-sqlserverdatabasemetadata.md)|メソッドを呼び出すことで可視の行を挿入するを検出できるかどうかを取得[rowInserted](../../../connect/jdbc/reference/rowinserted-method-sqlserverresultset.md)のメソッド、 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)クラスです。|  
|[isCatalogAtStart](../../../connect/jdbc/reference/iscatalogatstart-method-sqlserverdatabasemetadata.md)|カタログが完全修飾テーブル名の先頭に現れるかどうかを取得します。|  
|[isReadOnly](../../../connect/jdbc/reference/isreadonly-method-sqlserverdatabasemetadata.md)|データベースが読み取り専用モードであるかどうかを取得します。|  
|[locatorsUpdateCopy](../../../connect/jdbc/reference/locatorsupdatecopy-method-sqlserverdatabasemetadata.md)|LOB に対する更新が、コピーに対して行われたか、LOB に直接行われたかを示します。|  
|[nullPlusNonNullIsNull](../../../connect/jdbc/reference/nullplusnonnullisnull-method-sqlserverdatabasemetadata.md)|NULL 値と NULL 以外の値の連結を NULL とすることを、データベースがサポートするかどうかを示します。|  
|[nullsAreSortedAtEnd](../../../connect/jdbc/reference/nullsaresortedatend-method-sqlserverdatabasemetadata.md)|並べ替え順序に関係なく、最後に null 値を並べ替えるかどうかを取得します。|  
|[nullsAreSortedAtStart](../../../connect/jdbc/reference/nullsaresortedatstart-method-sqlserverdatabasemetadata.md)|並べ替え順序に関係なく、最初に null 値を並べ替えるかどうかを取得します。|  
|[nullsAreSortedHigh](../../../connect/jdbc/reference/nullsaresortedhigh-method-sqlserverdatabasemetadata.md)|NULL 値が上位に並べ替えられるかどうかを取得します。|  
|[nullsAreSortedLow](../../../connect/jdbc/reference/nullsaresortedlow-method-sqlserverdatabasemetadata.md)|NULL 値が下位に並べ替えられるかどうかを取得します。|  
|[othersDeletesAreVisible](../../../connect/jdbc/reference/othersdeletesarevisible-method-sqlserverdatabasemetadata.md)|他で行われた削除が可視かどうかを取得します。|  
|[othersInsertsAreVisible](../../../connect/jdbc/reference/othersinsertsarevisible-method-sqlserverdatabasemetadata.md)|他で行われた挿入が可視かどうかを取得します。|  
|[othersUpdatesAreVisible](../../../connect/jdbc/reference/othersupdatesarevisible-method-sqlserverdatabasemetadata.md)|他で行われた更新が可視かどうかを取得します。|  
|[ownDeletesAreVisible](../../../connect/jdbc/reference/owndeletesarevisible-method-sqlserverdatabasemetadata.md)|結果セット自体の削除が可視であるかどうかを取得します。|  
|[ownInsertsAreVisible](../../../connect/jdbc/reference/owninsertsarevisible-method-sqlserverdatabasemetadata.md)|結果セット自体の挿入が可視であるかどうかを取得します。|  
|[ownUpdatesAreVisible](../../../connect/jdbc/reference/ownupdatesarevisible-method-sqlserverdatabasemetadata.md)|結果セット自体の更新が可視であるかどうかを取得します。|  
|[storesLowerCaseIdentifiers](../../../connect/jdbc/reference/storeslowercaseidentifiers-method-sqlserverdatabasemetadata.md)|引用符で囲まれていない大文字と小文字が混在する SQL 識別子を、データベースが大文字と小文字を区別しないで扱うかどうか、およびそれらの識別子を小文字で格納するかどうかを取得します。|  
|[storesLowerCaseQuotedIdentifiers](../../../connect/jdbc/reference/storeslowercasequotedidentifiers-method-sqlserverdatabasemetadata.md)|引用符で囲まれた大文字と小文字が混在する SQL 識別子を、データベースが大文字と小文字を区別しないで扱うかどうか、およびそれらの識別子を小文字で格納するかどうかを取得します。|  
|[storesMixedCaseIdentifiers](../../../connect/jdbc/reference/storesmixedcaseidentifiers-method-sqlserverdatabasemetadata.md)|引用符で囲まれていない大文字と小文字が混在する SQL 識別子を、データベースが大文字と小文字を区別しないで扱うかどうか、およびそれらの識別子を大文字小文字混在で格納するかどうかを取得します。|  
|[storesMixedCaseQuotedIdentifiers](../../../connect/jdbc/reference/storesmixedcasequotedidentifiers-method-sqlserverdatabasemetadata.md)|引用符で囲まれた大文字と小文字が混在する SQL 識別子を、データベースが大文字と小文字を区別しないで扱うかどうか、およびそれらの識別子を大文字小文字混在で格納するかどうかを取得します。|  
|[storesUpperCaseIdentifiers](../../../connect/jdbc/reference/storesuppercaseidentifiers-method-sqlserverdatabasemetadata.md)|引用符で囲まれていない大文字と小文字が混在する SQL 識別子を、データベースが大文字と小文字を区別しないで扱うかどうか、およびそれらの識別子を大文字で格納するかどうかを取得します。|  
|[storesUpperCaseQuotedIdentifiers](../../../connect/jdbc/reference/storesuppercasequotedidentifiers-method-sqlserverdatabasemetadata.md)|引用符で囲まれた大文字と小文字が混在する SQL 識別子を、データベースが大文字と小文字を区別しないで扱うかどうか、およびそれらの識別子を大文字で格納するかどうかを取得します。|  
|[supportsAlterTableWithAddColumn](../../../connect/jdbc/reference/supportsaltertablewithaddcolumn-method-sqlserverdatabasemetadata.md)|データベースが列の追加で ALTER TABLE をサポートするかどうかを取得します。|  
|[supportsAlterTableWithDropColumn](../../../connect/jdbc/reference/supportsaltertablewithdropcolumn-method-sqlserverdatabasemetadata.md)|データベースが列の削除で ALTER TABLE をサポートするかどうかを取得します。|  
|[supportsANSI92EntryLevelSQL](../../../connect/jdbc/reference/supportsansi92entrylevelsql-method-sqlserverdatabasemetadata.md)|データベースが ANSI92 エントリ レベルの SQL 文法をサポートするかどうかを取得します。|  
|[supportsANSI92FullSQL](../../../connect/jdbc/reference/supportsansi92fullsql-method-sqlserverdatabasemetadata.md)|データベースが ANSI92 完全レベルの SQL 文法をサポートするかどうかを取得します。|  
|[supportsANSI92IntermediateSQL](../../../connect/jdbc/reference/supportsansi92intermediatesql-method-sqlserverdatabasemetadata.md)|データベースが ANSI92 の中間レベル SQL 文法をサポートするかどうかを取得します。|  
|[supportsBatchUpdates](../../../connect/jdbc/reference/supportsbatchupdates-method-sqlserverdatabasemetadata.md)|データベースがバッチ更新をサポートするかどうかを取得します。|  
|[supportsCatalogsInDataManipulation](../../../connect/jdbc/reference/supportscatalogsindatamanipulation-method-sqlserverdatabasemetadata.md)|データ操作ステートメントでカタログ名を使用できるかどうかを取得します。|  
|[supportsCatalogsInIndexDefinitions](../../../connect/jdbc/reference/supportscatalogsinindexdefinitions-method-sqlserverdatabasemetadata.md)|インデックス定義ステートメントでカタログ名を使用できるかどうかを取得します。|  
|[supportsCatalogsInPrivilegeDefinitions](../../../connect/jdbc/reference/supportscatalogsinprivilegedefinitions-method-sqlserverdatabasemetadata.md)|特権定義ステートメントでカタログ名を使用できるかどうかを取得します。|  
|[supportsCatalogsInProcedureCalls](../../../connect/jdbc/reference/supportscatalogsinprocedurecalls-method-sqlserverdatabasemetadata.md)|プロシージャ呼び出しステートメントでカタログ名を使用できるかどうかを取得します。|  
|[supportsCatalogsInTableDefinitions](../../../connect/jdbc/reference/supportscatalogsintabledefinitions-method-sqlserverdatabasemetadata.md)|テーブル定義ステートメントでカタログ名を使用できるかどうかを取得します。|  
|[supportsColumnAliasing](../../../connect/jdbc/reference/supportscolumnaliasing-method-sqlserverdatabasemetadata.md)|データベースが列の別名をサポートするかどうかを取得します。|  
|[supportsConvert](../../../connect/jdbc/reference/supportsconvert-method-sqlserverdatabasemetadata.md)|データベースが SQL 型間の CONVERT 関数をサポートするかどうかを取得します。|  
|[supportsCoreSQLGrammar](../../../connect/jdbc/reference/supportscoresqlgrammar-method-sqlserverdatabasemetadata.md)|データベースが ODBC Core SQL 文法をサポートするかどうかを取得します。|  
|[supportsCorrelatedSubqueries](../../../connect/jdbc/reference/supportscorrelatedsubqueries-method-sqlserverdatabasemetadata.md)|データベースが、相関サブクエリをサポートするかどうかを取得します。|  
|[supportsDataDefinitionAndDataManipulationTransactions](../../../connect/jdbc/reference/supportsdatadefinitionanddatamanipulationtransactions-method.md)|データベースがトランザクション内のデータ定義ステートメントとデータ操作ステートメントの両方をサポートするかどうかを取得します。|  
|[supportsDataManipulationTransactionsOnly](../../../connect/jdbc/reference/supportsdatamanipulationtransactionsonly-method-sqlserverdatabasemetadata.md)|データベースがトランザクション内でデータ操作ステートメントのみをサポートするかどうかを取得します。|  
|[supportsDifferentTableCorrelationNames](../../../connect/jdbc/reference/supportsdifferenttablecorrelationnames-method-sqlserverdatabasemetadata.md)|テーブルの相関名がサポートされる場合に、それらの名前をテーブルの名前と異なるものにするという制限があるかどうかを取得します。|  
|[supportsExpressionsInOrderBy](../../../connect/jdbc/reference/supportsexpressionsinorderby-method-sqlserverdatabasemetadata.md)|データベースが、ORDER BY リストで式をサポートするかどうかを取得します。|  
|[supportsExtendedSQLGrammar](../../../connect/jdbc/reference/supportsextendedsqlgrammar-method-sqlserverdatabasemetadata.md)|データベースが ODBC 拡張 SQL 文法をサポートするかどうかを取得します。|  
|[supportsFullOuterJoins](../../../connect/jdbc/reference/supportsfullouterjoins-method-sqlserverdatabasemetadata.md)|データベースが完全に入れ子状態になった外部結合をサポートするかどうかを取得します。|  
|[supportsGetGeneratedKeys](../../../connect/jdbc/reference/supportsgetgeneratedkeys-method-sqlserverdatabasemetadata.md)|ステートメントの実行後に自動生成キーを取得できるかどうかを取得します。|  
|[supportsGroupBy](../../../connect/jdbc/reference/supportsgroupby-method-sqlserverdatabasemetadata.md)|データベースが GROUP BY 句をサポートするかどうかを取得します。|  
|[supportsGroupByBeyondSelect](../../../connect/jdbc/reference/supportsgroupbybeyondselect-method-sqlserverdatabasemetadata.md)|データベースが GROUP BY 句で SELECT ステートメント内の列のすべてが含まれますが、GROUP BY 句で SELECT ステートメントに含まれていない列の使用をサポートするかどうかを取得します。|  
|[supportsGroupByUnrelated](../../../connect/jdbc/reference/supportsgroupbyunrelated-method-sqlserverdatabasemetadata.md)|データベースが GROUP BY 句で SELECT ステートメントにない列の使用をサポートするかどうかを取得します。|  
|[supportsIntegrityEnhancementFacility](../../../connect/jdbc/reference/supportsintegrityenhancementfacility-method-sqlserverdatabasemetadata.md)|データベースが SQL Integrity Enhancement Facility をサポートするかどうかを取得します。|  
|[supportsLikeEscapeClause](../../../connect/jdbc/reference/supportslikeescapeclause-method-sqlserverdatabasemetadata.md)|データベースが LIKE エスケープ句の指定をサポートするかどうかを取得します。|  
|[supportsLimitedOuterJoins](../../../connect/jdbc/reference/supportslimitedouterjoins-method-sqlserverdatabasemetadata.md)|データベースが、外部結合を制限付きでサポートするかどうかを取得します。|  
|[supportsMinimumSQLGrammar](../../../connect/jdbc/reference/supportsminimumsqlgrammar-method-sqlserverdatabasemetadata.md)|データベースが ODBC Minimum SQL 文法をサポートするかどうかを取得します。|  
|[supportsMixedCaseIdentifiers](../../../connect/jdbc/reference/supportsmixedcaseidentifiers-method-sqlserverdatabasemetadata.md)|引用符で囲まれていない大文字と小文字が混在する SQL 識別子を、データベースが大文字と小文字を区別しないで扱うかどうか、およびそれらの識別子を大文字小文字混在で格納するかどうかを取得します。|  
|[supportsMixedCaseQuotedIdentifiers](../../../connect/jdbc/reference/supportsmixedcasequotedidentifiers-method-sqlserverdatabasemetadata.md)|引用符で囲まれた大文字と小文字が混在する SQL 識別子を、データベースが大文字と小文字を区別しないで扱うかどうか、およびそれらの識別子を大文字小文字混在で格納するかどうかを取得します。|  
|[supportsMultipleOpenResults](../../../connect/jdbc/reference/supportsmultipleopenresults-method-sqlserverdatabasemetadata.md)|複数を設定することがあるかどうかを取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)から返されるオブジェクト、 [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)オブジェクトを同時にします。|  
|[supportsMultipleResultSets](../../../connect/jdbc/reference/supportsmultipleresultsets-method-sqlserverdatabasemetadata.md)|このデータベースは、複数の取得をサポートしているかどうかを取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)に 1 回の呼び出しからのオブジェクト、[実行](../../../connect/jdbc/reference/execute-method.md)のメソッド、 [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)クラスです。|  
|[supportsMultipleTransactions](../../../connect/jdbc/reference/supportsmultipletransactions-method-sqlserverdatabasemetadata.md)|データベースが、異なる接続で複数のトランザクションを同時に開くことができるかどうかを取得します。|  
|[supportsNamedParameters](../../../connect/jdbc/reference/supportsnamedparameters-method-sqlserverdatabasemetadata.md)|データベースが呼び出し可能ステートメントで名前付きパラメーターをサポートするかどうかを取得します。|  
|[supportsNonNullableColumns](../../../connect/jdbc/reference/supportsnonnullablecolumns-method-sqlserverdatabasemetadata.md)|データベースの列を null を許容しない列として定義できるかどうかを取得します。|  
|[supportsOpenCursorsAcrossCommit](../../../connect/jdbc/reference/supportsopencursorsacrosscommit-method-sqlserverdatabasemetadata.md)|データベースが複数のコミットにわたってカーソルが開いたままの状態をサポートするかどうかを取得します。|  
|[supportsOpenCursorsAcrossRollback](../../../connect/jdbc/reference/supportsopencursorsacrossrollback-method-sqlserverdatabasemetadata.md)|データベースが複数のロールバックにわたってカーソルが開いたままの状態をサポートするかどうかを取得します。|  
|[supportsOpenStatementsAcrossCommit](../../../connect/jdbc/reference/supportsopenstatementsacrosscommit-method-sqlserverdatabasemetadata.md)|データベースが複数のコミットにわたってステートメントが開いたままの状態をサポートするかどうかを取得します。|  
|[supportsOpenStatementsAcrossRollback](../../../connect/jdbc/reference/supportsopenstatementsacrossrollback-method-sqlserverdatabasemetadata.md)|データベースが複数のロールバックにわたってステートメントが開いたままの状態をサポートするかどうかを取得します。|  
|[supportsOrderByUnrelated](../../../connect/jdbc/reference/supportsorderbyunrelated-method-sqlserverdatabasemetadata.md)|データベースが、ORDER BY 句で SELECT ステートメントにない列の使用をサポートするかどうかを取得します。|  
|[supportsOuterJoins](../../../connect/jdbc/reference/supportsouterjoins-method-sqlserverdatabasemetadata.md)|データベースが外部結合をサポートするかどうかを取得します。|  
|[supportsPositionedDelete](../../../connect/jdbc/reference/supportspositioneddelete-method-sqlserverdatabasemetadata.md)|データベースが位置指定された DELETE ステートメントをサポートするかどうかを取得します。|  
|[supportsPositionedUpdate](../../../connect/jdbc/reference/supportspositionedupdate-method-sqlserverdatabasemetadata.md)|データベースが位置指定された UPDATE ステートメントをサポートするかどうかを取得します。|  
|[supportsResultSetConcurrency](../../../connect/jdbc/reference/supportsresultsetconcurrency-method-sqlserverdatabasemetadata.md)|データベースが、渡された同時実行の種類と結果セットの種類の組み合わせをサポートするかどうかを取得します。|  
|[supportsResultSetHoldability](../../../connect/jdbc/reference/supportsresultsetholdability-method-sqlserverdatabasemetadata.md)|データベースが渡された結果セットの保持機能をサポートするかどうかを取得します。|  
|[supportsResultSetType](../../../connect/jdbc/reference/supportsresultsettype-method-sqlserverdatabasemetadata.md)|データベースが渡された結果セットの種類をサポートするかどうかを取得します。|  
|[supportsSavepoints](../../../connect/jdbc/reference/supportssavepoints-method-sqlserverdatabasemetadata.md)|データベースがセーブポイントをサポートするかどうかを取得します。|  
|[supportsSchemasInDataManipulation](../../../connect/jdbc/reference/supportsschemasindatamanipulation-method-sqlserverdatabasemetadata.md)|データ操作ステートメントでスキーマ名を使用できるかどうかを取得します。|  
|[supportsSchemasInIndexDefinitions](../../../connect/jdbc/reference/supportsschemasinindexdefinitions-method-sqlserverdatabasemetadata.md)|インデックス定義ステートメントでスキーマ名を使用できるかどうかを取得します。|  
|[supportsSchemasInPrivilegeDefinitions](../../../connect/jdbc/reference/supportsschemasinprivilegedefinitions-method-sqlserverdatabasemetadata.md)|特権定義ステートメントでスキーマ名を使用できるかどうかを取得します。|  
|[supportsSchemasInProcedureCalls](../../../connect/jdbc/reference/supportsschemasinprocedurecalls-method-sqlserverdatabasemetadata.md)|プロシージャ呼び出しステートメントでスキーマ名を使用できるかどうかを取得します。|  
|[supportsSchemasInTableDefinitions](../../../connect/jdbc/reference/supportsschemasintabledefinitions-method-sqlserverdatabasemetadata.md)|テーブル定義ステートメントでスキーマ名を使用できるかどうかを取得します。|  
|[supportsSelectForUpdate](../../../connect/jdbc/reference/supportsselectforupdate-method-sqlserverdatabasemetadata.md)|データベースが SELECT FOR UPDATE ステートメントをサポートするかどうかを取得します。|  
|[supportsStatementPooling](../../../connect/jdbc/reference/supportsstatementpooling-method-sqlserverdatabasemetadata.md)|データベースがステートメントのプールをサポートするかどうかを取得します。|  
|[supportsStoredFunctionsUsingCallSyntax](../../../connect/jdbc/reference/supportsstoredfunctionsusingcallsyntax-method-sqlserverdatabasemetadata.md)|現在のデータベースがストアド プロシージャのエスケープ構文を使用したユーザー定義関数またはベンダー定義関数の呼び出しをサポートするかどうかを示します。|  
|[supportsStoredProcedures](../../../connect/jdbc/reference/supportsstoredprocedures-method-sqlserverdatabasemetadata.md)|データベースがストアド プロシージャのエスケープ構文を使用するストアド プロシージャの呼び出しをサポートするかどうかを取得します。|  
|[supportsSubqueriesInComparisons](../../../connect/jdbc/reference/supportssubqueriesincomparisons-method-sqlserverdatabasemetadata.md)|データベースが比較式でサブクエリをサポートするかどうかを取得します。|  
|[supportsSubqueriesInExists](../../../connect/jdbc/reference/supportssubqueriesinexists-method-sqlserverdatabasemetadata.md)|データベースが EXISTS 式でサブクエリをサポートするかどうかを取得します。|  
|[supportsSubqueriesInIns](../../../connect/jdbc/reference/supportssubqueriesinins-method-sqlserverdatabasemetadata.md)|データベースが IN ステートメントでサブクエリをサポートするかどうかを取得します。|  
|[supportsSubqueriesInQuantifieds](../../../connect/jdbc/reference/supportssubqueriesinquantifieds-method-sqlserverdatabasemetadata.md)|データベースが定量化された式でサブクエリをサポートするかどうかを取得します。|  
|[supportsTableCorrelationNames](../../../connect/jdbc/reference/supportstablecorrelationnames-method-sqlserverdatabasemetadata.md)|データベースがテーブルの相関名をサポートするかどうかを取得します。|  
|[supportsTransactionIsolationLevel](../../../connect/jdbc/reference/supportstransactionisolationlevel-method-sqlserverdatabasemetadata.md)|データベースが渡されたトランザクションの分離レベルをサポートするかどうかを取得します。|  
|[supportsTransactions](../../../connect/jdbc/reference/supportstransactions-method-sqlserverdatabasemetadata.md)|データベースがトランザクションをサポートするかどうかを取得します。|  
|[supportsUnion](../../../connect/jdbc/reference/supportsunion-method-sqlserverdatabasemetadata.md)|データベースが SQL UNION をサポートするかどうかを取得します。|  
|[supportsUnionAll](../../../connect/jdbc/reference/supportsunionall-method-sqlserverdatabasemetadata.md)|データベースが SQL UNION ALL をサポートするかどうかを取得します。|  
|[updatesAreDetected](../../../connect/jdbc/reference/updatesaredetected-method-sqlserverdatabasemetadata.md)|呼び出して表示される行の更新プログラムを検出できるかどうかを取得、 [rowUpdated](../../../connect/jdbc/reference/rowupdated-method-sqlserverresultset.md)のメソッド、 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)クラスです。|  
|[usesLocalFilePerTable](../../../connect/jdbc/reference/useslocalfilepertable-method-sqlserverdatabasemetadata.md)|データベースがテーブルごとにファイルを使用するかどうかを取得します。|  
|[usesLocalFiles](../../../connect/jdbc/reference/useslocalfiles-method-sqlserverdatabasemetadata.md)|データベースがテーブルをローカル ファイルに格納するかどうかを取得します。|  
  
## <a name="inherited-methods"></a>継承されたメソッド  
  
|継承元のクラス|メソッド|  
|---------------------------|-------------|  
|java.lang.Object|clone、equals、finalize、getClass、hashCode、notify、notifyAll、toString、wait|  
|java.sql.Wrapper|isWrapperFor、unwrap|  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

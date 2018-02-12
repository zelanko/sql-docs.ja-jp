---
title: "プログラミング ガイドライン (SQL Server 用 ODBC Driver) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/11/2018
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: fd8952f28f389fa5f1b8f82072998676c5a4196e
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2018
---
# <a name="programming-guidelines"></a>プログラミング ガイドライン

[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

プログラミング機能、 [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] macOS および Linux では、ODBC に基づいて[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]Native Client ([SQL Server ・ Native Client (ODBC)](http://go.microsoft.com/fwlink/?LinkID=134151))。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]Native Client は Windows Data Access Components の ODBC に基づいて ([ODBC プログラマ リファレンス](http://go.microsoft.com/fwlink/?LinkID=45250))。  

複数のアクティブな結果セット (MARS) およびその他の ODBC アプリケーションで使用できます[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]特定の機能を含めることによって`/usr/local/include/msodbcsql.h`unixODBC ヘッダーを含めた後 (`sql.h`、 `sqlext.h`、 `sqltypes.h`、および`sqlucode.h`)。 場合は、同じシンボル名を使用して[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]-Windows ODBC アプリケーションで使用する特定の項目。

## <a name="available-features"></a>利用可能な機能  
以下のセクション、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] ODBC 用 Native Client のドキュメント ([SQL Server ・ Native Client (ODBC)](http://go.microsoft.com/fwlink/?LinkID=134151)) macOS および Linux で ODBC driver を使用しているときに有効。  

-   [SQL Server との通信 (ODBC)](http://msdn.microsoft.com/library/ms131692.aspx)  
-   [接続とクエリのタイムアウトのサポート](http://msdn.microsoft.com/library/ms130822.aspx)  
-   [カーソル](http://msdn.microsoft.com/library/ms130794(SQL.110).aspx)  
-   [日付/時刻の強化 (ODBC)](http://msdn.microsoft.com/library/bb677319.aspx)  
-   [クエリの実行 (ODBC)](http://msdn.microsoft.com/library/ms131677.aspx)  
-   [エラーとメッセージの処理](http://msdn.microsoft.com/library/ms131289.aspx)  
-   [Kerberos 認証](http://msdn.microsoft.com/library/cc280459.aspx)  
-   [大きな CLR ユーザー定義型 (ODBC)](http://msdn.microsoft.com/library/bb677316.aspx)  
-   [実行 (分散トランザクション) を除くトランザクション (ODBC)](http://msdn.microsoft.com/library/ms131706.aspx)  
-   [結果の処理 (ODBC)](http://msdn.microsoft.com/library/ms130812.aspx)  
-   [ストアド プロシージャの実行](http://msdn.microsoft.com/library/ms131440.aspx)
-   [スパース列のサポート (ODBC)](http://msdn.microsoft.com/library/cc280357.aspx)
-   [SSL 暗号化](http://msdn.microsoft.com/library/ms131691.aspx)
-   [テーブルの値を持つパラメーター](https://docs.microsoft.com/en-us/sql/relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc)
-   [Utf-8 および utf-16 コマンドおよびデータ API を](http://msdn.microsoft.com/library/ff878241.aspx)
-   [カタログ関数の使用](http://msdn.microsoft.com/library/ms131490.aspx)  

## <a name="unsupported-features"></a>サポートされていない機能

MacOS および Linux の ODBC ドライバーのこのリリースで正常に動作する、次の機能が検証されていません。

-   フェールオーバー クラスターの接続
-   [透過ネットワーク IP 解決](https://docs.microsoft.com/en-us/sql/connect/odbc/linux/using-transparent-network-ip-resolution)(ODBC ドライバー 17) の前に
-   [高度なドライバーのトレース](https://blogs.msdn.microsoft.com/mattn/2012/05/15/enabling-advanced-driver-tracing-for-the-sql-native-client-odbc-drivers/)

MacOS および Linux の ODBC ドライバーのこのリリースでは、次の機能が利用できません。 

-   分散トランザクション (SQL_ATTR_ENLIST_IN_DTC 属性はサポートされていません)  
-   データベース ミラーリング  
-   FILESTREAM  
-   説明されている ODBC ドライバーのパフォーマンスのプロファイリング、 [SQLSetConnectAttr](http://go.microsoft.com/fwlink/?LinkId=234099)、および次のパフォーマンス関連接続属性。  
    -   SQL_COPT_SS_PERF_DATA  
    -   SQL_COPT_SS_PERF_DATA_LOG  
    -   SQL_COPT_SS_PERF_DATA_LOG_NOW  
    -   SQL_COPT_SS_PERF_QUERY  
    -   SQL_COPT_SS_PERF_QUERY_INTERVAL  
    -   SQL_COPT_SS_PERF_QUERY_LOG  
-   SQLBrowseConnect  
-   SQL_C_INTERVAL_YEAR_TO_MONTH など C 間隔型 (に記載されている[のデータ型識別子と記述子](http://msdn.microsoft.com/library/ms716351(VS.85).aspx))
-   SQLSetConnectAttr 関数の SQL_ATTR_ODBC_CURSORS 属性の SQL_CUR_USE_ODBC 値です。

## <a name="character-set-support"></a>文字セットのサポート

ODBC Driver 13 および 13.1、SQLCHAR データは utf-8 をする必要があります。 その他のエンコーディングがサポートされていません。

ODBC ドライバーの 17、次の文字セットとエンコーディングのいずれかの SQLCHAR データはサポートされています。

|名前|Description|
|-|-|
|UTF-8|Unicode|
|CP437|MS-DOS ラテン アメリカ|
|CP850|MS-DOS ラテン 1|
|CP874|ラテン/タイ語|
|CP932|日本語、SHIFT-JIS|
|CP936|簡体字中国語、GBK|
|CP949|韓国語、EUC-KR|
|CP950|繁体字中国語、Big5|
|CP1251|キリル文字|
|CP1253|ギリシャ語|
|CP1256|アラビア語|
|CP1257|バルト語|
|CP1258|ベトナム語|
|ISO-8859-1 / CP1252|ラテン語-1|
|ISO-8859-2 / CP1250|ラテン語-2|
|ISO-8859-3|ラテン語-3|
|ISO-8859-4|ラテン語-4|
|ISO-8859-5|ラテン/キリル|
|ISO-8859-6|ラテン語とアラビア語|
|ISO-8859-7|ラテン語とギリシャ語|
|ISO-8859-8 / CP1255|ヘブライ語|
|ISO-8859-9 / CP1254|トルコ語|
|ISO-8859-13|ラテン語-7|
|ISO-8859-15|ラテン 9|

接続時に、ドライバーに読み込まれるプロセスの現在のロケールを検出します。 ドライバーはその SQLCHAR (ナロー文字) のデータのエンコードを使用して上記のエンコーディングのいずれかを使用している場合それ以外の場合、既定値は utf-8 です。 すべてのプロセスは既定では、"C"ロケールで開始 (そして、utf-8 を既定値に、ドライバーが発生するため)、使用する場合は、アプリケーションは、上記のエンコーディングのいずれかを使用する必要がある、 **setlocale、_wsetlocale**前に適切なロケールを設定する関数接続です。目的のロケールを明示的に指定または空の文字列を使用して、たとえばによって`setlocale(LC_ALL, "")`環境のロケール設定を使用します。

したがって、環境では一般的な Linux または Mac utf-8 エンコードが、ODBC ドライバーの 17 が 13 または 13.1 からアップグレードする場合のユーザー監視しませんのすべての差異です。 ただしを使用するアプリケーションを使用して、上記のリストで非 utf-8 のエンコード`setlocale()`utf-8 ではなく、ドライバーからのデータをそのエンコーディングを使用する必要があります。

SQLWCHAR データは UTF 16LE (リトル エンディアン) である必要があります。

ドライバーがクライアントの既定値 (通常のコード ページ 1252) にエンコーディングから提供されたデータを変換ナロー文字 SQL 型などが SQL_VARCHAR が指定されている場合は、SQLBindParameter での入力パラメーターをバインドする場合[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]エンコードします。 出力パラメーターの場合は、ドライバーは、クライアントのエンコーディングのデータに関連付けられた照合順序の情報に指定されたエンコーディングから変換します。 ただし、データ損失が発生する---ターゲット エンコードでは表現できないソースのエンコード中に文字が疑問符 () に変換されます ('? ')。

このデータの損失を避けるためには、入力パラメーターをバインドするときに、SQL_NVARCHAR などの Unicode SQL 文字型を指定します。 この場合、ドライバーは、クライアントのすべての Unicode 文字を表すことができます、utf-16 エンコーディングから変換します。 さらに、ターゲット列またはサーバー上のパラメーターもありますか、Unicode 型 (**nchar**、 **nvarchar**、 **ntext**) または 1 つでは、照合順序/、エンコーディングが元のソース データのすべての文字を表します。 Output パラメーターとデータの損失を回避するため、Unicode の SQL 型と型を指定いずれか、Unicode C (SQL_C_WCHAR) utf-16; としてデータを返すドライバーの原因または、ナロー C 型、およびクライアントのエンコーディングがすべて (これは常に utf-8 では可能です)、ソース データの文字を表すことができることを確認してください。

照合順序とエンコーディングの詳細については、次を参照してください。 [Collation and Unicode Support](../../../relational-databases/collations/collation-and-unicode-support.md)です。

なエンコード変換相違 Windows と Linux および macOS の iconv ライブラリの複数のバージョンがあります。 テキストのコードページ 1255 (ヘブライ語) にはデータを Unicode に変換すると動作が異なる 1 つのコード ポイント (0 xca)。 Windows では、この文字は、0x05BA の utf-16 コード ポイントに変換します。 MacOS および libiconv 1.15 より前のバージョンの Linux では、0x00CA に変換します。 Big5/CP950 の 2003年バージョンをサポートしていない iconv ライブラリと Linux の (名前付き`BIG5-2003`)、そのリビジョンを使用して追加の文字が正しく変換されません。

ODBC Driver 13 および 13.1、マルチバイト文字の utf-8 または utf-16 サロゲートが SQLPutData バッファー間で分割はデータの破損で行われます。 部分文字エンコーディングで終了していないストリーミング SQLPutData にバッファーを使用します。 この制限は、ODBC ドライバーの 17 で削除されました。

## <a name="additional-notes"></a>追加の注意事項  

1.  専用管理者接続 (DAC) を行うことができますを使用して[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]認証と**ホスト、ポート**です。 Sysadmin ロールのメンバーはまず、DAC ポートを検出する必要があります。 参照してください[データベース管理者用の診断接続](https://docs.microsoft.com/en-us/sql/database-engine/configure-windows/diagnostic-connection-for-database-administrators#dac-port)を検出する方法です。 たとえば、DAC ポートが 33000 なら、接続できますを使って`sqlcmd`次のようにします。  

    ```
    sqlcmd –U <user> -P <pwd> -S <host>,33000
    ```

    > [!NOTE]  
    > DAC 接続を使用する必要があります[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]認証します。  
    
2.  UnixODBC ドライバー マネージャーは、すべてのステートメント属性に対し、それらが SQLSetConnectAttr 経由で渡される場合に、「属性またはオプション識別子が無効です」を返します。 Windows では、SQLSetConnectAttr がステートメント属性値を受信すると、接続ハンドルの子であるすべてのアクティブなステートメントでその値を設定するドライバー。  

## <a name="see-also"></a>参照  
[よく寄せられる質問](../../../connect/odbc/linux-mac/frequently-asked-questions-faq-for-odbc-linux.md)

[このバージョンのドライバーの既知の問題](../../../connect/odbc/linux-mac/known-issues-in-this-version-of-the-driver.md)

[リリース ノート](../../../connect/odbc/linux-mac/release-notes.md)

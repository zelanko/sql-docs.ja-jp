---
title: プログラミング ガイドライン (ODBC Driver for SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 01/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3068d2a796e7e28e4eda58514cc316fe504bbce3
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 08/16/2018
ms.locfileid: "42785683"
---
# <a name="programming-guidelines"></a>プログラミング ガイドライン

[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

macOS と Linux での [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のプログラミング機能は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ([SQL Server Native Client (ODBC)](http://go.microsoft.com/fwlink/?LinkID=134151)) の ODBC に基づいています。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client は、Windows Data Access Components の ODBC に基づいています ([ODBC プログラマー リファレンス](http://go.microsoft.com/fwlink/?LinkID=45250))。  

複数のアクティブな結果セット (MARS) およびその他の ODBC アプリケーションで使用できます[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]特定の機能を含めることによって`/usr/local/include/msodbcsql.h`unixODBC ヘッダーを含めた後 (`sql.h`、 `sqlext.h`、 `sqltypes.h`、および`sqlucode.h`)。 次に、Windows ODBC アプリケーションで使用する [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 固有の項目に、同じシンボル名を使用します。

## <a name="available-features"></a>利用可能な機能  
[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ODBC 用 Native Client のドキュメント ([SQL Server Native Client (ODBC)](http://go.microsoft.com/fwlink/?LinkID=134151)) の次のセクションは、macOS と Linux で ODBC ドライバーを使用する場合に有効です。  

-   [SQL Server との通信 (ODBC)](http://msdn.microsoft.com/library/ms131692.aspx)  
-   [接続とクエリのタイムアウトのサポート](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)  
-   [カーソル](../../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md)  
-   [日付/時刻の強化 (ODBC)](http://msdn.microsoft.com/library/bb677319.aspx)  
-   [クエリの実行 (ODBC)](http://msdn.microsoft.com/library/ms131677.aspx)  
-   [エラーとメッセージの処理](../../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
-   [Kerberos 認証](../../../relational-databases/native-client/features/service-principal-name-spn-support-in-client-connections.md)  
-   [大きな CLR ユーザー定義型 (ODBC)](http://msdn.microsoft.com/library/bb677316.aspx)  
-   [トランザクションの実行 (ODBC) (分散トランザクションを除く)](http://msdn.microsoft.com/library/ms131706.aspx)  
-   [結果の処理 (ODBC)](http://msdn.microsoft.com/library/ms130812.aspx)  
-   [ストアド プロシージャの実行](../../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)
-   [スパース列のサポート (ODBC)](http://msdn.microsoft.com/library/cc280357.aspx)
-   [SSL 暗号化](../../../relational-databases/native-client/features/using-encryption-without-validation.md)
-   [テーブル値パラメーター](https://docs.microsoft.com/sql/relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc)
-   [コマンドおよびデータ API の UTF-8 および UTF-16](http://msdn.microsoft.com/library/ff878241.aspx)
-   [カタログ関数の使用](../../../relational-databases/native-client/odbc/using-catalog-functions.md)  

## <a name="unsupported-features"></a>サポートされていない機能

MacOS および Linux で ODBC ドライバーのこのリリースで正常に動作する、次の機能が検証されていません。

-   フェールオーバー クラスターの接続
-   [透過ネットワーク IP 解決](https://docs.microsoft.com/sql/connect/odbc/linux/using-transparent-network-ip-resolution)(ODBC Driver 17) の前に
-   [高度なドライバーのトレース](https://blogs.msdn.microsoft.com/mattn/2012/05/15/enabling-advanced-driver-tracing-for-the-sql-native-client-odbc-drivers/)

macOS と Linux でのこのリリースの ODBC ドライバーでは、次の機能は利用できません。 

-   分散トランザクション (SQL_ATTR_ENLIST_IN_DTC 属性はサポートされていません)  
-   データベース ミラーリング  
-   FILESTREAM  
-   [SQLSetConnectAttr](http://go.microsoft.com/fwlink/?LinkId=234099) で説明されている ODBC ドライバー パフォーマンスのプロファイリング、および次のパフォーマンス関連接続属性:  
    -   SQL_COPT_SS_PERF_DATA  
    -   SQL_COPT_SS_PERF_DATA_LOG  
    -   SQL_COPT_SS_PERF_DATA_LOG_NOW  
    -   SQL_COPT_SS_PERF_QUERY  
    -   SQL_COPT_SS_PERF_QUERY_INTERVAL  
    -   SQL_COPT_SS_PERF_QUERY_LOG  
-   SQLBrowseConnect  
-   SQL_C_INTERVAL_YEAR_TO_MONTH などの C 時間隔型 (「[Data Type Identifiers and Descriptors](http://msdn.microsoft.com/library/ms716351(VS.85).aspx)」(データ型識別子と記述子) を参照)
-   SQLSetConnectAttr 関数の SQL_ATTR_ODBC_CURSORS 属性の SQL_CUR_USE_ODBC 値。

## <a name="character-set-support"></a>文字セットのサポート

ODBC Driver 13 および 13.1、SQLCHAR データは utf-8 をする必要があります。 その他のエンコーディングがサポートされていません。

ODBC Driver 17 では、次の文字セットとエンコーディングのいずれかの SQLCHAR データはサポートされています。

|[オブジェクト名]|[説明]|
|-|-|
|UTF-8|Unicode|
|CP437|MS-DOS ラテン アメリカ|
|CP850|MS-DOS ラテン 1|
|CP874|ラテン/タイ語|
|CP932|日本語、Shift-JIS|
|CP936|簡体字中国語、GBK|
|CP949|韓国語、EUC-KR|
|CP950|繁体字中国語、Big5|
|CP1251|キリル文字|
|CP1253|ギリシャ語|
|CP1256|アラビア語|
|CP1257|バルト語|
|CP1258|ベトナム語|
|ISO 8859-1/CP1252|ラテン-1|
|ISO 8859-2/CP1250|ラテン 2|
|ISO 8859-3|ラテン語-3|
|ISO 8859-4|ラテン語-4|
|ISO 8859-5|ラテン/キリル|
|ISO 8859-6|ラテン語とアラビア語|
|ISO 8859-7|ラテン語とギリシャ語|
|ISO 8859-8/CP1255|ヘブライ語|
|ISO-8859-9/CP1254|トルコ語|
|ISO 8859-13|ラテン語-7|
|ISO-8859-15|ラテン 9|

接続時に、ドライバーに読み込まれるプロセスの現在のロケールを検出します。 ドライバーはその SQLCHAR (ナロー文字) データのエンコーディングを使用して上記のエンコーディングのいずれかを使用する場合それ以外の場合、utf-8 を既定になります。 すべてのプロセスは既定で"C"ロケールで開始 (そして、既定値にドライバーを utf-8 に発生するため)、上記のエンコーディングのいずれかを使用する場合、アプリケーションを使用する、 **setlocale**ロケールを前に適切に設定する関数接続します。目的のロケールを明示的に指定するか、空の文字列を例を使用していずれか`setlocale(LC_ALL, "")`環境のロケール設定を使用します。

したがって、環境では、一般的な Linux または Mac utf-8 エンコーディングが、ODBC Driver 17 が 13 または 13.1 からアップグレードするユーザーは、そのはな違いにも確認しません。 ただし、使用するアプリケーションを使用して、上記のリストで非 utf-8 エンコード`setlocale()`そのエンコードすると、utf-8 ではなく、ドライバーからデータを使用する必要があります。

SQLWCHAR データは UTF 16LE (リトル エンディアン) である必要があります。

ドライバーがクライアントの既定値 (コード ページ 1252 通常) にエンコーディングから、指定されたデータを変換 SQL_VARCHAR が指定したなどのナロー文字 SQL 型の場合は、SQLBindParameter の入力パラメーターをバインドする場合[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]エンコードします。 出力パラメーターの場合は、ドライバーは、クライアントのエンコーディングのデータに関連付けられた照合順序の情報に指定されたエンコーディングからに変換します。 ただし、データ損失が---ソースのエンコード中にターゲット エンコードで表現できない文字が疑問符 () に変換されます ('? ')。

このデータの損失を避けるためには、入力パラメーターをバインドするときに、SQL_NVARCHAR などの Unicode SQL 文字型を指定します。 この場合、ドライバーは、クライアントのすべての Unicode 文字を表すことができます、utf-16 エンコーディングから変換します。 さらに、ターゲット列またはパラメーター、サーバーである必要がありますも Unicode 型 (**nchar**、 **nvarchar**、 **ntext**) または 1 つで、照合順序/エンコードすることができます元のソース データのすべての文字を表します。 出力パラメーターを持つデータの損失を回避するには、Unicode SQL 型と型を指定か、Unicode C (SQL_C_WCHAR)、utf-16; としてデータを返す、ドライバーの原因または、幅が狭い C 型、およびクライアントのエンコーディングが (これは常に utf-8 でできること). ソース データのすべての文字を表すことを確認して

照合順序とエンコードについて詳しくは、「[照合順序と Unicode のサポート](../../../relational-databases/collations/collation-and-unicode-support.md)」をご覧ください。

Windows と Linux、macOS 上の iconv ライブラリのいくつかのバージョンでいくつかのエンコード変換違いがあります。 コードページ 1255 のテキスト データ (ヘブライ語) では、Unicode に変換すると動作が異なる 1 つのコード ポイント (0 xca) があります。 、Windows では、この文字は、0x05BA の utf-16 コード ポイントに変換します。 MacOS および Linux libiconv バージョン 1.15 より前で、0x00CA に変換します。 Big5/CP950 の 2003年バージョンをサポートしていない iconv ライブラリを使った Linux 上 (という`BIG5-2003`)、そのリビジョンを使用して追加の文字が正しく変換されません。 コード ページ 932 (日本語、Shift JIS)、エンコードの標準で定義されていない文字のデコード結果が異なるもします。 たとえば、バイト 0x80 は u+0080 Windows 上に変換が、Linux と macOS の iconv バージョンに応じて、U + 30FB になる可能性があります。

ODBC Driver 13 および 13.1 では、UTF-8 マルチバイト文字または UTF-16 サロゲートが SQLPutData バッファー間で分割されている場合、データの破損が発生します。 部分文字エンコーディングで終了していないストリーミング SQLPutData にバッファーを使用します。 ODBC Driver 17 で、この制限が削除されました。

## <a name="additional-notes"></a>追加情報  

1.  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証と **host,port** を使用して、専用管理者接続 (DAC) を作成できます。 Sysadmin ロールのメンバーはまず、DAC ポートを検出する必要があります。 参照してください[データベース管理者用の診断接続](https://docs.microsoft.com/sql/database-engine/configure-windows/diagnostic-connection-for-database-administrators#dac-port)を検出する方法。 たとえば、DAC ポートが 33000 である場合、次のように `sqlcmd` でそれに接続することができます。  

    ```
    sqlcmd –U <user> -P <pwd> -S <host>,33000
    ```

    > [!NOTE]  
    > DAC 接続では、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証を使用する必要があります。  
    
2.  UnixODBC ドライバー マネージャーは、すべてのステートメント属性に対し、それらが SQLSetConnectAttr 経由で渡される場合に、「属性またはオプション識別子が無効です」を返します。 Windows で、SQLSetConnectAttr がステートメント属性値を受け取ると、ドライバーは接続ハンドルの子であるすべてのアクティブなステートメントにその値を設定します。  

## <a name="see-also"></a>参照  
[よく寄せられる質問](../../../connect/odbc/linux-mac/frequently-asked-questions-faq-for-odbc-linux.md)

[このバージョンのドライバーの既知の問題](../../../connect/odbc/linux-mac/known-issues-in-this-version-of-the-driver.md)

[リリース ノート](../../../connect/odbc/linux-mac/release-notes.md)

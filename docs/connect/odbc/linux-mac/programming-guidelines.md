---
title: "プログラミング ガイドライン |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 50f9efe65f14dbd73ccbc3c6e81307c3893c469f
ms.openlocfilehash: 85ba8b35fa698769bd390837855729f3edbc7291
ms.contentlocale: ja-jp
ms.lasthandoff: 11/08/2017

---
# <a name="programming-guidelines"></a>プログラミング ガイドライン

[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

プログラミング機能、 [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 13 およびの 13.1 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] macOS および Linux では、ODBC に基づいて[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]Native Client ([SQL Server ・ Native Client (ODBC)](http://go.microsoft.com/fwlink/?LinkID=134151))。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]Native Client は Windows Data Access Components の ODBC に基づいて ([ODBC プログラマ リファレンス](http://go.microsoft.com/fwlink/?LinkID=45250))。  

複数のアクティブな結果セット (MARS) およびその他の ODBC アプリケーションで使用できます[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]特定の機能を含めることによって`/usr/local/include/msodbcsql.h`unixODBC ヘッダーを含めた後 (`sql.h`、 `sqlext.h`、 `sqltypes.h`、および`sqlucode.h`)。 場合は、同じシンボル名を使用して[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]-Windows ODBC アプリケーションでは特定の項目。  

## <a name="available-features"></a>利用可能な機能  
以下のセクション、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] ODBC 用 Native Client のドキュメント ([SQL Server ・ Native Client (ODBC)](http://go.microsoft.com/fwlink/?LinkID=134151)) macOS および Linux で ODBC driver を使用しているときに有効。  

-   [SQL Server (ODBC) との通信](http://msdn.microsoft.com/library/ms131692.aspx)  
-   [接続とクエリのタイムアウトのサポート](http://msdn.microsoft.com/library/ms130822.aspx)  
-   [カーソル](http://msdn.microsoft.com/library/ms130794(SQL.110).aspx)  
-   [日付/時刻の強化 (ODBC)](http://msdn.microsoft.com/library/bb677319.aspx)  
-   [クエリの実行 (ODBC)](http://msdn.microsoft.com/library/ms131677.aspx)  
-   [エラーとメッセージの処理](http://msdn.microsoft.com/library/ms131289.aspx)  
-   [Kerberos 認証](http://msdn.microsoft.com/library/cc280459.aspx)  
-   [大きな CLR ユーザー定義型 (ODBC)](http://msdn.microsoft.com/library/bb677316.aspx)  
-   [実行 (分散トランザクション) を除くトランザクション (ODBC)](http://msdn.microsoft.com/library/ms131706.aspx)  
-   [処理結果 (ODBC)](http://msdn.microsoft.com/library/ms130812.aspx)  
-   [ストアド プロシージャの実行](http://msdn.microsoft.com/library/ms131440.aspx)
-   [スパース列のサポート (ODBC)](http://msdn.microsoft.com/library/cc280357.aspx)
-   [SSL 暗号化](http://msdn.microsoft.com/library/ms131691.aspx)
-   [テーブルの値を持つパラメーター](https://docs.microsoft.com/en-us/sql/relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc)
-   [Utf-8 および utf-16 コマンドおよびデータ API を](http://msdn.microsoft.com/library/ff878241.aspx)
-   [カタログ関数の使用](http://msdn.microsoft.com/library/ms131490.aspx)  

## <a name="unsupported-features"></a>サポートされていない機能

MacOS および Linux の ODBC ドライバーのこのリリースで正常に動作する、次の機能が検証されていません。

-   フェールオーバー クラスターの接続
-   [透過ネットワーク IP 解決](https://docs.microsoft.com/en-us/sql/connect/odbc/linux/using-transparent-network-ip-resolution)
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

クライアントのエンコーディングには、次のいずれかを指定できます。
  -  UTF-8
  -  ISO 8859-1
  -  ISO 8859-2
  -  ISO 8859-3
  -  ISO 8859-4
  -  ISO 8859-5
  -  ISO 8859-6
  -  ISO 8859-7
  -  ISO 8859-8
  -  ISO 8859-9
  -  ISO 8859-13
  -  ISO 8859-15
  
SQLCHAR データは、サポートされている文字セットのいずれかにする必要があります。 SQLWCHAR データは UTF 16LE (リトル エンディアン) である必要があります。  

SQLDescribeParameter でサーバーの SQL 型を指定していない場合、ドライバーは SQLBindParameter の *ParameterType* パラメーターに指定された SQL 型を使用します。 SQLBindParameter に SQL_VARCHAR などのナロー文字 SQL 型が指定されている場合、ドライバー、提供されたデータ、クライアント コード ページからに変換既定値[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]コード ページです。 (既定値[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]コード ページは一般に 1252 です)。クライアントのコード ページがサポートされていない場合は、utf-8 に設定されます。 この場合、ドライバー utf-8 データを既定のコード ページとし、変換します。 ただし、データが失われる可能性があります。 コード ページ 1252 で文字を表現できない場合、ドライバーは文字を疑問符 ('?') に変換します。 このデータの損失を回避するには、SQLBindParameter に SQL_NVARCHAR などの Unicode SQL 文字型を指定します。 この場合、ドライバーは、utf-8 エンコードで utf-16 データの損失なしで指定された Unicode データを変換します。

Windows と Linux および macOS の iconv ライブラリの複数のバージョンの間でテキスト エンコード変換違いがあります。 コードページ 1255 (ヘブライ語) でエンコードされたテキスト データは、変換時に動作が異なる 1 つのコード ポイント (0 xca) がします。 この文字を Windows では Unicode に変換するには、0x05BA の utf-16 コード ポイントが生成されます。 Libiconv バージョンと macOS および Linux で Unicode への変換 1.15 より以前生成 0x00CA の utf-16 コード ポイント。

UTF-8 マルチバイト文字または UTF-16 サロゲートが SQLPutData バッファー間で分割されている場合、データの破損が発生します。 部分文字エンコーディングで終了していないストリーミング SQLPutData にバッファーを使用します。  

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


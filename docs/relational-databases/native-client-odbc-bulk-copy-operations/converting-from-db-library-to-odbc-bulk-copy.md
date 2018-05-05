---
title: Db-library から ODBC 一括コピーへの変換 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-odbc-bulk-copy-operations
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- converting DB-Library to ODBC bulk copy
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC], DB-Library bulk copy
- ODBC, bulk copy operations
- DB-Library bulk copy
ms.assetid: 0bc15bdb-f19f-4537-ac6c-f249f42cf07f
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: bc8072a1bd0f0e3a097a01696c9d034e0acb33c7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="converting-from-db-library-to-odbc-bulk-copy"></a>DB-Library から ODBC への一括コピーの変換
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Db-library の一括コピー プログラムを ODBC に変換するには、一括コピー関数でサポートされているので簡単、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは次の例外を除き、Db-library の一括コピー関数に似ています。  
  
-   DB-Library アプリケーションでは、DBPROCESS 構造体を指すポインターを一括コピー関数の最初のパラメーターに渡します。 ODBC アプリケーションでは、DBPROCESS ポインターが ODBC 接続ハンドルに置き換わります。  
  
-   Db-library アプリケーション呼び出し**BCP_SETL** DBPROCESS で一括コピー操作を有効に接続する前にします。 ODBC アプリケーションを呼び出す代わりに[SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)接続ハンドルでの一括操作を有効に接続する前に。  
  
    ```  
    SQLSetConnectAttr(hdbc, SQL_COPT_SS_BCP,  
        (void *)SQL_BCP_ON, SQL_IS_INTEGER);  
    ```  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは Db-library のメッセージとエラー ハンドラーをサポートしていません。 する関数を呼び出す必要があります**SQLGetDiagRec**エラーと ODBC の一括コピー関数によって生成されたメッセージを取得します。 ODBC バージョンの一括コピー関数は、標準的な一括コピーのリターン コードである SUCCEED または FAILED を返しますが、SQL_SUCCESS や SQL_ERROR など、ODBC 形式のリターン コードを返しません。  
  
-   DB ライブラリの指定した値[bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)*varlen*パラメーターの解釈は、ODBC とは異なる **bcp_bind * * * cbData*パラメーター。  
  
    |示された状態|Db-library *varlen*値|ODBC *cbData*値|  
    |-------------------------|--------------------------------|-------------------------|  
    |NULL 値が指定された場合|0|-1 (SQL_NULL_DATA)|  
    |可変長のデータが指定された場合|-1|-10 (SQL_VARLEN_DATA)|  
    |長さが 0 の文字列またはバイナリ文字列の場合|NA|0|  
  
     Db-library では、 *varlen*値-1 は、可変長のデータが指定されていることを示します、ODBC で*cbData*は NULL 値のみが指定されていることを意味する解釈されます。 Db-library での変更*varlen*を SQL_VARLEN_DATA に-1 が仕様*varlen* SQL_NULL_DATA に 0 が指定されます。  
  
-   Db-library  **bcp_colfmt * * * file_collen*と ODBC [bcp_colfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md)* cbUserData * として同じ問題がある、**bcp_bind * * * varlen*と*cbData*上記のパラメーターです。 Db-library での変更*file_collen*を SQL_VARLEN_DATA に-1 が仕様*file_collen* SQL_NULL_DATA に 0 が指定されます。  
  
-   *IValue* 、ODBC のパラメーター [bcp_control](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-control.md)関数は、void ポインターです。 Db-library では、 *iValue*が整数でした。 ODBC の値をキャスト*iValue*を void * です。  
  
-   **Bcp_control** BCPMAXERRS オプションは、一括コピー操作が失敗する前に、個々 の行の数がエラーを持つことができますを指定します。 BCPMAXERRS の既定値は 0 (最初のエラーで失敗します)、Db-library バージョンので**bcp_control** ODBC のバージョンでは 10 です。 Db-library アプリケーションで、既定の一括コピー操作を終了する 0 に依存するは、ODBC の呼び出しに変更する必要があります**bcp_control** BCPMAXERRS を 0 に設定します。  
  
-   ODBC **bcp_control**関数では、次のオプションの Db-library バージョンでサポートされていません**bcp_control**:  
  
    -   BCPODBC  
  
         条件を満たすことを指定する設定と**datetime**と**smalldatetime** ODBC タイムスタンプ エスケープ シーケンスのプレフィックスとサフィックス文字形式で保存された値になります。 これは、BCP_OUT 操作に対してのみ適用されます。  
  
         Bcpodbc を FALSE に設定した、 **datetime**と文字の文字列に変換された値が出力されます。  
  
        ```  
        1997-01-01 00:00:00.000  
        ```  
  
         Bcpodbc を同じ TRUE に設定した**datetime**として値を出力します。  
  
        ```  
        {ts '1997-01-01 00:00:00.000' }  
        ```  
  
    -   BCPKEEPIDENTITY  
  
         TRUE に設定した場合、一括コピー関数で、ID 制約を含む列に対して指定したデータ値が挿入されることを示します。 このオプションを設定しないと、挿入される行に対して新しい ID 値が生成されます。  
  
    -   BCPHINTS  
  
         一括コピーのさまざまな最適化を指定します。 このオプションは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.5 以前のバージョンでは使用できません。  
  
    -   BCPFILECP  
  
         一括コピー ファイルのコード ページを指定します。  
  
    -   BCPUNICODEFILE  
  
         キャラクター モードの一括コピー ファイルが Unicode ファイルであることを指定します。  
  
-   ODBC **bcp_colfmt**関数がサポートされていません、 *file_type* SQLCHAR のインジケーター、ODBC SQLCHAR typedef と競合するためです。 代わりに SQLCHARACTER を使用して**bcp_colfmt**です。  
  
-   ODBC のバージョンの一括コピー関数で使用するための形式で**datetime**と**smalldatetime** -yyyy-mm-dd hh:mm:ss.sss; の ODBC 形式の文字列の値は**smalldatetime**値形式を使用して、ODBC の yyyy-mm-dd hh:mm:ss のです。  
  
     Db-library バージョンの一括コピー関数を受け入れる**datetime**と**smalldatetime**いくつかの形式を使用する文字の文字列の値。  
  
    -   既定の形式は*mmm dd yyyy hh:mmxx*場所*xx*は AM または PM。  
  
    -   **datetime**と**smalldatetime** Db-library でサポートされている任意の形式で文字列**dbconvert**関数。  
  
    -   ときに、**インターナショナル設定を使用して**Db-library のチェック ボックスをオン**オプション**のタブ、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアント ネットワーク ユーティリティ、Db-library の一括コピー関数も日付を受け取る地域クライアント コンピューターのレジストリのロケール設定に定義された日付形式です。  
  
     Db-library の一括コピー関数は、ODBC を受け入れない**datetime**と**smalldatetime**形式です。  
  
     SQL_SOPT_SS_REGIONALIZE ステートメント属性を SQL_RE_ON に設定すると、ODBC の一括コピー関数はクライアント コンピューターのレジストリのロケール設定に定義された地域別の日付形式のデータを受け取ります。  
  
-   出力時に**money**文字形式、ODBC 一括コピー関数サプライ 4 桁の有効桁数および; なしのコンマ区切りの値Db-library バージョンでのみ有効桁数 2 桁の数字を指定してください、コンマを区切り記号が含まれます。  
  
## <a name="see-also"></a>参照  
 [一括コピー操作を実行する&#40;ODBC&#41;](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)   
 [一括コピー関数](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  

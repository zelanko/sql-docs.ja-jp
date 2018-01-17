---
title: "bcp_init |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-extensions-bulk-copy-functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname: bcp_init
apilocation: sqlncli11.dll
apitype: DLLExport
helpviewer_keywords: bcp_init function
ms.assetid: 6a25862c-7f31-4873-ab65-30f3abde89d2
caps.latest.revision: "40"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 19e15b0c56bc673bff3bd88bc3b5a639e54ea48c
ms.sourcegitcommit: 779f3398e4e3f4c626d81ae8cedad153bee69540
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2018
---
# <a name="bcpinit"></a>bcp_init
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  一括コピー操作を初期化します。  
  
## <a name="syntax"></a>構文  
  
```  
  
RETCODE bcp_init (  
        HDBC hdbc,  
        LPCTSTR szTable,  
        LPCTSTR szDataFile,  
        LPCTSTR szErrorFile,  
        INT eDirection);  
```  
  
## <a name="arguments"></a>引数  
 *hdbc*  
 一括コピーが有効な ODBC 接続ハンドルです。  
  
 *szTable*  
 コピー操作の対象になるデータベース テーブルの名前です。 この名前には、データベース名または所有者名を含めることもできます。 たとえば、 **pubs.gracie.titles**、 **pubs.タイトル**、 **gracie.titles**、および**タイトル**はすべての有効なテーブル名。  
  
 場合*eDirection* DB_OUT では、 *szTable*データベース ビューの名前をすることもできます。  
  
 場合*eDirection* DB_OUT を使用して、SELECT ステートメントを指定して[bcp_control](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-control.md)する前に[bcp_exec](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md)が呼び出されると、 **bcp_init** *szTable* NULL に設定する必要があります。  
  
 *szDataFile*  
 コピー操作の対象になるユーザー ファイルの名前です。 変数から直接使用して、データがコピーされる[bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md)設定、 *szDataFile*を NULL にします。  
  
 *szErrorFile*  
 進行状況メッセージ、エラー メッセージ、および何かの理由でユーザー ファイルからテーブルにコピーできなかった任意の行のコピーを書き込むエラー ファイルの名前です。 として NULL を渡す場合*szErrorFile*、エラー ファイルは使用されません。  
  
 *eDirection*  
 コピーの方向です。この値は DB_IN または DB_OUT になります。 DB_IN は、プログラム変数またはユーザー ファイルからテーブルへのコピーを示します。 DB_OUT は、データベース テーブルからユーザー ファイルへのコピーを示します。 DB_OUT を指定する場合は、ユーザー ファイル名を指定する必要があります。  
  
## <a name="returns"></a>返します。  
 SUCCEED または FAIL。  
  
## <a name="remarks"></a>解説  
 呼び出す**bcp_init**他の一括コピー関数を呼び出す前にします。 **bcp_init**ワークステーション間でデータの一括コピーに必要な初期化を実行し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
 **Bcp_init**関数は、一括コピー関数で使用できる ODBC 接続ハンドルと共に指定する必要があります。 ハンドルを有効にするには、 [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) SQL_COPT_SS_BCP を SQL_BCP_ON に設定する、割り当て済みですが、接続されていない接続ハンドルの使用。 接続済みのハンドルの属性を割り当てようとすると、エラーが発生します。  
  
 データ ファイルを指定すると、 **bcp_init**データベース ソースまたはターゲット テーブルのデータ ファイルではなく構造を調べます。 **bcp_init**データベース テーブル、ビュー、または SELECT 結果セット内の各列に基づいてデータ ファイルのデータ形式値を指定します。 このデータ形式値には、各列のデータ型、長さや NULL のインジケーターとターミネータのバイト文字列がデータ内に存在するかどうか、および固定長データ型の幅の指定などが含まれます。 **bcp_init**これらの値を次のように設定します。  
  
-   指定するデータ型は、データベース テーブル、ビュー、または SELECT 結果セット内の列のデータ型です。 データ型は、sqlncli.h に指定されている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ネイティブ データ型によって列挙されます。 データ自体はそのコンピューターの形式で表されます。 列のデータは、**整数**データ型は、ビッグ 4 バイトのシーケンスで表される、またはリトル エンディアン データ ファイルを作成したコンピューターに基づいて。  
  
-   データベースのデータ型が固定長の場合は、データ ファイルのデータも固定長になります。 データを処理する一括コピー関数 (たとえば、 [bcp_exec](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md)) と同じデータベース テーブル、ビュー、または SELECT 列リストで指定されるデータの長さにするデータ ファイル内のデータの長さはデータ行を解析します。 たとえば、列のデータはデータベースとして定義されている**char (13)**ファイル内のデータの行ごとに 13 文字で表される必要があります。 データベース列で NULL 値を許容する場合は、固定長データにプレフィックスとして NULL インジケーターを付けることができます。  
  
-   ターミネータ バイト シーケンスを定義すると、ターミネータ バイト シーケンスの長さが 0 に設定されます。  
  
-   データを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にコピーするときは、データ ファイルにデータベース テーブル内の各列に格納するデータが含まれている必要があります。 データを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からコピーするときは、データベース テーブル、ビュー、または SELECT 結果セット内のすべての列のデータがデータ ファイルにコピーされます。  
  
-   データを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にコピーするときは、データ ファイル内の列の序数位置がデータベース テーブル内の列の序数位置と同じであることが必要です。 コピーするときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、 **bcp_exec**データベース テーブルの列の序数位置に基づいてデータを配置します。  
  
-   データベースのデータ型が可変長である場合 (たとえば、 **varbinary(22)**) またはデータ ファイル内のデータを長さや null インジケーターを付けた場合は、データベース列で null 値を含めることができます。 インジケーターの幅は、データ型と一括コピーのバージョンによって異なります。  
  
 データ ファイルに指定されたデータ形式値を変更するには、呼び出す[bcp_columns](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md)と[bcp_colfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md)です。  
  
 インデックスを含まないテーブルの場合は、データベース復旧モデルを SIMPLE または BULK_LOGGED に設定することで、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] への一括コピーを最適化できます。 詳細については、次を参照してください。[一括インポートで最小ログ記録の前提条件](../../relational-databases/import-export/prerequisites-for-minimal-logging-in-bulk-import.md)と[ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md)です。  
  
 データ ファイルを使用しない場合を呼び出す必要があります[bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)形式と場所の各列のデータをメモリを指定するデータ行をコピーし、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を使用して[bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md)です。  
  
## <a name="example"></a>例  
 このサンプルでは、ODBC bcp_init 関数をフォーマット ファイルと共に使用する方法を示します。  
  
 この C++ コードをコンパイルして実行する前に、次の手順を実行する必要があります。  
  
-   Test という ODBC データ ソースを作成し、 任意のデータベースに関連付けます。  
  
-   そのデータベースに対して次の [!INCLUDE[tsql](../../includes/tsql-md.md)] を実行します。  
  
    ```  
    CREATE TABLE BCPDate (cola int, colb datetime);  
    ```  
  
-   アプリケーションを実行するディレクトリに Bcpfmt.fmt というファイルを追加して、そのファイルに次の内容を追加します。  
  
    ```  
    8.0  
    2  
    1SQLCHAR04"\t"1colaSQL_Latin1_General_Cp437_Bin  
    2SQLCHAR08"\r\n"2colbSQL_Latin1_General_Cp437_Bin  
    ```  
  
-   アプリケーションを実行するディレクトリに Bcpodbc.bcp というファイルを追加して、そのファイルに次の内容を追加します。  
  
    ```  
    1  
    2  
    ```  
  
 以上で、この C++ コードをコンパイルして実行できるようになりました。  
  
```  
// compile with: odbc32.lib sqlncli11.lib  
#include <stdio.h>  
#include <windows.h>  
#include <sql.h>  
#include <sqlext.h>  
#include <odbcss.h>  
  
SQLHENV henv = SQL_NULL_HENV;  
HDBC hdbc1 = SQL_NULL_HDBC;   
  
void Cleanup() {  
   if (hdbc1 != SQL_NULL_HDBC) {  
      SQLDisconnect(hdbc1);  
      SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   }  
  
   if (henv != SQL_NULL_HENV)  
      SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
  
int main() {  
   RETCODE retcode;  
   SDWORD cRows;  
  
   // Allocate the ODBC environment and save handle.  
   retcode = SQLAllocHandle (SQL_HANDLE_ENV, NULL, &henv);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(Env) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Notify ODBC that this is an ODBC 3.0 app.  
   retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER) SQL_OV_ODBC3, SQL_IS_INTEGER);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLSetEnvAttr(ODBC version) Failed\n\n");  
      Cleanup();  
      return(9);      
   }  
  
   // Allocate ODBC connection handle, set BCP mode, and connect.  
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc1);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   retcode = SQLSetConnectAttr(hdbc1, SQL_COPT_SS_BCP, (void *)SQL_BCP_ON, SQL_IS_INTEGER);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLSetConnectAttr(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Sample uses Integrated Security. Create SQL Server DSN using Windows NT authentication.  
   retcode = SQLConnect(hdbc1, (UCHAR*)"Test", SQL_NTS, (UCHAR*)"", SQL_NTS, (UCHAR*)"", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLConnect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Initialize the bulk copy.  
   retcode = bcp_init(hdbc1, "BCPDate", "BCPODBC.bcp", NULL, DB_IN);  
   if ( (retcode != SUCCEED) ) {  
      printf("bcp_init(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Read the format file.  
   retcode = bcp_readfmt(hdbc1, "BCPFMT.fmt");  
   if ( (retcode != SUCCEED) ) {  
      printf("bcp_readfmt(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Execute the bulk copy.  
   retcode = bcp_exec(hdbc1, &cRows);  
   if ( (retcode != SUCCEED) ) {  
      printf("bcp_exec(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   printf("Number of rows bulk copied in = %d.\n", cRows);  
  
   // Cleanup  
   SQLDisconnect(hdbc1);  
   SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
  
```  
  
## <a name="see-also"></a>参照  
 [一括コピー関数](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  

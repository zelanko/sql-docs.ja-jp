---
title: bcp_bind |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- bcp_bind
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_bind function
ms.assetid: 6e335a5c-64b2-4bcf-a88f-35dc9393f329
caps.latest.revision: 47
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c7fa336f3e2c7820dfbd2a6f9707f6119c6e9b09
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43085094"
---
# <a name="bcpbind"></a>bcp_bind
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に一括コピーするために、プログラム変数からテーブル列にデータをバインドします。  
  
## <a name="syntax"></a>構文  
  
```  
  
RETCODE bcp_bind (  
        HDBC hdbc,   
        LPCBYTE pData,  
        INT cbIndicator,  
        DBINT cbData,  
        LPCBYTE pTerm,  
        INT cbTerm,  
        INT eDataType,  
        INT idxServerCol);  
```  
  
## <a name="arguments"></a>引数  
 *hdbc*  
 一括コピーが有効な ODBC 接続ハンドルです。  
  
 *pData*  
 データへのポインターがコピーされます。 場合*eDataType*が SQLTEXT、SQLNTEXT、SQLXML、SQLUDT、SQLCHARACTER、SQLVARCHAR、SQLVARBINARY、SQLBINARY、SQLNCHAR または sqlimage の場合、 *pData* NULL を指定できます。 NULL *pData*を長い形式のデータ値が送信されることを示します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を使用してまとめて[bcp_moretext](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md)します。 ユーザーを設定する必要がありますのみ*pData*が BLOB 列のそれ以外の場合、バインドするフィールドに対応する列の場合は NULL に**bcp_bind**は失敗します。  
  
 データ内にインジケーターが存在する場合、それらのインジケーターはメモリ内ではデータの直前にあります。 *PData*パラメーターがこの場合と、インジケーターの幅はインジケーター変数を指す、 *cbIndicator*アドレスのユーザー データを一括コピーでは、パラメーターが正しく使用されています。  
  
 *cbIndicator*  
 列のデータに関する長さのインジケーターや NULL インジケーターのバイト単位の長さです。 インジケーターの長さの有効値は、0 (インジケーターを使用しない場合)、1、2、4、または 8 です。 インジケーターは、メモリ内ではすべてのデータの直前にあります。 たとえば、一括コピーを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルに整数値を挿入するには、次のような構造体の型定義を使用します。  
  
```  
typedef struct tagBCPBOUNDINT  
    {  
    int iIndicator;  
    int Value;  
    } BCPBOUNDINT;  
```  
  
 例の場合、 *pData*パラメーターは、宣言された構造体、つまり、BCPBOUNDINT のアドレスのインスタンスのアドレスに設定されます*iIndicator*構造体のメンバー。 *CbIndicator*パラメーターは整数のサイズに設定されます (sizeof と*cbData* (sizeof(int)) 整数のサイズにパラメーターを設定するともう一度。 インスタンスの値、バインドされた列の値の null 値を格納しているサーバーへの行の一括コピーする*iIndicator* SQL_NULL_DATA にメンバーを設定する必要があります。  
  
 *cbData*  
 プログラム変数内のデータのバイト数です。長さのインジケーター、NULL インジケーター、およびターミネータの長さは含まれません。  
  
 設定*cbData* SQL_NULL_DATA をサーバーにコピーされるすべての行に列の NULL 値があることを示します。  
  
 設定*cbData*を SQL_VARLEN_DATA またはことを示します、システムが、文字列ターミネータを使用してデータの長さを決定するその他のメソッドをコピーします。  
  
 整数などの固定長データ型の場合、データ型によってデータの長さがシステムに示されます。 そのため、固定長データ型の*cbData* SQL_VARLEN_DATA にしても、データの長さを安全にすることができます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]文字やバイナリ データ型、 *cbData* SQL_VARLEN_DATA、SQL_NULL_DATA、正の値、または 0 にすることができます。 場合*cbData* SQL_VARLEN_DATA は、システムは、長さや null インジケーター (存在する場合) またはターミネータ シーケンスのいずれかを使用して、データの長さを決定します。 インジケーターとターミネータ シーケンスの両方を指定した場合、システムでは、コピーされるデータ量が少なくなる方法が使用されます。 場合*cbData* SQL_VARLEN_DATA には、列のデータ型は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]文字またはバイナリの型と長さのインジケーターもターミネータ シーケンスを指定すると、システムには、エラー メッセージが返されます。  
  
 場合*cbData*が 0 または正の値をシステムを使用して*cbData*データ長として。 ただし、正の値の場合、 *cbData*長さのインジケーターとターミネータ シーケンスを指定する値をコピーするデータ量が少なくなる方法を使用してデータの長さを決定します。  
  
 *CbData*パラメーターの値は、データのバイト数を表します。 文字データが Unicode ワイド文字では、正の値で表されている場合*cbData*パラメーターの値は、各文字のバイト単位のサイズを乗算する文字数を表します。  
  
 *pTerm*  
 このプログラム変数の終了位置をマークするバイト パターンがある場合、そのバイト パターンを指すポインターです。 たとえば、通常、ANSI 文字列と MBCS C 文字列には 1 バイトのターミネータ (\0) があります。  
  
 変数にターミネータがない場合は、設定*pTerm*を NULL にします。  
  
 C NULL ターミネータをプログラム変数のターミネータとして指定する場合、空文字列 ("") を使用できます。 Null で終わる空の文字列が 1 バイト (ターミネータのバイト自体) を構成するため、設定*cbTerm*を 1 にします。 たとえば、あることを示す内の文字列*szName*が null で終わる、長さを示すために、終端記号を使用することと。  
  
```  
bcp_bind(hdbc, szName, 0,  
   SQL_VARLEN_DATA, "", 1,  
   SQLCHARACTER, 2)  
```  
  
 この例の文字列形式はから 15 文字をコピーすることを示す可能性があります、 *szName*変数にバインドされたテーブルの 2 番目の列。  
  
```  
bcp_bind(hdbc, szName, 0, 15,   
   NULL, 0, SQLCHARACTER, 2)  
```  
  
 一括コピー API では、必要に応じて Unicode から MBCS への文字変換が実行されます。 ターミネータのバイト文字列とそのバイト文字列の長さの両方を正しく設定してください。 たとえば、あることを示すで文字列*szName* Unicode null ターミネータ値で終わる Unicode ワイド文字の文字列は。  
  
```  
bcp_bind(hdbc, szName, 0,   
   SQL_VARLEN_DATA, L"",  
   sizeof(WCHAR), SQLNCHAR, 2)  
```  
  
 場合、バインドされた[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]列がワイド文字での変換は行われません[bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md)します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 列が MBCS 文字型の場合、データが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に送信されるときに、ワイド文字がマルチバイト文字に変換されます。  
  
 *cbTerm*  
 プログラム変数にターミネータがある場合は、そのターミネータを構成するバイト数です。 変数にターミネータがない場合は、設定*cbTerm*を 0 にします。  
  
 *eDataType*  
 プログラム変数の C データ型です。 プログラム変数内のデータは、データベース列の型に変換されます。 このパラメーターが 0 の場合、変換は実行されません。  
  
 *EDataType*パラメーターは列挙型によって、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sqlncli.h 内のデータ型のトークン、しない、ODBC C データ型の列挙子。 たとえば、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 固有の SQLINT2 型を使用して、ODBC の SQL_C_SHORT 型の 2 バイトの整数を指定できます。  
  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SQLXML および SQLUDT データ型のトークンでのサポートが導入され、 ***eDataType***パラメーター。  
 
 次の表では、有効な列挙データ型と対応する ODBC C データ型の一覧を示します。
  
|eDataType|C 型|  
|-----------------------|------------|  
|SQLTEXT|char *|  
|SQLNTEXT|wchar_t *|  
|SQLCHARACTER|char *|  
|SQLBIGCHAR|char *|  
|SQLVARCHAR|char *|  
|SQLBIGVARCHAR|char *|  
|SQLNCHAR|wchar_t *|  
|SQLNVARCHAR|wchar_t *|  
|SQLBINARY|unsigned char *|  
|SQLBIGBINARY|unsigned char *|  
|SQLVARBINARY|unsigned char *|  
|SQLBIGVARBINARY|unsigned char *|  
|SQLBIT|char|  
|SQLBITN|char|  
|SQLINT1|char|  
|SQLINT2|short int|  
|SQLINT4|ssNoversion|  
|SQLINT8|_int64|  
|SQLINTN|*cbIndicator*<br /> 1: SQLINT1<br /> 2: SQLINT2<br /> 4: SQLINT4<br /> 8: SQLINT8|  
|SQLFLT4|FLOAT|  
|SQLFLT8|FLOAT|  
|SQLFLTN|*cbIndicator*<br /> 4: SQLFLT4<br /> 8: SQLFLT8|  
|SQLDECIMALN|SQL_NUMERIC_STRUCT|  
|SQLNUMERICN|SQL_NUMERIC_STRUCT|  
|SQLMONEY|DBMONEY|  
|SQLMONEY4|DBMONEY4|  
|SQLMONEYN|*cbIndicator*<br /> 4: SQLMONEY4<br /> 8: SQLMONEY|  
|SQLTIMEN|SQL_SS_TIME2_STRUCT|  
|SQLDATEN|SQL_DATE_STRUCT|  
|SQLDATETIM4|DBDATETIM4|  
|SQLDATETIME|DBDATETIME|  
|SQLDATETIMN|*cbIndicator*<br /> 4: SQLDATETIM4<br /> 8: SQLDATETIME|  
|SQLDATETIME2N|SQL_TIMESTAMP_STRUCT|  
|SQLDATETIMEOFFSETN|SQL_SS_TIMESTAMPOFFSET_STRUCT|  
|SQLIMAGE|unsigned char *|  
|SQLUDT|unsigned char *|  
|SQLUNIQUEID|SQLGUID|  
|SQLVARIANT|*以下を除く任意のデータ型:*<br />-   text<br />-   ntext<br />-   image<br />-   varchar(max)<br />-   varbinary(max)<br />-   nvarchar(max)<br />-   xml<br />-   timestamp|  
|SQLXML|*サポートされる C のデータ型*<br />-   char*<br />-   wchar_t *<br />-   unsigned char *|  
  
 *idxServerCol*  
 データベース テーブル内にある、データのコピー先となる列の序数位置です。 テーブル内の最初の列は列 1 です。 列の序数位置がによって報告された[SQLColumns](../../relational-databases/native-client-odbc-api/sqlcolumns.md)します。  
  
## <a name="returns"></a>戻り値  
 SUCCEED または FAIL。  
  
## <a name="remarks"></a>コメント  
 使用**bcp_bind**プログラム変数からのテーブルにデータをコピーする高速で効率的な方法を[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。  
  
 呼び出す[bcp_init](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-init.md)これまたは他の一括コピー関数を呼び出す前にします。 呼び出す**bcp_init**設定、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]一括コピー先のテーブル。 呼び出すときに**bcp_init**で使用するため**bcp_bind**と[bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md)、 **bcp_init** *szDataFile*、データ ファイルを示すパラメーターが NULL に設定されています。**bcp_init * * * eDirection*パラメーターが DB_IN に設定されます。  
  
 個別**bcp_bind**の各列に対して呼び出し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をコピーするテーブル。 後、必要な**bcp_bind**呼び出しが行われているし、呼び出す**bcp_sendrow**をプログラム変数からのデータ行を送信する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 列の再バインドはサポートされていません。  
  
 必要な場合に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を既に受信した行をコミットするには、呼び出す[bcp_batch](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-batch.md)します。 たとえば、呼び出す**bcp_batch** 1000 行が挿入されるたびに、またはその他の任意の間隔で 1 回です。  
  
 挿入する行がこれ以上が存在する場合、呼び出す[bcp_done](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-done.md)します。 この操作を行わないと、エラーが発生します。  
  
 指定されたパラメーターの設定を制御[bcp_control](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-control.md)、の影響はありません**bcp_bind**行転送します。  
  
 場合*pData*はその値への呼び出しによって指定されるため、列が NULL に設定されて[bcp_moretext](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md)、以降のすべての列で*eDataType* SQLTEXT、SQLNTEXT に設定SQLXML、SQLUDT、SQLCHARACTER、SQLVARCHAR、SQLVARBINARY、SQLBINARY、SQLNCHAR、または SQLIMAGE をバインドする必要がありますも*pData*は NULL に設定し、その値への呼び出しによっても指定する必要があります**bcp_moretext**.  
  
 新しい大きな値型など**varchar (max)**、 **varbinary (max)**、または**nvarchar (max)** SQLCHARACTER、SQLVARCHAR、SQLVARBINARY、SQLBINARY を使用してSQLNCHAR で型を表すインジケーターとして、 *eDataType*パラメーター。  
  
 場合*cbTerm*は任意の値 (1、2、4、または 8) は、プレフィックス、0 ではありません (*cbIndicator*)。 このような状況で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client は、終端文字の検索、ターミネータを基準データの長さを計算 (*は*) を設定し、 *cbData* i の値と値を小さくするプレフィックス。  
  
 場合*cbTerm*は 0 と*cbIndicator* (プレフィックス) が 0、 *cbIndicator* 8 にする必要があります。 8 バイトのプレフィックスでは、次の値を受け取ることができます。  
  
-   0xFFFFFFFFFFFFFFFF は、フィールドの NULL 値を示します。  
  
-   0xFFFFFFFFFFFFFFFE は、データをチャンク単位でサーバーに効率的に送信するために使用する特別なプレフィックスの値として処理されます。 この特別なプレフィックス値を含むデータは、次のような形式になります。  
  
-   < SPECIAL_PREFIX > \<0 または複数のデータ チャンク >< ZERO_CHUNK > 場所。  
  
-   SPECIAL_PREFIX には 0xFFFFFFFFFFFFFFFE を指定します。  
  
-   DATA_CHUNK には、チャンクの長さを含む 4 バイトのプレフィックスを指定し、その後に 4 バイトのプレフィックスで長さを指定した実際のデータを指定します。  
  
-   ZERO_CHUNK には、データの終了を示す、すべてがゼロの 4 バイトの値 (00000000) を指定します。  
  
-   その他の有効な 8 バイト長は、通常のデータ長として処理されます。  
  
 呼び出す[bcp_columns](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md)を使用する場合**bcp_bind**エラーが発生します。  
  
## <a name="bcpbind-support-for-enhanced-date-and-time-features"></a>bcp_bind による機能強化された日付と時刻のサポート  
 使用される型については、 *eDataType*日付/時刻の型のパラメーターを参照してください[強化された日付と時刻型向けの一括コピーの変更&#40;OLE DB および ODBC&#41;](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)します。  
  
 詳細については、次を参照してください。[日付と時刻の強化&#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)します。  
  
## <a name="example"></a>例  
  
```  
#include sql.h  
#include sqlext.h  
#include odbcss.h  
// Variables like henv not specified.  
HDBC      hdbc;  
char         szCompanyName[MAXNAME];  
DBINT      idCompany;  
DBINT      nRowsProcessed;  
DBBOOL      bMoreData;  
char*      pTerm = "\t\t";  
  
// Application initiation, get an ODBC environment handle, allocate the  
// hdbc, and so on.  
...   
  
// Enable bulk copy prior to connecting on allocated hdbc.  
SQLSetConnectAttr(hdbc, SQL_COPT_SS_BCP, (SQLPOINTER) SQL_BCP_ON,  
   SQL_IS_INTEGER);  
  
// Connect to the data source; return on error.  
if (!SQL_SUCCEEDED(SQLConnect(hdbc, _T("myDSN"), SQL_NTS,  
   _T("myUser"), SQL_NTS, _T("myPwd"), SQL_NTS)))  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Initialize bcp.   
if (bcp_init(hdbc, "comdb..accounts_info", NULL, NULL  
   DB_IN) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Bind program variables to table columns.   
if (bcp_bind(hdbc, (LPCBYTE) &idCompany, 0, sizeof(DBINT), NULL, 0,  
   SQLINT4, 1)    == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
if (bcp_bind(hdbc, (LPCBYTE) szCompanyName, 0, SQL_VARLEN_DATA,  
   (LPCBYTE) pTerm, strnlen(pTerm, sizeof(pTerm)), SQLCHARACTER, 2) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
while (TRUE)  
   {  
   // Retrieve and process program data.   
   if ((bMoreData = getdata(&idCompany, szCompanyName)) == TRUE)  
      {  
      // Send the data.   
      if (bcp_sendrow(hdbc) == FAIL)  
         {  
         // Raise error and return.  
         return;  
         }  
      }  
   else  
      {  
      // Break out of loop.  
      break;  
      }  
   }  
  
// Terminate the bulk copy operation.  
if ((nRowsProcessed = bcp_done(hdbc)) == -1)  
   {  
   printf_s("Bulk-copy unsuccessful.\n");  
   return;  
   }  
  
printf_s("%ld rows copied.\n", nRowsProcessed);  
```  
  
## <a name="see-also"></a>参照  
 [一括コピー関数](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  

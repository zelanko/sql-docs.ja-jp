---
title: bcp_bind |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_bind
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_bind function
ms.assetid: 6e335a5c-64b2-4bcf-a88f-35dc9393f329
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 711c82bb627ca9ad1620cf1e11fdbc9dfa5f4351
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "63140565"
---
# <a name="bcp_bind"></a>bcp_bind
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に一括コピーするために、プログラム変数からテーブル列にデータをバインドします。  
  
## <a name="syntax"></a>構文  
  
```  
  
RETCODE bcp_bind (  
HDBC   
hdbc  
,   
LPCBYTE   
pData  
,  
INT   
cbIndicator  
,  
DBINT   
cbData  
,  
LPCBYTE   
pTerm  
,  
INT   
cbTerm  
,  
INT   
eDataType  
,  
INT   
idxServerCol  
);  
  
```  
  
## <a name="arguments"></a>引数  
 *hdbc*  
 一括コピーが有効な ODBC 接続ハンドルです。  
  
 *pData*  
 コピーされたデータへのポインターです。 *Edatatype*が SQLTEXT、SQLNTEXT、SQLXML、sqlntext、sqlntext、sqlntext、sqlntext、SQLNTEXT、sqlntext、または SQLIMAGE の場合は、 *pData*を NULL にすることができます。 NULL *pData*は、長いデータ値が[bcp_moretext](bcp-moretext.md)を使用し[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]てチャンクに送信されることを示します。 ユーザーは、ユーザーバインドフィールドに対応する列が BLOB 列の場合、 *pData*を NULL に設定する必要があります。それ以外の場合、 **bcp_bind**は失敗します。  
  
 データ内にインジケーターが存在する場合、それらのインジケーターはメモリ内ではデータの直前にあります。 この場合、 *pData*パラメーターはインジケーター変数を指します。インジケーターの幅 ( *cbindicator*パラメーター) は、一括コピーによってユーザーデータを正しくアドレス指定するために使用されます。  
  
 *cbIndicator*  
 列のデータに関する長さのインジケーターや NULL インジケーターのバイト単位の長さです。 インジケーターの長さの有効値は、0 (インジケーターを使用しない場合)、1、2、4、または 8 です。 インジケーターは、メモリ内ではすべてのデータの直前にあります。 たとえば、一括コピーを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルに整数値を挿入するには、次のような構造体の型定義を使用します。  
  
```  
typedef struct tagBCPBOUNDINT  
    {  
    int iIndicator;  
    int Value;  
    } BCPBOUNDINT;  
```  
  
 この例では、 *pData*パラメーターは、構造体の宣言されたインスタンスのアドレス (BCPBOUNDINT *iindicator*構造体メンバーのアドレス) に設定されます。 *Cbindicator*パラメーターは整数のサイズ (sizeof (int)) に設定され、 *cbindicator*パラメーターはもう一度整数のサイズ (sizeof (int)) に設定されます。 バインドされた列に NULL 値が含まれているサーバーに行を一括コピーするには、インスタンスの*Iindicator*メンバーの値を SQL_NULL_DATA に設定する必要があります。  
  
 *cbData*  
 プログラム変数内のデータのバイト数です。長さのインジケーター、NULL インジケーター、およびターミネータの長さは含まれません。  
  
 *Cbdata*を SQL_NULL_DATA に設定すると、サーバーにコピーされるすべての行に列の NULL 値が格納されます。  
  
 *Cbdata*を SQL_VARLEN_DATA に設定すると、システムは、文字列ターミネータ (またはその他の方法) を使用してコピーされるデータの長さを決定します。  
  
 整数などの固定長データ型の場合、データ型によってデータの長さがシステムに示されます。 したがって、固定長データ型の場合は、 *Cbdata*を安全に SQL_VARLEN_DATA することも、データの長さを指定することもできます。  
  
 文字[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型およびバイナリデータ型の場合、 *cbdata*には SQL_VARLEN_DATA、SQL_NULL_DATA、正の値、または0を指定できます。 *Cbdata*が SQL_VARLEN_DATA 場合、システムは長さ/null インジケーター (存在する場合) またはターミネータシーケンスを使用してデータの長さを決定します。 インジケーターとターミネータ シーケンスの両方を指定した場合、システムでは、コピーされるデータ量が少なくなる方法が使用されます。 *Cbdata*が SQL_VARLEN_DATA 場合、列のデータ型は[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]文字型またはバイナリ型で、長さのインジケーターもターミネータシーケンスも指定されていないと、システムはエラーメッセージを返します。  
  
 *Cbdata*が0または正の値の場合、システムではデータ長として*cbdata*が使用されます。 ただし、正の*Cbdata*値に加えて、長さのインジケーターまたはターミネータシーケンスが指定されている場合、システムは、コピーされるデータ量が最小になるメソッドを使用してデータ長を決定します。  
  
 *Cbdata*パラメーター値は、データのバイト数を表します。 文字データが Unicode ワイド文字で表されている場合、 *cbdata*パラメーターの正の値は、各文字のサイズ (バイト単位) を乗算した文字数を表します。  
  
 *pTerm*  
 このプログラム変数の終了位置をマークするバイト パターンがある場合、そのバイト パターンを指すポインターです。 たとえば、通常、ANSI 文字列と MBCS C 文字列には 1 バイトのターミネータ (\0) があります。  
  
 変数にターミネータがない場合は、 *Pterm*を NULL に設定します。  
  
 C NULL ターミネータをプログラム変数のターミネータとして指定する場合、空文字列 ("") を使用できます。 Null で終わる空の文字列は1バイト (ターミネータバイト自体) を構成するので、 *Cbterm*を1に設定します。 たとえば、 *szName*の文字列が null で終了し、長さを示すためにターミネータを使用する必要があることを示すには、次のようにします。  
  
```  
bcp_bind(hdbc, szName, 0,  
   SQL_VARLEN_DATA, "", 1,  
   SQLCHARACTER, 2)  
```  
  
 この例では、終了しない形式の場合、 *szName*変数からバインドされたテーブルの2番目の列に15文字をコピーすることを示している可能性があります。  
  
```  
bcp_bind(hdbc, szName, 0, 15,   
   NULL, 0, SQLCHARACTER, 2)  
```  
  
 一括コピー API では、必要に応じて Unicode から MBCS への文字変換が実行されます。 ターミネータのバイト文字列とそのバイト文字列の長さの両方を正しく設定してください。 たとえば、 *szName*の文字列が unicode ワイド文字列で、unicode の null 終端記号の値によって終了することを示すには、次のように指定します。  
  
```  
bcp_bind(hdbc, szName, 0,   
   SQL_VARLEN_DATA, L"",  
   sizeof(WCHAR), SQLNCHAR, 2)  
```  
  
 バインド[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]された列がワイド文字の場合、 [bcp_sendrow](bcp-sendrow.md)に対して変換は実行されません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 列が MBCS 文字型の場合、データが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に送信されるときに、ワイド文字がマルチバイト文字に変換されます。  
  
 *cbTerm*  
 プログラム変数にターミネータがある場合は、そのターミネータを構成するバイト数です。 変数にターミネータがない場合は、 *Cbterm*を0に設定します。  
  
 *eDataType*  
 プログラム変数の C データ型です。 プログラム変数内のデータは、データベース列の型に変換されます。 このパラメーターが 0 の場合、変換は実行されません。  
  
 *Edatatype*パラメーターは、ODBC C データ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型の列挙子ではなく、sqlncli のデータ型のトークンによって列挙されます。 たとえば、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 固有の SQLINT2 型を使用して、ODBC の SQL_C_SHORT 型の 2 バイトの整数を指定できます。  
  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]では、paramenter での SQLXML および SQLUDT データ*`eDataType`* 型のトークンのサポートが導入されました。  
  
 *idxServerCol*  
 データベース テーブル内にある、データのコピー先となる列の序数位置です。 テーブル内の最初の列は列 1 です。 列の序数位置は[Sqlcolumns](../native-client-odbc-api/sqlcolumns.md)によって報告されます。  
  
## <a name="returns"></a>戻り値  
 SUCCEED または FAIL。  
  
## <a name="remarks"></a>Remarks  
 プログラム**bcp_bind**変数からの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブルにデータをコピーする高速で効率的な方法には、bcp_bind を使用します。  
  
 このまたはその他の一括コピー関数を呼び出す前に[bcp_init](bcp-init.md)を呼び出してください。 **Bcp_init**を呼び出す[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と、一括コピーの対象テーブルが設定されます。 **Bcp_bind**と[bcp_sendrow](bcp-sendrow.md)で使用するために**bcp_init**を呼び出すと、データファイルを示す**BCP_INIT**の_szdatafile_ファイルパラメーターが NULL に設定されます。**bcp_init**_edirection_パラメーターが DB_IN に設定されています。  
  
 コピー先の**bcp_bind** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブル内のすべての列に対して、個別の bcp_bind 呼び出しを作成します。 必要な**bcp_bind**の呼び出しが行われたら、 **bcp_sendrow**を呼び出して、プログラム変数からに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ行を送信します。 列の再バインドはサポートされていません。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]既に受信した行をコミットする場合は常に、 [bcp_batch](bcp-batch.md)を呼び出します。 たとえば、1000行が挿入されるたびに、またはその他の間隔で1回**bcp_batch**を呼び出します。  
  
 挿入する行がなくなった場合は、 [bcp_done](bcp-done.md)を呼び出します。 この操作を行わないと、エラーが発生します。  
  
 [Bcp_control](bcp-control.md)で指定されたコントロールパラメーターの設定は、 **bcp_bind**の行転送には影響しません。  
  
 列の値が[bcp_moretext](bcp-moretext.md)の呼び出しによって指定されるため、列の*pData*が null に設定されている場合は、 *EDATATYPE*が SQLTEXT、SQLNTEXT、SQLXML、SQLNTEXT、SQLNTEXT、SQLNTEXT、SQLNTEXT、sqlntext、sqlntext、または SQLIMAGE に設定されている後続の列も*pdata*に設定する必要`bcp_moretext`があります。また  
  
 `varchar(max)`、 `varbinary(max)`、 `nvarchar(max)`などの新しい大きな値型の場合は、 *edatatype*パラメーターで型インジケーターとして sqlcharacter、sqlcharacter、sqlcharacter、sqlcharacter、および sqlcharacter を使用できます。  
  
 *Cbterm*が0でない場合は、すべての値 (1、2、4、または 8) がプレフィックス (*cbterm*) に対して有効です。 この場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client はターミネータを検索し、ターミネータ (*i*) に対してデータの長さを計算し、 *cbdata*を i の小さい値と prefix の値に設定します。  
  
 *Cbterm*が0で、 *cbterm* (プレフィックス) が0でない場合、 *cbterm*は8である必要があります。 8 バイトのプレフィックスでは、次の値を受け取ることができます。  
  
-   0xFFFFFFFFFFFFFFFF は、フィールドの NULL 値を示します。  
  
-   0xFFFFFFFFFFFFFFFE は、データをチャンク単位でサーバーに効率的に送信するために使用する特別なプレフィックスの値として処理されます。 この特別なプレフィックス値を含むデータは、次のような形式になります。  
  
-   <SPECIAL_PREFIX> \<0 個以上のデータチャンク> <ZERO_CHUNK> ます。  
  
-   SPECIAL_PREFIX には 0xFFFFFFFFFFFFFFFE を指定します。  
  
-   DATA_CHUNK には、チャンクの長さを含む 4 バイトのプレフィックスを指定し、その後に 4 バイトのプレフィックスで長さを指定した実際のデータを指定します。  
  
-   ZERO_CHUNK には、データの終了を示す、すべてがゼロの 4 バイトの値 (00000000) を指定します。  
  
-   その他の有効な 8 バイト長は、通常のデータ長として処理されます。  
  
 **Bcp_bind**を使用するときに[bcp_columns](bcp-columns.md)を呼び出すと、エラーが発生します。  
  
## <a name="bcp_bind-support-for-enhanced-date-and-time-features"></a>bcp_bind による機能強化された日付と時刻のサポート  
 日付型または時刻型の*Edatatype*パラメーターで使用される型の詳細については、「 [&#40;OLE DB および ODBC&#41;の拡張された日付/時刻型に対する一括コピーの変更](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)」を参照してください。  
  
 詳細については、「[日付と時刻の機能強化 &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)」を参照してください。  
  
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
 [一括コピー関数](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  

---
title: "プログラム変数から一括コピー |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-bulk-copy-operations
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC], program variables
- bcp_bind function
- mapping data types [ODBC]
- SQL Server Native Client ODBC driver, bulk copy
- data types [ODBC], bulk copying
- ODBC, bulk copy operations
- program variables [ODBC]
ms.assetid: e4284a1b-7534-4b34-8488-b8d05ed67b8c
caps.latest.revision: "31"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 603d759724fd7a634e6cc4b53ccb5302ccb56816
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="bulk-copying-from-program-variables"></a>プログラム変数からの一括コピー
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  プログラム変数から直接一括コピーできます。 行と呼び出し元のデータを保持する変数を割り当て後[bcp_init](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-init.md)一括コピーを開始するには、呼び出す[bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)を関連付けるプログラム変数の形式と場所を指定するには、各列の列です。 各変数を入力にデータを呼び出して[bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md)をサーバーに 1 行のデータを送信します。 変数を入力し、呼び出す手順を繰り返す**bcp_sendrow**のすべての行がサーバーに送信される、まで、呼び出し[bcp_done](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-done.md)操作が完了したことを指定します。  
  
 **Bcp_bind***pData*パラメーターには、列にバインドされている変数のアドレスが含まれています。 各列のデータは、次の 2 つの方法のいずれかを使用して格納できます。  
  
-   データを保持する変数を 1 つ割り当てる  
  
-   データ変数の直前にインジケーター変数を割り当てる  
  
 インジケーター変数は、可変長列のデータの長さを示します。列で NULL 値を許容している場合は NULL 値も示します。 データ変数を使用すると、専用の場合、この変数のアドレスに格納されます、 **bcp_bind***pData*パラメーター。 インジケーター変数のアドレスが格納されているインジケーター変数を使用する場合、 **bcp_bind***pData*パラメーター。 一括コピー関数では、データ変数の場所を計算を追加して、 **bcp_bind***cbIndicator*と*pData*パラメーター。  
  
 **bcp_bind**可変長のデータを処理するための 3 つのメソッドをサポートしています。  
  
-   使用して*cbData*には、データ変数のみです。 内のデータの長さを配置*cbData*です。 一括データの長さが、変更をコピーするたびに呼び出す[bcp_collen](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md)をリセットする*cbData*です。 その他の 2 つの方法のいずれかが使用されている場合は、SQL_VARLEN_DATA を指定します。 *cbData*です。 列に対して指定されているすべてのデータ値が NULL の場合は、指定の SQL_NULL_DATA *cbData*です。  
  
-   インジケーター変数を使用します。 新しい各データ値をデータ変数に移動するときに、その値の長さをインジケーター変数に格納します。 その他の 2 つの方法のいずれかが使用されている場合 0 を指定*cbIndicator*です。  
  
-   ターミネータ ポインターを使用します。 負荷、 **bcp_bind***pTerm*パラメーター データを終了するビット パターンのアドレスを使用します。 その他の 2 つの方法のいずれかが使用されている場合は、場合は NULL を指定します。 *pTerm*です。  
  
 これらのメソッドの 3 つすべてを同じで使用できる**bcp_bind**を呼び出すと、その場合コピーされるデータ量の最小の仕様を使用します。  
  
 **Bcp_bind***型*パラメーターは Db-library のデータ型識別子、ODBC データ型識別子されません。 Db-library のデータ型識別子が、ODBC で使用する、sqlncli.h で定義されている**bcp_bind**関数。  
  
 一括コピー関数では、すべての ODBC C データ型をサポートしているわけではありません。 たとえば、一括コピー関数が、ODBC SQL_C_TYPE_TIMESTAMP 構造をサポートして、これを使用して[SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md)または[SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) ODBC sql_type_timestamp 型のデータを sql_c_char 型の変数に変換します。 使用する場合**bcp_bind**で、*型*sqlcharacter を変数にバインドするパラメーター、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **datetime**列、一括コピー関数を変換します文字変数を適切な datetime 形式のタイムスタンプ エスケープ句。  
  
 次の表は、ODBC SQL データ型のマッピングで使用する推奨されるデータ型、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型。  
  
|ODBC SQL データ型|ODBC C データ型|bcp_bind*型*パラメーター|SQL Server データ型|  
|-----------------------|----------------------|--------------------------------|--------------------------|  
|SQL_CHAR|SQL_C_CHAR|SQLCHARACTER|**文字**<br /><br /> **char**|  
|SQL_VARCHAR|SQL_C_CHAR|SQLCHARACTER|**varchar**<br /><br /> **可変の文字**<br /><br /> **char のさまざまな**<br /><br /> **sysname**|  
|SQL_LONGVARCHAR|SQL_C_CHAR|SQLCHARACTER|**text**|  
|SQL_WCHAR|SQL_C_WCHAR|SQLNCHAR|**nchar**|  
|SQL_WVARCHAR|SQL_C_WCHAR|SQLNVARCHAR|**nvarchar**|  
|SQL_WLONGVARCHAR|SQL_C_WCHAR|SQLNTEXT|**ntext**|  
|SQL_DECIMAL|SQL_C_CHAR|SQLCHARACTER|**decimal**<br /><br /> **年 12 月**<br /><br /> **money**<br /><br /> **smallmoney**|  
|SQL_NUMERIC|SQL_C_NUMERIC|SQLNUMERICN|**numeric**|  
|SQL_BIT|SQL_C_BIT|SQLBIT|**bit**|  
|SQL_TINYINT (符号付き)|SQL_C_SSHORT|SQLINT2|**smallint**|  
|SQL_TINYINT (符号なし)|SQL_C_UTINYINT|SQLINT1|**tinyint**|  
|SQL_SMALL_INT (符号付き)|SQL_C_SSHORT|SQLINT2|**smallint**|  
|SQL_SMALL_INT (符号なし)|SQL_C_SLONG|SQLINT4|**int**<br /><br /> **整数 (integer)**|  
|SQL_INTEGER (符号付き)|SQL_C_SLONG|SQLINT4|**int**<br /><br /> **整数 (integer)**|  
|SQL_INTEGER (符号なし)|SQL_C_CHAR|SQLCHARACTER|**decimal**<br /><br /> **年 12 月**|  
|SQL_BIGINT (符号付きと符号なし)|SQL_C_CHAR|SQLCHARACTER|**bigint**|  
|SQL_REAL|SQL_C_FLOAT|SQLFLT4|**real**|  
|SQL_FLOAT|SQL_C_DOUBLE|SQLFLT8|**float**|  
|SQL_DOUBLE|SQL_C_DOUBLE|SQLFLT8|**float**|  
|SQL_BINARY|SQL_C_BINARY|SQLBINARY|**[バイナリ]**<br /><br /> **timestamp**|  
|SQL_VARBINARY|SQL_C_BINARY|SQLBINARY|**varbinary**<br /><br /> **バイナリのさまざまな**|  
|SQL_LONGVARBINARY|SQL_C_BINARY|SQLBINARY|**image**|  
|SQL_TYPE_DATE|SQL_C_CHAR|SQLCHARACTER|**datetime**<br /><br /> **smalldatetime**|  
|SQL_TYPE_TIME|SQL_C_CHAR|SQLCHARACTER|**datetime**<br /><br /> **smalldatetime**|  
|SQL_TYPE_TIMESTAMP|SQL_C_CHAR|SQLCHARACTER|**datetime**<br /><br /> **smalldatetime**|  
|SQL_GUID|SQL_C_GUID|SQLUNIQUEID|**uniqueidentifier**|  
|SQL_INTERVAL_|SQL_C_CHAR|SQLCHARACTER|**char**|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]署名されていない**tinyint**、unsigned **smallint**、または符号なし**int**データ型。 値のデータの損失を防ぐためには、これらのデータ型を移行するときに、作成、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [次へ] の最大の整数データ型を持つテーブルです。 ユーザーが元のデータ型で許容されている範囲外の値を後から追加しないようにするには、次のようにルールを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 列に適用し、ソースのデータ型でサポートされる範囲内に許容値を限定します。  
  
```  
CREATE TABLE Sample_Ints(STinyIntCol   SMALLINT,  
USmallIntCol INT)  
GO  
CREATE RULE STinyInt_Rule  
AS   
@range >= -128 AND @range <= 127  
GO  
CREATE RULE USmallInt_Rule  
AS   
@range >= 0 AND @range <= 65535  
GO  
sp_bindrule STinyInt_Rule, 'Sample_Ints.STinyIntCol'  
GO  
sp_bindrule USmallInt_Rule, 'Sample_Ints.USmallIntCol'  
GO  
```  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]interval データ型を直接サポートされていませんしません。 アプリケーション、ただし、間隔のエスケープ シーケンスとして格納の文字列、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]文字列です。 アプリケーションでは、後で使用するためにこれらのエスケープ シーケンスを読み取ることができますが、[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメント内では使用できません。  
  
 一括コピー関数は、すばやくデータを読み込むために使用できます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は、ODBC データ ソースから読み取られています。 使用して[SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md)プログラム変数に結果セットの列をバインドするを使用し、 **bcp_bind**一括コピーを同じプログラム変数をバインドします。 呼び出す[SQLFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md)または**SQLFetch**したプログラム変数と呼び出し元に、ODBC データ ソースからデータの行をフェッチ[bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md)データの一括コピープログラム変数から[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
 アプリケーションで使用できます、 [bcp_colptr](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-colptr.md)関数で指定したデータ変数のアドレスを変更する必要があるとき、 **bcp_bind** *pData*パラメーター。 アプリケーションで使用できます、 [bcp_collen](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md)関数に最初に指定されたデータの長さを変更する必要があるとき、 **bcp_bind***cbData*パラメーター。  
  
 データを読み取ることができません[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を一括コピー; を使用してプログラム変数には"bcp_readrow"関数のようなものがありません。 実行できるのは、アプリケーションからサーバーへのデータの送信だけです。  
  
## <a name="see-also"></a>参照  
 [一括コピー &#40;ODBC&#41; を実行します。](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)  
  
  

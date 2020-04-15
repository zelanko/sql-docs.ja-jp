---
title: データ型のマッピング (ODBC) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- mapping data types [ODBC]
- result sets [ODBC], data types
- ODBC data types, mapping
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- data types [ODBC], mapping
- sql_variant data type
- SQL Server Native Client ODBC driver, data types
ms.assetid: 4ba0924d-9fca-4c48-aced-0a8d817b3dde
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 92426c854758d07a9d62ec57510d202b870dd9f2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304632"
---
# <a name="mapping-data-types-odbc"></a>データ型のマッピング (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  ネイティブ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアント ODBC[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ドライバーは、SQL データ型を ODBC SQL データ型にマップします。 次のセクションでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL データ型とマップ先の ODBC SQL データ型について説明します。 また、ODBC SQL データ型と対応する ODBC C データ型、およびサポートされる変換と既定の変換についても説明します。  
  
> [!NOTE]  
>  タイムスタンプ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]列の値は**日時**値ではなく、行の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]アクティビティのシーケンスを示す**timestamp** **binary(8)** または**varbinary(8)** 値であるため、**タイムスタンプ**データ型は SQL_BINARY または SQL_VARBINARY ODBC データ型にマップされます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでは、奇数バイトの SQL_C_WCHAR (Unicode) 型の値を処理する場合、末尾の奇数バイトが切り捨てられます。  
  
## <a name="dealing-with-sql_variant-data-type-in-odbc"></a>ODBC での sql_variant データ型の処理  
 **sql_variant**データ型列には、**テキスト** **、ntext** **、image**などのラージ オブジェクト (LOB) 以外の任意の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型を含めることができます。 たとえば、列に含まれる小**さな**値をいくつかの行、他の行の**浮動小数点**値、および剰余の**char/nchar**値を含めることができます。  
  
 **sql_variant**データ型は、Visual Basic の**バリアント**型のデータ型に似ています®。  
  
### <a name="retrieving-data-from-the-server"></a>サーバーからのデータの取得  
 ODBC にはバリアント型の概念が含まれていないので[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、ODBC ドライバで**のsql_variant**データ型の使用を制限しています。 で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]binding を指定する場合 **、sql_variant**データ型は、文書化された ODBC データ型のいずれかにバインドする必要があります。 **SQL_CA_SS_VARIANT_TYPE、** ネイティブ クライアント ODBC[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ドライバに固有の新しい属性で **、sql_variant**列のインスタンスのデータ型をユーザーに返します。  
  
 バインディングが指定されていない場合[、SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md)関数を使用して **、sql_variant**列内のインスタンスのデータ型を決定できます。  
  
 **sql_variant**データを取得するには、次の手順を実行します。  
  
1.  取得した行に位置する**SQLFetch**を呼び出します。  
  
2.  型のSQL_C_BINARYを指定し、データ長に 0 を指定して**SQLGetData**を呼び出します。 これにより、ドライバーは **、sql_variant**ヘッダーを読み取る必要があります。 ヘッダーは **、sql_variant**列にそのインスタンスのデータ型を提供します。 **値**のサイズ (バイト単位) を返します。  
  
3.  属性値として**SQL_CA_SS_VARIANT_TYPE**を指定して[、SQLColAttribute](../../relational-databases/native-client-odbc-api/sqlcolattribute.md)を呼び出します。 この関数は **、sql_variant**列のインスタンスの C データ型をクライアントに返します。  
  
 上記の手順を行うコードを次に示します。  
  
```  
while ((retcode = SQLFetch (hstmt))==SQL_SUCCESS)  
{  
    if (retcode != SQL_SUCCESS && retcode != SQL_SUCCESS_WITH_INFO)  
    {  
        SQLError (NULL, NULL, hstmt, NULL,   
                    &lNativeError,szError,MAX_DATA,&sReturned);  
        printf_s ("%s\n",szError);  
        goto Exit;  
    }  
    retcode = SQLGetData (hstmt, 1, SQL_C_BINARY,   
                                pBuff,0,&Indicator);//Figure out the length  
    if (retcode != SQL_SUCCESS_WITH_INFO && retcode != SQL_SUCCESS)  
    {  
        SQLError (NULL, NULL, hstmt, NULL, &lNativeError,   
                    szError,MAX_DATA,&sReturned);  
        printf_s ("%s\n",szError);  
        goto Exit;  
    }  
    printf_s ("Byte length : %d ",Indicator); //Print out the byte length  
  
    int iValue = 0;  
    retcode = SQLColAttribute (hstmt, 1, SQL_CA_SS_VARIANT_TYPE, NULL,   
                                        NULL,NULL,&iValue);  //Figure out the type  
    printf_s ("Sub type = %d ",iValue);//Print the type, the return is C_type of the column]  
  
// Set up a new binding or do the SQLGetData on that column with   
// the appropriate type  
}  
```  
  
 ユーザーが[SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md)を使用してバインドを作成する場合、ドライバーはメタデータとデータを読み取ります。 次に、そのデータをバインドに指定されている適切な ODBC 型に変換します。  
  
### <a name="sending-data-to-the-server"></a>サーバーへのデータの送信  
 **SQL_SS_VARIANT、** ネイティブ クライアント ODBC ドライバ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に固有の新しいデータ型が **、sql_variant**列に送信されるデータに使用されます。 パラメーターを使用してサーバーにデータを送信する場合 (例えば、INSERT INTO テーブル名の値 (?,?) )、SQLBindParameter を使用して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、C 型とそれに対応する型を含むパラメーター情報を指定します。 [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント ODBC ドライバーは、C データ型を適切な**sql_variant**サブタイプのいずれかに変換します。  
  
## <a name="see-also"></a>参照  
 [ODBC&#41;&#40;結果の処理](../../relational-databases/native-client-odbc-results/processing-results-odbc.md)  
  
  

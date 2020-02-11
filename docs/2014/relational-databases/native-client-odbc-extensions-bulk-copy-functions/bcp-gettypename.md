---
title: bcp_gettypename |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_gettypename
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_gettypename function
ms.assetid: 65f036d1-f60e-4b8a-97b3-76fccf0dfed4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5bc7caa063d14967e576fd009a23110b9647836b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62689027"
---
# <a name="bcp_gettypename"></a>bcp_gettypename
  指定された BCP 型トークンの SQL 型名を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
RETCODE bcp_gettypename (  
INT   
token  
,  
DBBOOL   
fIsMaxType  
);  
  
```  
  
## <a name="arguments"></a>引数  
 *token*  
 BCP 型トークンを示す値です。  
  
 *分野*  
 要求されたトークンが max 型かどうかを示します。  
  
## <a name="returns"></a>戻り値  
 BCP 型に対応する SQL 型名を含む文字列を返します。 無効な BCP 型が指定されると、空文字列を返します。  
  
## <a name="remarks"></a>解説  
 BCP 型トークンは、sqlncli.h ヘッダー ファイルと sqlncli11.lib ライブラリで定義されています。  
  
 次の表では、指定できる BCP 型、それらの BCP 型が max 型かどうか、および予想される出力を示しています。  
  
|BCP 型名|MaxType|Output|  
|-------------------|-------------|------------|  
|`SQLDECIMAL`|使用できるのは|**decimal**|  
|`SQLNUMERIC`|使用できるのは|**番号**|  
|`SQLINT1`|使用できるのは|**tinyint**|  
|`SQLINT2`|使用できるのは|**smallint**|  
|`SQLINT4`|使用できるのは|**int**|  
|`SQLMONEY`|使用できるのは|**money**|  
|`SQLFLT8`|使用できるのは|**float**|  
|`SQLDATETIME`|使用できるのは|**DATETIME**|  
|`SQLBITN`|使用できるのは|**bit-null**|  
|`SQLBIT`|使用できるのは|**bit**|  
|`SQLBIGCHAR`|いいえ|**char**|  
|`SQLCHARACTER`|いいえ|**char**|  
|`SQLBIGVARCHAR`|いいえ|**varchar**|  
|`SQLVARCHAR`|いいえ|**varchar**|  
|`SQLTEXT`|使用できるのは|**本文**|  
|`SQLBIGBINARY`|いいえ|**binary**|  
|`SQLBINARY`|いいえ|**バイナリ**|  
|`SQLBIGVARBINARY`|いいえ|**可変長**|  
|`SQLVARBINARY`|いいえ|**可変長**|  
|`SQLIMAGE`|使用できるのは|**Image**|  
|`SQLINTN`|使用できるのは|**int-null**|  
|`SQLDATETIMN`|使用できるのは|**datetime-null**|  
|`SQLMONEYN`|使用できるのは|**money-null**|  
|`SQLFLTN`|使用できるのは|**float-null**|  
|`SQLAOPSUM`|使用できるのは|**求め**|  
|`SQLAOPAVG`|使用できるのは|**Avg**|  
|`SQLAOPCNT`|使用できるのは|**数**|  
|`SQLAOPMIN`|使用できるのは|**」**|  
|`SQLAOPMAX`|使用できるのは|**制限**|  
|`SQLDATETIM4`|使用できるのは|**smalldatetime**|  
|`SQLMONEY4`|使用できるのは|**Smallmoney**|  
|`SQLFLT4`|使用できるのは|**Real**|  
|`SQLUNIQUEID`|使用できるのは|**UNIQUEIDENTIFIER**|  
|`SQLNCHAR`|いいえ|**Nchar**|  
|`SQLNVARCHAR`|いいえ|**Nvarchar**|  
|`SQLNTEXT`|使用できるのは|**Ntext**|  
|`SQLVARIANT`|使用できるのは|**sql_variant**|  
|`SQLINT8`|使用できるのは|**Bigint**|  
|`SQLCHARACTER`|はい|**varchar(max)**|  
|`SQLBIGCHAR`|はい|**varchar(max)**|  
|`SQLBIGVARCHAR`|はい|**varchar(max)**|  
|`SQLVARCHAR`|はい|**varchar(max)**|  
|`SQLBINARY`|はい|**varbinary(max)**|  
|`SQLBIGBINARY`|はい|**varbinary(max)**|  
|`SQLBIGVARBINARY`|はい|**varbinary(max)**|  
|`SQLVARBINARY`|はい|**varbinary(max)**|  
|`SQLNCHAR`|はい|**nvarchar(max)**|  
|`SQLNVARCHAR`|はい|**nvarchar(max)**|  
|`SQLXML`|はい|**Xml**|  
|`SQLUDT`|使用できるのは|**Udt**|  
  
## <a name="bcp_gettypename-support-for-enhanced-date-and-time-features"></a>bcp_gettypename による機能強化された日付と時刻のサポート  
 日付/時刻型のトークンパラメーター値については、「 [&#40;OLE DB および ODBC&#41;の拡張された日付と時刻の型に対する一括コピーの変更](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)」を参照してください。 返される値は、対応する行の "ファイル ストレージ型" 列に示されています。  
  
 詳細については、「[日付と時刻の機能強化 &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [一括コピー関数](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  

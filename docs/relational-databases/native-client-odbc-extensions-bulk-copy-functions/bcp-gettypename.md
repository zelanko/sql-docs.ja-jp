---
title: bcp_gettypename による |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- bcp_gettypename
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_gettypename function
ms.assetid: 65f036d1-f60e-4b8a-97b3-76fccf0dfed4
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e00a0bc4178cc8ac607366e9d80377954c14d3ae
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43106163"
---
# <a name="bcpgettypename"></a>bcp_gettypename
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  指定された BCP 型トークンの SQL 型名を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
RETCODE bcp_gettypename (  
        INT token,  
        DBBOOL fIsMaxType);  
```  
  
## <a name="arguments"></a>引数  
 *token*  
 BCP 型トークンを示す値です。  
  
 *field*  
 要求されたトークンが max 型かどうかを示します。  
  
## <a name="returns"></a>戻り値  
 BCP 型に対応する SQL 型名を含む文字列を返します。 無効な BCP 型が指定されると、空文字列を返します。  
  
## <a name="remarks"></a>コメント  
 BCP 型トークンは、sqlncli.h ヘッダー ファイルと sqlncli11.lib ライブラリで定義されています。  
  
 次の表では、指定できる BCP 型、それらの BCP 型が max 型かどうか、および予想される出力を示しています。  
  
|BCP 型名|MaxType|[出力]|  
|-------------------|-------------|------------|  
|**SQLDECIMAL**|接続前/接続後|**decimal**|  
|**SQLNUMERIC**|接続前/接続後|**numeric**|  
|**SQLINT1**|接続前/接続後|**tinyint**|  
|**SQLINT2**|接続前/接続後|**smallint**|  
|**SQLINT4**|接続前/接続後|**int**|  
|**SQLMONEY**|接続前/接続後|**money**|  
|**SQLFLT8**|接続前/接続後|**float**|  
|**SQLDATETIME**|接続前/接続後|**datetime**|  
|**SQLBITN**|接続前/接続後|**bit-null**|  
|**SQLBIT**|接続前/接続後|**bit**|  
|**SQLBIGCHAR**|いいえ|**char**|  
|**SQLCHARACTER**|いいえ|**char**|  
|**SQLBIGVARCHAR**|いいえ|**varchar**|  
|**SQLVARCHAR**|いいえ|**varchar**|  
|**SQLTEXT**|接続前/接続後|**text**|  
|**SQLBIGBINARY**|いいえ|**[バイナリ]**|  
|**SQLBINARY**|いいえ|**Binary**|  
|**SQLBIGVARBINARY**|いいえ|**varbinary**|  
|**SQLVARBINARY**|いいえ|**varbinary**|  
|**SQLIMAGE**|接続前/接続後|**[イメージ]**|  
|**SQLINTN**|接続前/接続後|**int-null**|  
|**SQLDATETIMN**|接続前/接続後|**datetime-null**|  
|**SQLMONEYN**|接続前/接続後|**money-null**|  
|**SQLFLTN**|接続前/接続後|**float-null**|  
|**SQLAOPSUM**|接続前/接続後|**Sum**|  
|**SQLAOPAVG**|接続前/接続後|**Avg**|  
|**SQLAOPCNT**|接続前/接続後|**Count**|  
|**SQLAOPMIN**|接続前/接続後|**Min**|  
|**SQLAOPMAX**|接続前/接続後|**Max**|  
|**SQLDATETIM4**|接続前/接続後|**smalldatetime**|  
|**SQLMONEY4**|接続前/接続後|**smallmoney**|  
|**SQLFLT4**|接続前/接続後|**本当の**|  
|**SQLUNIQUEID**|接続前/接続後|**uniqueidentifier**|  
|**SQLNCHAR**|いいえ|**nchar**|  
|**SQLNVARCHAR**|いいえ|**Nvarchar**|  
|**SQLNTEXT**|接続前/接続後|**ntext**|  
|**SQLVARIANT**|接続前/接続後|**sql_variant**|  
|**SQLINT8**|接続前/接続後|**Bigint**|  
|**SQLCHARACTER**|はい|**varchar(max)**|  
|**SQLBIGCHAR**|はい|**varchar(max)**|  
|**SQLBIGVARCHAR**|はい|**varchar(max)**|  
|**SQLVARCHAR**|はい|**varchar(max)**|  
|**SQLBINARY**|はい|**varbinary(max)**|  
|**SQLBIGBINARY**|はい|**varbinary(max)**|  
|**SQLBIGVARBINARY**|はい|**varbinary(max)**|  
|**SQLVARBINARY**|はい|**varbinary(max)**|  
|**SQLNCHAR**|はい|**nvarchar(max)**|  
|**SQLNVARCHAR**|はい|**nvarchar(max)**|  
|**SQLXML**|はい|**Xml**|  
|**SQLUDT**|接続前/接続後|**Udt**|  
  
## <a name="bcpgettypename-support-for-enhanced-date-and-time-features"></a>bcp_gettypename による機能強化された日付と時刻のサポート  
 内のテーブルの「sqlncli.h の型」列の日付/時刻型のトークンのパラメーターの値が説明されている[強化された日付と時刻型向けの一括コピーの変更&#40;OLE DB および ODBC&#41;](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)します。 返される値は、対応する行の "ファイル ストレージ型" 列に示されています。  
  
 詳細については、次を参照してください。[日付と時刻の強化&#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)します。  
  
## <a name="see-also"></a>参照  
 [一括コピー関数](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  

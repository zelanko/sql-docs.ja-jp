---
title: "bcp_gettypename による |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-extensions-bulk-copy-functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname: bcp_gettypename
apilocation: sqlncli11.dll
apitype: DLLExport
helpviewer_keywords: bcp_gettypename function
ms.assetid: 65f036d1-f60e-4b8a-97b3-76fccf0dfed4
caps.latest.revision: "31"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8f452b3c5e12b76ba2d1327b59f1cfa17f16bb46
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
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
 *トークン*  
 BCP 型トークンを示す値です。  
  
 *フィールド*  
 要求されたトークンが max 型かどうかを示します。  
  
## <a name="returns"></a>返します。  
 BCP 型に対応する SQL 型名を含む文字列を返します。 無効な BCP 型が指定されると、空文字列を返します。  
  
## <a name="remarks"></a>解説  
 BCP 型トークンは、sqlncli.h ヘッダー ファイルと sqlncli11.lib ライブラリで定義されています。  
  
 次の表では、指定できる BCP 型、それらの BCP 型が max 型かどうか、および予想される出力を示しています。  
  
|BCP 型名|MaxType|出力|  
|-------------------|-------------|------------|  
|**SQLDECIMAL**|接続前/接続後|**decimal**|  
|**SQLNUMERIC**|接続前/接続後|**numeric**|  
|**SQLINT1**|接続前/接続後|**tinyint**|  
|**SQLINT2**|接続前/接続後|**smallint**|  
|**SQLINT4**|接続前/接続後|**int**|  
|**SQLMONEY**|接続前/接続後|**money**|  
|**SQLFLT8**|接続前/接続後|**float**|  
|**SQLDATETIME**|接続前/接続後|**datetime**|  
|**SQLBITN**|接続前/接続後|**ビット null**|  
|**SQLBIT**|接続前/接続後|**bit**|  
|**SQLBIGCHAR**|不可|**char**|  
|**SQLCHARACTER**|不可|**char**|  
|**SQLBIGVARCHAR**|不可|**varchar**|  
|**SQLVARCHAR**|不可|**varchar**|  
|**SQLTEXT**|接続前/接続後|**text**|  
|**SQLBIGBINARY**|不可|**[バイナリ]**|  
|**SQLBINARY**|不可|**Binary**|  
|**SQLBIGVARBINARY**|不可|**Varbinary**|  
|**SQLVARBINARY**|不可|**Varbinary**|  
|**SQLIMAGE**|接続前/接続後|**[イメージ]**|  
|**SQLINTN**|接続前/接続後|**int null**|  
|**SQLDATETIMN**|接続前/接続後|**datetime null**|  
|**SQLMONEYN**|接続前/接続後|**money null**|  
|**SQLFLTN**|接続前/接続後|**float null**|  
|**SQLAOPSUM**|接続前/接続後|**Sum**|  
|**SQLAOPAVG**|接続前/接続後|**Avg**|  
|**SQLAOPCNT**|接続前/接続後|**Count**|  
|**SQLAOPMIN**|接続前/接続後|**Min**|  
|**SQLAOPMAX**|接続前/接続後|**Max**|  
|**SQLDATETIM4**|接続前/接続後|**smalldatetime**|  
|**SQLMONEY4**|接続前/接続後|**Smallmoney**|  
|**SQLFLT4**|接続前/接続後|**本当の**|  
|**SQLUNIQUEID**|接続前/接続後|**uniqueidentifier**|  
|**SQLNCHAR**|不可|**Nchar**|  
|**SQLNVARCHAR**|不可|**Nvarchar**|  
|**SQLNTEXT**|接続前/接続後|**Ntext**|  
|**SQLVARIANT**|接続前/接続後|**sql_variant**|  
|**SQLINT8**|接続前/接続後|**Bigint**|  
|**SQLCHARACTER**|可|**varchar(max)**|  
|**SQLBIGCHAR**|可|**varchar(max)**|  
|**SQLBIGVARCHAR**|可|**varchar(max)**|  
|**SQLVARCHAR**|可|**varchar(max)**|  
|**SQLBINARY**|可|**varbinary(max)**|  
|**SQLBIGBINARY**|可|**varbinary(max)**|  
|**SQLBIGVARBINARY**|可|**varbinary(max)**|  
|**SQLVARBINARY**|可|**varbinary(max)**|  
|**SQLNCHAR**|可|**nvarchar(max)**|  
|**SQLNVARCHAR**|可|**nvarchar(max)**|  
|**SQLXML**|可|**Xml**|  
|**SQLUDT**|接続前/接続後|**Udt**|  
  
## <a name="bcpgettypename-support-for-enhanced-date-and-time-features"></a>bcp_gettypename による機能強化された日付と時刻のサポート  
 内のテーブルの「sqlncli.h 内の型」列に日付/時刻型のトークンのパラメーター値が説明されている[強化された日付と時刻型 &#40; OLE DB と ODBC &#41; の変更の一括コピー](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)です。 返される値は、対応する行の "ファイル ストレージ型" 列に示されています。  
  
 詳細については、次を参照してください。[日付と時刻の強化 &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)です。  
  
## <a name="see-also"></a>参照  
 [一括コピー関数](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  

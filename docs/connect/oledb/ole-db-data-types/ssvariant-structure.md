---
title: SSVARIANT 構造体 | Microsoft Docs
description: OLE DB Driver for SQL Server の SSVARIANT 構造
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
f1_keywords:
- SSVARIANT
helpviewer_keywords:
- SSVARIANT struct
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 09ff4af7026ce75a8668db22910e550dc0c72857
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "67995170"
---
# <a name="ssvariant-structure"></a>SSVARIANT 構造体
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  msoledbsql.h で定義されている **SSVARIANT** 構造体は、OLE DB Driver for SQL Server の DBTYPE_SQLVARIANT 値に対応します。  
  
 **SSVARIANT** は、識別共用体です。 vt メンバーの値に応じて、コンシューマーは読み取るメンバーを決めることができます。 vt 値は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型に対応します。 したがって、**SSVARIANT** 構造体には、任意の SQL Server 型を格納できます。 標準の OLE DB 型のデータ構造体の詳細については、「[型インジケーター](https://go.microsoft.com/fwlink/?LinkId=122171)」を参照してください。  
  
## <a name="remarks"></a>解説  
 DataTypeCompat==80 の場合、いくつかの **SSVARIANT** サブタイプが文字列になります。 たとえば、次の vt 値は **SSVARIANT** では VT_SS_WVARSTRING として表されます。  
  
-   VT_SS_DATETIMEOFFSET  
  
-   VT_SS_DATETIME2  
  
-   VT_SS_TIME2  
  
-   VT_SS_DATE  
  
 DateTypeCompat == 0 の場合、これらの型はネイティブ形式で表されます。  
  
 SSPROP_INIT_DATATYPECOMPATIBILITY の詳細については、「[OLE DB Driver for SQL Server での接続文字列キーワードの使用](../../oledb/applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md)」を参照してください。  
  
 msoledbsql.h ファイルには、**SSVARIANT** 構造体のメンバー型の逆参照を単純化するバリアント アクセス マクロが格納されています。 たとえば、V_SS_DATETIMEOFFSET を次のように使用できます。  
  
```  
memcpy(&V_SS_DATETIMEOFFSET(pssVar).tsoDateTimeOffsetVal, pDTO, cbNative);  
V_SS_DATETIMEOFFSET(pssVar).bScale = bScale;  
```  
  
 **SSVARIANT** 構造体の各メンバーのアクセス マクロの完全なセットについては、msoledbsql.h ファイルを参照してください。  
  
 次の表で、**SSVARIANT** 構造体のメンバーについて説明します。  
  
|メンバー|OLE DB 型インジケーター|OLE DB C データ型|vt の値|説明|  
|------------|---------------------------|------------------------|--------------|--------------|  
|vt|SSVARTYPE|||**SSVARIANT** 構造体に格納される値の型を指定します。|  
|bTinyIntVal|DBTYPE_UI1|**BYTE**|**VT_SS_UI1**|**tinyint**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型がサポートされています。|  
|sShortIntVal|DBTYPE_I2|**SHORT**|**VT_SS_I2**|**smallint**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型がサポートされています。|  
|lIntVal|DBTYPE_I4|**LONG**|**VT_SS_I4**|**int**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型がサポートされています。|  
|llBigIntVal|DBTYPE_I8|**LARGE_INTEGER**|**VT_SS_I8**|**bigint**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型がサポートされています。|  
|fltRealVal|DBTYPE_R4|**float**|**VT_SS_R4**|**real**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型がサポートされています。|  
|dblFloatVal|DBTYPE_R8|**double**|**VT_SS_R8**|**float**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型がサポートされています。|  
|cyMoneyVal|DBTYPE_CY|**LARGE_INTEGER**|**VT_SS_MONEY VT_SS_SMALLMONEY**|**money** と **smallmoney**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のデータ型がサポートされています。|  
|fBitVal|DBTYPE_BOOL|**VARIANT_BOOL**|**VT_SS_BIT**|**bit**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型がサポートされています。|  
|rgbGuidVal|DBTYPE_GUID|**GUID**|**VT_SS_GUID**|**uniqueidentifier**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型がサポートされています。|  
|numNumericVal|DBTYPE_NUMERIC|**DB_NUMERIC**|**VT_SS_NUMERIC**|**numeric**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型がサポートされています。|  
|dDateVal|DBTYPE_DATE|**DBDATE**|**VT_SS_DATE**|**date**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型をサポートします。|  
|tsDateTimeVal|DBTYPE_DBTIMESTAMP|**DBTIMESTAMP**|**VT_SS_SMALLDATETIME VT_SS_DATETIME VT_SS_DATETIME2**|**smalldatetime**、**datetime**、**datetime2**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のデータ型がサポートされています。|  
|Time2Val|DBTYPE_DBTIME2|**DBTIME2**|**VT_SS_TIME2**|**time**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型がサポートされています。<br /><br /> 次のメンバーを含みます。<br /><br /> *tTime2Val* (**DBTIME2**)<br /><br /> *bScale* (**BYTE**) *tTime2Val* 値の小数点以下桁数を指定します。|  
|DateTimeVal|DBTYPE_DBTIMESTAMP|**DBTIMESTAMP**|**VT_SS_DATETIME2**|**datetime2**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型がサポートされています。<br /><br /> 次のメンバーを含みます。<br /><br /> *tsDataTimeVal* (DBTIMESTAMP)<br /><br /> *bScale* (**BYTE**) *tsDataTimeVal* 値の小数点以下桁数を指定します。|  
|DateTimeOffsetVal|DBTYPE_DBTIMESTAMPOFSET|**DBTIMESTAMPOFFSET**|**VT_SS_DATETIMEOFFSET**|**datetimeoffset**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型がサポートされています。<br /><br /> 次のメンバーを含みます。<br /><br /> *tsoDateTimeOffsetVal* (**DBTIMESTAMPOFFSET**)<br /><br /> *bScale* (**BYTE**) *tsoDateTimeOffsetVal* 値の小数点以下桁数を指定します。|  
|NCharVal|対応する OLE DB 型インジケーターはありません。|**struct _NCharVal**|**VT_SS_WVARSTRING、**<br /><br /> **VT_SS_WSTRING**|**nchar** と **nvarchar**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のデータ型がサポートされています。<br /><br /> 次のメンバーを含みます。<br /><br /> *sActualLength* (**SHORT**) *pwchNCharVal* がポイントする文字列の実際の長さを指定します。 末尾の 0 は含まれません。<br /><br /> *sMaxLength* (**SHORT**) *pwchNCharVal* がポイントする文字列の最大長を指定します。<br /><br /> *pwchNCharVal* (**WCHAR** \*) 文字列へのポインター。<br /><br /> 使用されていないメンバー: *rgbReserved*、*dwReserved*、および *pwchReserved*。|  
|CharVal|対応する OLE DB 型インジケーターはありません。|**struct _CharVal**|**VT_SS_STRING、**<br /><br /> **VT_SS_VARSTRING**|**char** と **varchar**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のデータ型がサポートされています。<br /><br /> 次のメンバーを含みます。<br /><br /> *sActualLength* (**SHORT**) *pchCharVal* がポイントする文字列の実際の長さを指定します。 末尾の 0 は含まれません。<br /><br /> *sMaxLength* (**SHORT**) *pchCharVal* がポイントする文字列の最大長を指定します。<br /><br /> *pchCharVal* (**CHAR** \*) 文字列へのポインター。<br /><br /> 使用されないメンバー :<br /><br /> *rgbReserved*、*dwReserved*、および *pwchReserved*。|  
|BinaryVal|対応する OLE DB 型インジケーターはありません。|**struct _BinaryVal**|**VT_SS_VARBINARY、**<br /><br /> **VT_SS_BINARY**|**binary** と **varbinary**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のデータ型がサポートされています。<br /><br /> 次のメンバーを含みます。<br /><br /> *sActualLength* (**SHORT**) *prgbBinaryVal* がポイントするデータの実際の長さを指定します。<br /><br /> *sMaxLength* (**SHORT**) *prgbBinaryVal* がポイントするデータの最大長を指定します。<br /><br /> *prgbBinaryVal* (**BYTE** \*) バイナリ データへのポインター。<br /><br /> 使用されていないメンバー: *dwReserved*。|  
|UnknownType|未使用|未使用|未使用|未使用|  
|BLOBType|未使用|未使用|未使用|未使用|  
  
## <a name="see-also"></a>参照  
 [データ型 &#40;OLE DB&#41;](../../oledb/ole-db-data-types/data-types-ole-db.md)  
  
  

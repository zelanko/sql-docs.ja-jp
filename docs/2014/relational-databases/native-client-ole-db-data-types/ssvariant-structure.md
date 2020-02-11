---
title: SSVARIANT 構造体 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
f1_keywords:
- SSVARIANT
helpviewer_keywords:
- SSVARIANT struct
ms.assetid: d13c6aa6-bd49-467a-9093-495df8f1e2d9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ff6e37986378a66d94dc113c4e3fe072fe3c077f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63062500"
---
# <a name="ssvariant-structure"></a>SSVARIANT 構造体
  sqlncli.h で定義されている `SSVARIANT` 構造体は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLEDB プロバイダーの DBTYPE_SQLVARIANT 値に対応します。  
  
 
  `SSVARIANT` は、識別共用体です。 vt メンバーの値に応じて、コンシューマーは読み取るメンバーを決めることができます。 vt 値は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型に対応します。 したがって、`SSVARIANT` 構造体には、任意の SQL Server 型を格納できます。 標準 OLE DB 型のデータ構造の詳細については、「[型インジケーター](https://go.microsoft.com/fwlink/?LinkId=122171)」を参照してください。  
  
## <a name="remarks"></a>解説  
 DataTypeCompat==80 の場合、いくつかの `SSVARIANT` サブタイプが文字列になります。 たとえば、次の vt 値は `SSVARIANT` では VT_SS_WVARSTRING として表されます。  
  
-   VT_SS_DATETIMEOFFSET  
  
-   VT_SS_DATETIME2  
  
-   VT_SS_TIME2  
  
-   VT_SS_DATE  
  
 DateTypeCompat == 0 の場合、これらの型はネイティブ形式で表されます。  
  
 SSPROP_INIT_DATATYPECOMPATIBILITY の詳細については、「 [SQL Server Native Client での接続文字列キーワードの使用](../native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)」を参照してください。  
  
 sqlncli.h ファイルには、`SSVARIANT` 構造体のメンバー型の逆参照を単純化するバリアント アクセス マクロが格納されています。 たとえば、V_SS_DATETIMEOFFSET を次のように使用できます。  
  
```  
memcpy(&V_SS_DATETIMEOFFSET(pssVar).tsoDateTimeOffsetVal, pDTO, cbNative);  
V_SS_DATETIMEOFFSET(pssVar).bScale = bScale;  
```  
  
 
  `SSVARIANT` 構造体の各メンバーのアクセス マクロの完全なセットについては、sqlncli.hi ファイルを参照してください。  
  
 次の表で、`SSVARIANT` 構造体のメンバーについて説明します。  
  
|メンバー|OLE DB 型インジケーター|OLE DB C データ型|vt の値|説明|  
|------------|---------------------------|------------------------|--------------|--------------|  
|vt|SSVARTYPE|||
  `SSVARIANT` 構造体に格納される値の型を指定します。|  
|bTinyIntVal|DBTYPE_UI1|`BYTE`|`VT_SS_UI1`|データ型`tinyint` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をサポートします。|  
|sShortIntVal|DBTYPE_I2|`SHORT`|`VT_SS_I2`|データ型`smallint` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をサポートします。|  
|lIntVal|DBTYPE_I4|`LONG`|`VT_SS_I4`|データ型`int` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をサポートします。|  
|llBigIntVal|DBTYPE_I8|`LARGE_INTEGER`|`VT_SS_I8`|データ型`bigint` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をサポートします。|  
|fltRealVal|DBTYPE_R4|`float`|`VT_SS_R4`|データ型`real` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をサポートします。|  
|dblFloatVal|DBTYPE_R8|`double`|`VT_SS_R8`|データ型`float` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をサポートします。|  
|cyMoneyVal|DBTYPE_CY|`LARGE_INTEGER`|**VT_SS_MONEY VT_SS_SMALLMONEY**|では`money` 、および**smallmoney** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型をサポートしています。|  
|fBitVal|DBTYPE_BOOL|`VARIANT_BOOL`|`VT_SS_BIT`|データ型`bit` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をサポートします。|  
|rgbGuidVal|DBTYPE_GUID|`GUID`|`VT_SS_GUID`|データ型`uniqueidentifier` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をサポートします。|  
|numNumericVal|DBTYPE_NUMERIC|`DB_NUMERIC`|`VT_SS_NUMERIC`|データ型`numeric` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をサポートします。|  
|dDateVal|DBTYPE_DATE|`DBDATE`|`VT_SS_DATE`|データ型`date` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をサポートします。|  
|tsDateTimeVal|DBTYPE_DBTIMESTAMP|`DBTIMESTAMP`|`VT_SS_SMALLDATETIME VT_SS_DATETIME VT_SS_DATETIME2`|では`smalldatetime`、 `datetime`、、 `datetime2` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]およびの各データ型がサポートされます。|  
|Time2Val|DBTYPE_DBTIME2|`DBTIME2`|`VT_SS_TIME2`|データ型`time` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をサポートします。<br /><br /> 次のメンバーを含みます。<br /><br /> *tTime2Val* (`DBTIME2`)<br /><br /> *bscale* (`BYTE`) は、 *tTime2Val*値の小数点以下桁数を指定します。|  
|DateTimeVal|DBTYPE_DBTIMESTAMP|`DBTIMESTAMP`|`VT_SS_DATETIME2`|データ型`datetime2` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をサポートします。<br /><br /> 次のメンバーを含みます。<br /><br /> *tsDataTimeVal* (dbtimestamp)<br /><br /> *bscale* (`BYTE`) は、 *tsDataTimeVal*値の小数点以下桁数を指定します。|  
|DateTimeOffsetVal|DBTYPE_DBTIMESTAMPOFSET|`DBTIMESTAMPOFFSET`|`VT_SS_DATETIMEOFFSET`|データ型`datetimeoffset` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をサポートします。<br /><br /> 次のメンバーを含みます。<br /><br /> *tsoDateTimeOffsetVal* (`DBTIMESTAMPOFFSET`)<br /><br /> *bscale* (`BYTE`) は、 *tsoDateTimeOffsetVal*値の小数点以下桁数を指定します。|  
|NCharVal|対応する OLE DB 型インジケーターはありません。|`struct _NCharVal`|`VT_SS_WVARSTRING,`<br /><br /> `VT_SS_WSTRING`|では`nchar` 、および**nvarchar** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型がサポートされています。<br /><br /> 次のメンバーを含みます。<br /><br /> *sActualLength* (`SHORT`) *pwchNCharVal*が指す文字列の実際の長さを指定します。 末尾の 0 は含まれません。<br /><br /> *smaxlength* (`SHORT`) *pwchNCharVal*が指す文字列の最大長を指定します。<br /><br /> *pwchNCharVal* (`WCHAR` \*) 文字列へのポインター。<br /><br /> 使用されていないメンバー: *rgbReserved*、 *dwreserved*、および*pwchReserved*。|  
|CharVal|対応する OLE DB 型インジケーターはありません。|`struct _CharVal`|`VT_SS_STRING,`<br /><br /> `VT_SS_VARSTRING`|では`char` 、および**varchar** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型がサポートされます。<br /><br /> 次のメンバーを含みます。<br /><br /> *sActualLength* (`SHORT`) は、 *pchcharval*が指す文字列の実際の長さを指定します。 末尾の 0 は含まれません。<br /><br /> *smaxlength* (`SHORT`) は、 *pchcharval*が指す文字列の最大長を指定します。<br /><br /> *pchcharval* (`CHAR` \*) 文字列へのポインター。<br /><br /> 使用されないメンバー : <br /><br /> *rgbReserved*、 *dwreserved*、および*pwchReserved*。|  
|BinaryVal|対応する OLE DB 型インジケーターはありません。|`struct _BinaryVal`|`VT_SS_VARBINARY,`<br /><br /> `VT_SS_BINARY`|では`binary` 、および**varbinary** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型がサポートされます。<br /><br /> 次のメンバーを含みます。<br /><br /> *sActualLength* (`SHORT`) は、 *prgbbinaryval*が指すデータの実際の長さを指定します。<br /><br /> *smaxlength* (`SHORT`) は、 *prgbbinaryval*が指すデータの最大長を指定します。<br /><br /> *prgbbinaryval* (`BYTE` \*) バイナリデータへのポインター。<br /><br /> 未使用のメンバー: *Dwreserved*。|  
|UnknownType|未使用|未使用|未使用|未使用|  
|BLOBType|未使用|未使用|未使用|未使用|  
  
## <a name="see-also"></a>参照  
 [データ型 &#40;OLE DB&#41;](data-types-ole-db.md)  
  
  

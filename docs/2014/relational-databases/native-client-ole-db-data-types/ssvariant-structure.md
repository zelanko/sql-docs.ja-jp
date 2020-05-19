---
title: SSVARIANT 構造体 | Microsoft Docs
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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 3877e7b8c6ccd0d5364b3aea291facb1799bff7d
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/01/2020
ms.locfileid: "82705105"
---
# <a name="ssvariant-structure"></a>SSVARIANT 構造体
  sqlncli.h で定義されている `SSVARIANT` 構造体は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLEDB プロバイダーの DBTYPE_SQLVARIANT 値に対応します。  
  
 `SSVARIANT` は、識別共用体です。 vt メンバーの値に応じて、コンシューマーは読み取るメンバーを決めることができます。 vt 値は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型に対応します。 したがって、`SSVARIANT` 構造体には、任意の SQL Server 型を格納できます。 標準の OLE DB 型のデータ構造体の詳細については、「[型インジケーター](https://go.microsoft.com/fwlink/?LinkId=122171)」を参照してください。  
  
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
  
|メンバー|OLE DB 型インジケーター|OLE DB C データ型|vt の値|コメント|  
|------------|---------------------------|------------------------|--------------|--------------|  
|vt|SSVARTYPE|||`SSVARIANT` 構造体に格納される値の型を指定します。|  
|bTinyIntVal|DBTYPE_UI1|`BYTE`|`VT_SS_UI1`|`tinyint` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型をサポートします。|  
|sShortIntVal|DBTYPE_I2|`SHORT`|`VT_SS_I2`|`smallint` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型をサポートします。|  
|lIntVal|DBTYPE_I4|`LONG`|`VT_SS_I4`|`int` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型をサポートします。|  
|llBigIntVal|DBTYPE_I8|`LARGE_INTEGER`|`VT_SS_I8`|`bigint` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型をサポートします。|  
|fltRealVal|DBTYPE_R4|`float`|`VT_SS_R4`|`real` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型をサポートします。|  
|dblFloatVal|DBTYPE_R8|`double`|`VT_SS_R8`|`float` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型をサポートします。|  
|cyMoneyVal|DBTYPE_CY|`LARGE_INTEGER`|**VT_SS_MONEY VT_SS_SMALLMONEY**|では、 `money` および**smallmoney**データ型をサポートして [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] います。|  
|fBitVal|DBTYPE_BOOL|`VARIANT_BOOL`|`VT_SS_BIT`|`bit` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型をサポートします。|  
|rgbGuidVal|DBTYPE_GUID|`GUID`|`VT_SS_GUID`|`uniqueidentifier` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型をサポートします。|  
|numNumericVal|DBTYPE_NUMERIC|`DB_NUMERIC`|`VT_SS_NUMERIC`|`numeric` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型をサポートします。|  
|dDateVal|DBTYPE_DATE|`DBDATE`|`VT_SS_DATE`|`date` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型をサポートします。|  
|tsDateTimeVal|DBTYPE_DBTIMESTAMP|`DBTIMESTAMP`|`VT_SS_SMALLDATETIME VT_SS_DATETIME VT_SS_DATETIME2`|では `smalldatetime` 、、、およびの各データ型がサポートさ `datetime` `datetime2` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] れます。|  
|Time2Val|DBTYPE_DBTIME2|`DBTIME2`|`VT_SS_TIME2`|`time` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型をサポートします。<br /><br /> 次のメンバーを含みます。<br /><br /> *tTime2Val* ( `DBTIME2` )<br /><br /> *Bscale* ( `BYTE` ) は、 *tTime2Val*値の小数点以下桁数を指定します。|  
|DateTimeVal|DBTYPE_DBTIMESTAMP|`DBTIMESTAMP`|`VT_SS_DATETIME2`|`datetime2` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型をサポートします。<br /><br /> 次のメンバーを含みます。<br /><br /> *tsDataTimeVal* (DBTIMESTAMP)<br /><br /> *Bscale* ( `BYTE` ) は、 *tsDataTimeVal*値の小数点以下桁数を指定します。|  
|DateTimeOffsetVal|DBTYPE_DBTIMESTAMPOFSET|`DBTIMESTAMPOFFSET`|`VT_SS_DATETIMEOFFSET`|`datetimeoffset` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型をサポートします。<br /><br /> 次のメンバーを含みます。<br /><br /> *tsoDateTimeOffsetVal* ( `DBTIMESTAMPOFFSET` )<br /><br /> *Bscale* ( `BYTE` ) は、 *tsoDateTimeOffsetVal*値の小数点以下桁数を指定します。|  
|NCharVal|対応する OLE DB 型インジケーターはありません。|`struct _NCharVal`|`VT_SS_WVARSTRING,`<br /><br /> `VT_SS_WSTRING`|では、 `nchar` および**nvarchar**データ型がサポートされてい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。<br /><br /> 次のメンバーを含みます。<br /><br /> *sActualLength* ( `SHORT` ) *pwchNCharVal*が指す文字列の実際の長さを指定します。 末尾の 0 は含まれません。<br /><br /> *Smaxlength* ( `SHORT` ) *pwchNCharVal*が指す文字列の最大長を指定します。<br /><br /> *pwchNCharVal* ( `WCHAR` \* ) 文字列へのポインター。<br /><br /> 使用されていないメンバー: *rgbReserved*、*dwReserved*、および *pwchReserved*。|  
|CharVal|対応する OLE DB 型インジケーターはありません。|`struct _CharVal`|`VT_SS_STRING,`<br /><br /> `VT_SS_VARSTRING`|では、 `char` および**varchar**データ型がサポートさ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] れます。<br /><br /> 次のメンバーを含みます。<br /><br /> *sActualLength* ( `SHORT` ) は、 *pchcharval*が指す文字列の実際の長さを指定します。 末尾の 0 は含まれません。<br /><br /> *Smaxlength* ( `SHORT` ) は、 *pchcharval*が指す文字列の最大長を指定します。<br /><br /> *pchcharval* ( `CHAR` \* ) 文字列へのポインター。<br /><br /> 使用されないメンバー : <br /><br /> *rgbReserved*、*dwReserved*、および *pwchReserved*。|  
|BinaryVal|対応する OLE DB 型インジケーターはありません。|`struct _BinaryVal`|`VT_SS_VARBINARY,`<br /><br /> `VT_SS_BINARY`|では、 `binary` および**varbinary**データ型がサポートさ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] れます。<br /><br /> 次のメンバーを含みます。<br /><br /> *sActualLength* ( `SHORT` ) は、 *prgbbinaryval*が指すデータの実際の長さを指定します。<br /><br /> *Smaxlength* ( `SHORT` ) は、 *prgbbinaryval*が指すデータの最大長を指定します。<br /><br /> *prgbbinaryval* ( `BYTE` \* ) バイナリデータへのポインター。<br /><br /> 使用されていないメンバー: *dwReserved*。|  
|UnknownType|未使用|未使用|未使用|未使用|  
|BLOBType|未使用|未使用|未使用|未使用|  
  
## <a name="see-also"></a>参照  
 [データ型 &#40;OLE DB&#41;](data-types-ole-db.md)  
  
  

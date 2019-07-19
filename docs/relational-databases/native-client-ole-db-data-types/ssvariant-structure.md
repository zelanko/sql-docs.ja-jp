---
title: SSVARIANT 構造体 |Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3dffb546620f7a67f3dc8502d7a8e8b389d9ae7b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68128489"
---
# <a name="ssvariant-structure"></a>SSVARIANT 構造体
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  **SSVARIANT** DBTYPE_SQLVARIANT 値に対応する構造体は、sqlncli.h で定義されている、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLEDB プロバイダー。  
  
 **SSVARIANT**識別共用体です。 vt メンバーの値に応じて、コンシューマーは読み取るメンバーを決めることができます。 vt 値は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型に対応します。 したがって、**SSVARIANT** 構造体には、任意の SQL Server 型を格納できます。 標準の OLE DB 型のデータ構造の詳細については、次を参照してください。[型インジケーター](https://go.microsoft.com/fwlink/?LinkId=122171)します。  
  
## <a name="remarks"></a>コメント  
 DataTypeCompat==80 の場合、いくつかの **SSVARIANT** サブタイプが文字列になります。 たとえば、次の vt 値は **SSVARIANT** では VT_SS_WVARSTRING として表されます。  
  
-   VT_SS_DATETIMEOFFSET  
  
-   VT_SS_DATETIME2  
  
-   VT_SS_TIME2  
  
-   VT_SS_DATE  
  
 DateTypeCompat == 0 の場合、これらの型はネイティブ形式で表されます。  
  
 SSPROP_INIT_DATATYPECOMPATIBILITY の詳細については、次を参照してください。[使用した Connection String Keywords with SQL Server Native Client を使用して](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)します。  
  
 Sqlncli.h ファイルには、メンバーの型を逆参照を簡略化するバリアント アクセス マクロが含まれています、 **SSVARIANT**構造体。 たとえば、V_SS_DATETIMEOFFSET を次のように使用できます。  
  
```  
memcpy(&V_SS_DATETIMEOFFSET(pssVar).tsoDateTimeOffsetVal, pDTO, cbNative);  
V_SS_DATETIMEOFFSET(pssVar).bScale = bScale;  
```  
  
 各メンバーのアクセス マクロの完全なセットを**SSVARIANT**構造体は、sqlncli.hi ファイルを参照してください。  
  
 次の表で、**SSVARIANT** 構造体のメンバーについて説明します。  
  
|Member|OLE DB 型インジケーター|OLE DB C データ型|vt の値|コメント|  
|------------|---------------------------|------------------------|--------------|--------------|  
|vt|SSVARTYPE|||**SSVARIANT** 構造体に格納される値の型を指定します。|  
|bTinyIntVal|DBTYPE_UI1|**BYTE**|**VT_SS_UI1**|では、 **tinyint** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型。|  
|sShortIntVal|DBTYPE_I2|**SHORT**|**VT_SS_I2**|では、 **smallint** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型。|  
|lIntVal|DBTYPE_I4|**LONG**|**VT_SS_I4**|では、 **int** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型。|  
|llBigIntVal|DBTYPE_I8|**LARGE_INTEGER**|**VT_SS_I8**|では、 **bigint** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型。|  
|fltRealVal|DBTYPE_R4|**float**|**VT_SS_R4**|では、**実際**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型。|  
|dblFloatVal|DBTYPE_R8|**double**|**VT_SS_R8**|では、 **float** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型。|  
|cyMoneyVal|DBTYPE_CY|**LARGE_INTEGER**|**VT_SS_MONEY VT_SS_SMALLMONEY**|では、 **money**と**smallmoney** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型。|  
|fBitVal|DBTYPE_BOOL|**VARIANT_BOOL**|**VT_SS_BIT**|では、**ビット**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型。|  
|rgbGuidVal|DBTYPE_GUID|**GUID**|**VT_SS_GUID**|では、 **uniqueidentifier** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型。|  
|numNumericVal|DBTYPE_NUMERIC|**DB_NUMERIC**|**VT_SS_NUMERIC**|では、**数値**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型。|  
|dDateVal|DBTYPE_DATE|**DBDATE**|**VT_SS_DATE**|**date**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型をサポートします。|  
|tsDateTimeVal|DBTYPE_DBTIMESTAMP|**DBTIMESTAMP**|**VT_SS_SMALLDATETIME VT_SS_DATETIME VT_SS_DATETIME2**|では、 **smalldatetime**、 **datetime**、および**datetime2** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型。|  
|Time2Val|DBTYPE_DBTIME2|**DBTIME2**|**VT_SS_TIME2**|では、**時間**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型。<br /><br /> 次のメンバーを含みます。<br /><br /> *tTime2Val* (**DBTIME2**)<br /><br /> *bScale* (**バイト**) の有効桁数を指定*tTime2Val*値。|  
|DateTimeVal|DBTYPE_DBTIMESTAMP|**DBTIMESTAMP**|**VT_SS_DATETIME2**|では、 **datetime2** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型。<br /><br /> 次のメンバーを含みます。<br /><br /> *tsDataTimeVal* (DBTIMESTAMP)<br /><br /> *bScale* (**バイト**) の有効桁数を指定*tsDataTimeVal*値。|  
|DateTimeOffsetVal|DBTYPE_DBTIMESTAMPOFSET|**DBTIMESTAMPOFFSET**|**VT_SS_DATETIMEOFFSET**|では、 **datetimeoffset** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型。<br /><br /> 次のメンバーを含みます。<br /><br /> *tsoDateTimeOffsetVal* (**DBTIMESTAMPOFFSET**)<br /><br /> *bScale* (**バイト**) の有効桁数を指定*tsoDateTimeOffsetVal*値。|  
|NCharVal|対応する OLE DB 型インジケーターはありません。|**構造体 _NCharVal**|**VT_SS_WVARSTRING、**<br /><br /> **VT_SS_WSTRING**|では、 **nchar**と**nvarchar** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型。<br /><br /> 次のメンバーを含みます。<br /><br /> *sActualLength* (**短い**) を文字列の実際の長さを指定します*pwchNCharVal*ポイント。 末尾の 0 は含まれません。<br /><br /> *sMaxLength* (**短い**) を文字列の最大長を指定します*pwchNCharVal*ポイント。<br /><br /> *pwchNCharVal* (**WCHAR** \*) 文字列へのポインター。<br /><br /> 使用されないメンバー: *rgbReserved*、 *dwReserved*、および*pwchReserved*します。|  
|CharVal|対応する OLE DB 型インジケーターはありません。|**構造体 _CharVal**|**VT_SS_STRING,**<br /><br /> **VT_SS_VARSTRING**|では、 **char**と**varchar** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型。<br /><br /> 次のメンバーを含みます。<br /><br /> *sActualLength* (**短い**) を文字列の実際の長さを指定します*pchCharVal*ポイント。 末尾の 0 は含まれません。<br /><br /> *sMaxLength* (**短い**) を文字列の最大長を指定します*pchCharVal*ポイント。<br /><br /> *pchCharVal* (**CHAR** \*) 文字列へのポインター。<br /><br /> 使用されないメンバー :<br /><br /> *rgbReserved*、 *dwReserved*、および*pwchReserved*します。|  
|BinaryVal|対応する OLE DB 型インジケーターはありません。|**struct _BinaryVal**|**VT_SS_VARBINARY,**<br /><br /> **VT_SS_BINARY**|では、**バイナリ**と**varbinary** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型。<br /><br /> 次のメンバーを含みます。<br /><br /> *sActualLength* (**短い**) しているデータの実際の長さを指定します*prgbBinaryVal*ポイント。<br /><br /> *sMaxLength* (**短い**) しているデータの最大長を指定します*prgbBinaryVal*ポイント。<br /><br /> *prgbBinaryVal* (**バイト** \*) バイナリ データへのポインター。<br /><br /> 使用されないメンバー: *dwReserved*します。|  
|UnknownType|未使用|未使用|未使用|未使用|  
|BLOBType|未使用|未使用|未使用|未使用|  
  
## <a name="see-also"></a>参照  
 [データ型&#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-data-types/data-types-ole-db.md)  
  
  

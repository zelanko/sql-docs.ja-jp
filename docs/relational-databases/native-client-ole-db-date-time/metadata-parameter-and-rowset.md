---
title: "パラメーターと行セットのメタデータ |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-date-time
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: metadata [OLE DB]
ms.assetid: 31b318a4-20e7-4db0-b367-eb9938859029
caps.latest.revision: "32"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d45c0eafa873e0697c791d478eeffada7cfd91a0
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="metadata---parameter-and-rowset"></a>メタデータ - パラメーターと行セット
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  このトピックでは、OLE DB の日付および時刻の機能強化に関連する、次の型と型メンバーについて説明します。  
  
-   DBBINDING 構造体  
  
-   **Icommandwithparameters::getparameterinfo**  
  
-   **Icommandwithparameters::setparameterinfo**  
  
-   **Icolumnsrowset::getcolumnsrowset**  
  
-   **Icolumnsinfo::getcolumninfo**  
  
## <a name="icommandwithparametersgetparameterinfo"></a>ICommandWithParameters::GetParameterInfo  
 介して DBPARAMINFO 構造体で、次の情報が返される*prgParamInfo*:  
  
|パラメーターの型|*wType*|*ulParamSize*|*bPrecision*|*bScale*|*dwFlags*<br /><br /> DBPARAMFLAGS_SS_ISVARIABLESCALE|  
|--------------------|-------------|-------------------|------------------|--------------|-----------------------------------------------------|  
|date|DBTYPE_DBDATE|6|10|0|Clear|  
|time|DBTYPE_DBTIME2|10|8, 10..16|0..7|オン|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|Clear|  
|datetime|DBTYPE_DBTIMESTAMP|16|23|3|Clear|  
|datetime2|DBTYPE_DBTIMESTAMP|16|19,21..27|0..7|オン|  
|datetimeoffset|DBTYPE_DBTIMESTAMPOFFSET|20|26,28..34|0..7|オン|  
  
 場合によっては、値の範囲が連続していないことに注意してください。 有効桁数が 0 より大きい場合は、小数点が追加されるためです。  
  
 DBPARAMFLAGS_SS_ISVARIABLESCALE は有効なに接続しているときにのみ、 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (またはそれ以降) サーバー。 下位レベルのサーバーに接続されている場合は、DBPARAMFLAGS_SS_ISVARIABLESCALE は設定しないでください。  
  
## <a name="icommandwithparameterssetparameterinfo-and-implied-parameter-types"></a>ICommandWithParameters::SetParameterInfo と暗黙のパラメーターの型  
 DBPARAMBINDINFO 構造体で提供される情報は、次の表に準拠する必要があります。  
  
|*して*<br /><br /> (プロバイダー固有)|*して*<br /><br /> (OLE DB 汎用)|*ulParamSize*|*bScale*|  
|----------------------------------------------------|-------------------------------------------------|-------------------|--------------|  
||DBTYPE_DATE|6|無視|  
|date|DBTYPE_DBDATE|6|無視|  
||DBTYPE_DBTIME|10|無視|  
|time|DBTYPE_DBTIME2|10|0..7|  
|smalldatetime||16|無視|  
|datetime||16|無視|  
|datetime2 または DBTYPE_DBTIMESTAMP|DBTYPE_DBTIMESTAMP|16|0..7|  
|datetimeoffset|DBTYPE_DBTIMESTAMPOFFSET|20|0..7|  
  
 *BPrecision*パラメーターは無視されます。  
  
 データをサーバーに送信する場合、"DBPARAMFLAGS_SS_ISVARIABLESCALE" は無視されます。 アプリケーションは、プロバイダー固有の型名を使用してレガシの表形式データ ストリーム (TDS) 型の使用を強制できます"**datetime**「と」**smalldatetime**"です。 接続しているときに[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)](またはそれ以降)、サーバー"**datetime2**"の形式が使用して、暗黙的なサーバー変換が発生、必要に応じて、型名が"**datetime2**"または"dbtype _DBTIMESTAMP"です。 *bScale*プロバイダー固有の型名の場合は無視されます"**datetime**「または」**smalldatetime**"を使用します。 それ以外の場合、アプリケーションでは、必ずを*bScale*が正しく設定されています。 MDAC からアップグレードしたアプリケーションと[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client を[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]"DBTYPE_DBTIMESTAMP"には、設定しない場合は失敗を使用する*bScale*正しくです。 サーバー インスタンスに接続している場合よりも前[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、 *bScale* "DBTYPE_DBTIMESTAMP"で 0 または 3 以外の値がエラーであり、E_FAIL が返されます。  
  
 Icommandwithparameters::setparameterinfo が呼び出されていない場合プロバイダー基、サーバーに iaccessor::createaccessor で指定されたバインディングの種類から次のように入力します。  
  
|バインドの種類|*して*<br /><br /> (プロバイダー固有)|  
|------------------|----------------------------------------------------|  
|DBTYPE_DATE|datetime2(0)|  
|DBTYPE_DBDATE|date|  
|DBTYPE_DBTIME|time(0)|  
|DBTYPE_DBTIME2|time(7)|  
|DBTYPE_DBTIMESTAMP|datetime2(7)|  
|DBTYPE_DBTIMESTAMPOFFSET|datetimeoffset(7)|  
  
## <a name="icolumnsrowsetgetcolumnsrowset"></a>IColumnsRowset::GetColumnsRowset  
 **Icolumnsrowset::getcolumnsrowset**次の列を返します。  
  
|列の型|DBCOLUMN_TYPE|DBCOLUM_COLUMNSIZE|DBCOLUMN_PRECISION|DBCOLUMN_SCALE、DBCOLUMN_DATETIMEPRECISION|DBCOLUMN_FLAGS、DBCOLUMNFLAGS_SS_ISVARIABLESCALE|  
|-----------------|--------------------|-------------------------|-------------------------|--------------------------------------------------|---------------------------------------------------------|  
|date|DBTYPE_DBDATE|6|10|0|Clear|  
|time|DBTYPE_DBTIME2|10|8, 10..16|0..7|オン|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|Clear|  
|datetime|DBTYPE_DBTIMESTAMP|16|23|3|Clear|  
|datetime2|DBTYPE_DBTIMESTAMP|16|19, 21..27|0..7|オン|  
|datetimeoffset|DBTYPE_DBTIMESTAMPOFFSET|20|26, 28..34|0..7|オン|  
  
 DBCOLUMN_FLAGS では、DBCOLUMNFLAGS_ISFIXEDLENGTH は日付/時刻型に対して常に true になり、次のフラグは常に false になります。  
  
-   DBCOLUMNFLAGS_CACHEDEFERRED  
  
-   DBCOLUMNFLAGS_ISBOOKMARK  
  
-   DBCOLUMNFLAGS_ISCHAPTER  
  
-   DBCOLUMNFLAGS_ISLONG  
  
-   DBCOLUMNFLAGS_ISROWID  
  
-   DBCOLUMNFLAGS_ISROWVER  
  
-   DBCOLUMNFLAGS_MAYDEFER  
  
 その他のフラグ (DBCOLUMNFLAGS_ISNULLABLE、DBCOLUMNFLAGS_MAYBENULL、DBCOLUMNFLAGS_WRITE、および DBCOLUMNFLAGS_WRITEUNKNOWN) は、列の定義方法と実際のクエリに応じて設定できます。  
  
 DBCOLUMN_FLAGS に用意されている新しいフラグ DBCOLUMNFLAGS_SS_ISVARIABLESCALE を使用すると、アプリケーションは、DBCOLUMN_TYPE が DBTYPE_DBTIMESTAMP である列のサーバーの種類を判断できます。 サーバーの種類を識別するには、DBCOLUMN_SCALE または DBCOLUMN_DATETIMEPRECISION も使用する必要があります。  
  
 DBCOLUMNFLAGS_SS_ISVARIABLESCALE は有効なに接続しているときにのみ、 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (またはそれ以降) サーバー。 下位レベルのサーバーに接続されている場合、DBCOLUMNFLAGS_SS_ISVARIABLESCALE は未定義となります。  
  
## <a name="icolumnsinfogetcolumninfo"></a>IColumnsInfo::GetColumnInfo  
 DBCOLUMNINFO 構造体から次の情報が返されます。  
  
|パラメーターの型|*wType*|*ulColumnSize*|*bPrecision*|*bScale*|*dwFlags*<br /><br /> DBPARAMFLAGS_SS_ISVARIABLESCALE|  
|--------------------|-------------|--------------------|------------------|--------------|-----------------------------------------------------|  
|date|DBTYPE_DBDATE|6|10|0|Clear|  
|time(1..7)|DBTYPE_DBTIME2|10|8, 10..16|0..7|オン|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|Clear|  
|datetime|DBTYPE_DBTIMESTAMP|16|23|3|Clear|  
|datetime2|DBTYPE_DBTIMESTAMP|16|19, 21..27|0..7|オン|  
|datetimeoffset|DBTYPE_DBTIMESTAMPOFFSET|20|26, 28..34|0..7|オン|  
  
 *DwFlags*DBCOLUMNFLAGS_ISFIXEDLENGTH は日付/時刻型の場合は true 常におよび、次のフラグは常に false:。  
  
-   DBCOLUMNFLAGS_CACHEDEFERRED  
  
-   DBCOLUMNFLAGS_ISBOOKMARK  
  
-   DBCOLUMNFLAGS_ISCHAPTER  
  
-   DBCOLUMNFLAGS_ISLONG  
  
-   DBCOLUMNFLAGS_ISROWID  
  
-   DBCOLUMNFLAGS_ISROWVER、MAYDEFER  
  
 その他のフラグ (DBCOLUMNFLAGS_ISNULLABLE、DBCOLUMNFLAGS_MAYBENULL、DBCOLUMNFLAGS_WRITE、および DBCOLUMNFLAGS_WRITEUNKNOWN) は、設定することができます。  
  
 新しいフラグ DBCOLUMNFLAGS_SS_ISVARIABLESCALE がで提供される*dwFlags*アプリケーションで、列のサーバーの種類を決定するを許可する場所*wType* DBTYPE_DBTIMESTAMP がします。 *bScale*サーバーの種類の識別にも使用する必要があります。  
  
## <a name="see-also"></a>参照  
 [メタデータ &#40;OLE DB&#41;](http://msdn.microsoft.com/library/605e3be5-aeea-4573-9847-b866ed3c8bff)  
  
  

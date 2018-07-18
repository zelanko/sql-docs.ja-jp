---
title: 行セット、およびパラメーター内のデータ型マッピング |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- mapping data types [OLE DB]
- DBTYPE_SQLVARIANT data type
- SQL Server Native Client OLE DB provider, data types
- rowsets [OLE DB], data type mapping
- data types [OLE DB]
- GetColumnInfo function
- parameters [OLE DB]
- SSPROP_ALLOWNATIVEVARIANT property
- GetParameterInfo function
- OLE DB, data types
ms.assetid: 3d831ff8-3b79-4698-b2c1-2b5dd2f8235c
caps.latest.revision: 40
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 77b7718febb0a6b8e8a8575ff776ffb44364b68a
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37422681"
---
# <a name="data-type-mapping-in-rowsets-and-parameters"></a>行セットとパラメーターでのデータ型マッピング
  行セットでは、パラメーター値として、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーを表す[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]次 OLE DB を使用してデータには、関数で報告された、データ型が定義されている**icolumnsinfo::getcolumninfo**と**Icommandwithparameters::getparameterinfo**します。  
  
|SQL Server データ型|OLE DB データ型|  
|--------------------------|----------------------|  
|**bigint**|DBTYPE_I8|  
|**[バイナリ]**|DBTYPE_BYTES|  
|**bit**|DBTYPE_BOOL|  
|**char**|DBTYPE_STR|  
|**datetime**|DBTYPE_DBTIMESTAMP|  
|**datetime2**|DBTYPE_DBTIME2|  
|**decimal**|DBTYPE_NUMERIC|  
|**float**|DBTYPE_R8|  
|**image**|DBTYPE_BYTES|  
|**int**|DBTYPE_I4|  
|**money**|DBTYPE_CY|  
|**nchar**|DBTYPE_WSTR|  
|**ntext**|DBTYPE_WSTR|  
|**numeric**|DBTYPE_NUMERIC|  
|**nvarchar**|DBTYPE_WSTR|  
|**real**|DBTYPE_R4|  
|**smalldatetime**|DBTYPE_DBTIMESTAMP|  
|**smallint**|DBTYPE_I2|  
|**smallmoney**|DBTYPE_CY|  
|**sql_variant**|DBTYPE_VARIANT、DBTYPE_SQLVARIANT|  
|**sysname**|DBTYPE_WSTR|  
|**text**|DBTYPE_STR|  
|**timestamp**|DBTYPE_BYTES|  
|**tinyint**|DBTYPE_UI1|  
|**UDT**|DBTYPE_UDT|  
|**uniqueidentifier**|DBTYPE_GUID|  
|**varbinary**|DBTYPE_BYTES|  
|**varchar**|DBTYPE_STR|  
|**XML**|DBTYPE_XML|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、図に示すように、コンシューマーから要求されたデータの変換をサポートしています。  
  
 **Sql_variant**オブジェクトは、いずれかのデータを保持できる[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]text、ntext、image、varchar (max)、nvarchar (max)、varbinary (max)、xml、timestamp、および Microsoft .NET Framework 共通言語ランタイム (CLR) 以外のデータ型ユーザー定義の型。 また、sql_variant データのインスタンスは、その基になる基本データ型として sql_variant を保持できません。 たとえば、列を含めることができます**smallint**いくつかの行の値**float** 、他の行の値と**char**/**nchar**残りの部分での値。  
  
> [!NOTE]  
>  **Sql_variant**データ型は Microsoft Visual Basic® と DBTYPE_VARIANT、DBTYPE_SQLVARIANT Variant データ型に似ています。  
  
 ときに**sql_variant**データを DBTYPE_VARIANT としてフェッチは、バッファーの VARIANT 構造体内に格納されます。 VARIANT 構造体のサブタイプがで定義されているサブタイプにマップされていない可能性がありますが、 **sql_variant**データ型。 **Sql_variant**一致するように、すべてのサブタイプの順序でデータを DBTYPE_SQLVARIANT としてフェッチするする必要があります。  
  
## <a name="dbtypesqlvariant-data-type"></a>DBTYPE_SQLVARIANT データ型  
 サポートするために、 **sql_variant**データ型、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、DBTYPE_SQLVARIANT と呼ばれるプロバイダー固有のデータ型を公開します。 ときに**sql_variant**データを DBTYPE_SQLVARIANT としてフェッチで、プロバイダー固有の SSVARIANT 構造体に格納されます。 SSVARIANT 構造体を含むすべてのサブタイプのサブタイプに一致する、 **sql_variant**データ型。  
  
 また、セッション プロパティ SSPROP_ALLOWNATIVEVARIANT を TRUE に設定する必要もあります。  
  
## <a name="provider-specific-property-sspropallownativevariant"></a>プロバイダー固有のプロパティ SSPROP_ALLOWNATIVEVARIANT  
 データをフェッチするときに、列またはパラメーターに返すデータ型を明示的に指定できます。 **IColumnsInfo**をバインドを使用して列情報を取得できます。 ときに**IColumnsInfo** SSPROP_ALLOWNATIVEVARIANT セッション プロパティが FALSE (既定値) の DBTYPE_VARIANT が返された場合にバインドするため、列情報の取得に使用**sql_variant**列。 SSPROP_ALLOWNATIVEVARIANT プロパティが FALSE の場合、DBTYPE_SQLVARIANT はサポートされません。 SSPROP_ALLOWNATIVEVARIANT プロパティを TRUE に設定すると、列の型は DBTYPE_SQLVARIANT として返されます。この場合、バッファーには SSVARIANT 構造体が保持されます。 フェッチで**sql_variant**データを DBTYPE_SQLVARIANT としてセッション プロパティ SSPROP_ALLOWNATIVEVARIANT を TRUE に設定する必要があります。  
  
 SSPROP_ALLOWNATIVEVARIANT プロパティはプロバイダー固有の DBPROPSET_SQLSERVERSESSION プロパティ セットの一部であり、セッション プロパティです。  
  
 DBTYPE_VARIANT は、他のすべての OLE DB プロバイダーに適用されます。  
  
## <a name="sspropallownativevariant"></a>SSPROP_ALLOWNATIVEVARIANT  
 SSPROP_ALLOWNATIVEVARIANT はセッション プロパティで、DBPROPSET_SQLSERVERSESSION プロパティ セットの一部です。  
  
|||  
|-|-|  
|SSPROP_ALLOWNATIVEVARIANT|型 : VT_BOOL<br /><br /> R/W: 読み取り/書き込み<br /><br /> 既定値 : VARIANT_FALSE<br /><br /> 説明 : データを DBTYPE_VARIANT と DBTYPE_SQLVARIANT のどちらとしてフェッチするかを決定します。<br /><br /> VARIANT_TRUE: 列の型は DBTYPE_SQLVARIANT として返され、バッファーには SSVARIANT 構造体が保持されます。<br /><br /> VARIANT_FALSE: 列の型は DBTYPE_VARIANT として返され、バッファーには VARIANT 構造体が保持されます。|  
  
## <a name="see-also"></a>参照  
 [データ型&#40;OLE DB&#41;](data-types-ole-db.md)  
  
  

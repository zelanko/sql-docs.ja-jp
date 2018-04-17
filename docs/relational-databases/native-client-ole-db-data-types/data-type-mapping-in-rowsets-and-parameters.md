---
title: 行セット、およびパラメーター内のデータ型マッピング |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-ole-db-data-types
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
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
caps.latest.revision: 41
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: e89293718abadb332eb69d106b5d73717bd53cd9
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="data-type-mapping-in-rowsets-and-parameters"></a>行セットとパラメーターでのデータ型マッピング
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  行セットでは、パラメーター値として、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーを表す[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]次 OLE DB を使用してデータには、関数で報告される、データ型が定義されている**icolumnsinfo::getcolumninfo**と**Icommandwithparameters::getparameterinfo**です。  
  
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
  
 **Sql_variant**オブジェクトは、任意のデータを保持できる[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]text、ntext、image、varchar (max)、nvarchar (max)、varbinary (max)、xml、timestamp、および Microsoft .NET Framework 共通言語ランタイム (CLR) を除くデータの種類ユーザー定義型です。 また、sql_variant データのインスタンスは、その基になる基本データ型として sql_variant を保持できません。 たとえば、列を含めることができます**smallint**一部の行に対して値**float**の他の行の値と**char**/**nchar**残りの部分の値。  
  
> [!NOTE]  
>  **Sql_variant**データ型は Microsoft Visual Basic®、DBTYPE_VARIANT、DBTYPE_SQLVARIANT にバリアント データ型に似ています。  
  
 ときに**sql_variant**データを DBTYPE_VARIANT としてフェッチ、バッファーの VARIANT 構造体内に格納されます。 VARIANT 構造体内のサブタイプがで定義されているサブタイプにマップされていない可能性がありますが、 **sql_variant**データ型。 **Sql_variant**に一致するすべてのサブタイプの順序でデータを DBTYPE_SQLVARIANT としてフェッチするし、必要があります。  
  
## <a name="dbtypesqlvariant-data-type"></a>DBTYPE_SQLVARIANT データ型  
 サポートするために、 **sql_variant**データ型、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、DBTYPE_SQLVARIANT と呼ばれるプロバイダー固有のデータ型を公開します。 ときに**sql_variant**データを DBTYPE_SQLVARIANT としてフェッチで、プロバイダー固有の SSVARIANT 構造体に格納されます。 SSVARIANT 構造体を含むすべてのサブタイプのサブタイプに一致する、 **sql_variant**データ型。  
  
 また、セッション プロパティ SSPROP_ALLOWNATIVEVARIANT を TRUE に設定する必要もあります。  
  
## <a name="provider-specific-property-sspropallownativevariant"></a>プロバイダー固有のプロパティ SSPROP_ALLOWNATIVEVARIANT  
 データをフェッチするときに、列またはパラメーターに返すデータ型を明示的に指定できます。 **IColumnsInfo**列情報を取得し、それをバインドを使用するも使用できます。 ときに**IColumnsInfo** SSPROP_ALLOWNATIVEVARIANT セッション プロパティが FALSE (既定値)、DBTYPE_VARIANT が返された場合のバインドのために、列情報の取得に使用**sql_variant**列です。 SSPROP_ALLOWNATIVEVARIANT プロパティが FALSE の場合、DBTYPE_SQLVARIANT はサポートされません。 SSPROP_ALLOWNATIVEVARIANT プロパティを TRUE に設定すると、列の型は DBTYPE_SQLVARIANT として返されます。この場合、バッファーには SSVARIANT 構造体が保持されます。 フェッチで**sql_variant**データを DBTYPE_SQLVARIANT としてセッション プロパティ SSPROP_ALLOWNATIVEVARIANT を TRUE に設定する必要があります。  
  
 SSPROP_ALLOWNATIVEVARIANT プロパティはプロバイダー固有の DBPROPSET_SQLSERVERSESSION プロパティ セットの一部であり、セッション プロパティです。  
  
 DBTYPE_VARIANT は、他のすべての OLE DB プロバイダーに適用されます。  
  
## <a name="sspropallownativevariant"></a>SSPROP_ALLOWNATIVEVARIANT  
 SSPROP_ALLOWNATIVEVARIANT はセッション プロパティで、DBPROPSET_SQLSERVERSESSION プロパティ セットの一部です。  
  
|||  
|-|-|  
|SSPROP_ALLOWNATIVEVARIANT|型 : VT_BOOL<br /><br /> R/W: 読み取り/書き込み<br /><br /> 既定値 : VARIANT_FALSE<br /><br /> 説明 : データを DBTYPE_VARIANT と DBTYPE_SQLVARIANT のどちらとしてフェッチするかを決定します。<br /><br /> VARIANT_TRUE: 列の型は DBTYPE_SQLVARIANT として返され、バッファーには SSVARIANT 構造体が保持されます。<br /><br /> VARIANT_FALSE: 列の型は DBTYPE_VARIANT として返され、バッファーには VARIANT 構造体が保持されます。|  
  
## <a name="see-also"></a>参照  
 [データ型 &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-data-types/data-types-ole-db.md)  
  
  

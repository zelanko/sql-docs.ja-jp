---
title: 行セットとパラメーターでのデータ型マッピング | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 41e5fceb2e69ab049bc7b82db5f67eb340d35ac9
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297002"
---
# <a name="data-type-mapping-in-rowsets-and-parameters"></a>行セットとパラメーターでのデータ型マッピング
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  行セットおよびパラメーター値として[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、ネイティブ クライアント OLE DB[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]プロバイダーは、関数**IColumnsInfo::GetColumnInfo**と**ICommandWithParameters::GetParameterInfo**で報告される次の OLE DB 定義データ型を使用してデータを表します。  
  
|SQL Server のデータ型|OLE DB データ型|  
|--------------------------|----------------------|  
|**bigint**|DBTYPE_I8|  
|**[バイナリ]**|DBTYPE_BYTES|  
|**bit**|DBTYPE_BOOL|  
|**char**|DBTYPE_STR|  
|**datetime**|DBTYPE_DBTIMESTAMP|  
|**datetime2**|DBTYPE_DBTIME2|  
|**10 進**|DBTYPE_NUMERIC|  
|**float**|DBTYPE_R8|  
|**イメージ**|DBTYPE_BYTES|  
|**int**|DBTYPE_I4|  
|**money**|DBTYPE_CY|  
|**nchar**|DBTYPE_WSTR|  
|**Ntext**|DBTYPE_WSTR|  
|**numeric**|DBTYPE_NUMERIC|  
|**nvarchar**|DBTYPE_WSTR|  
|**real**|DBTYPE_R4|  
|**smalldatetime**|DBTYPE_DBTIMESTAMP|  
|**smallint**|DBTYPE_I2|  
|**smallmoney**|DBTYPE_CY|  
|**sql_variant**|DBTYPE_VARIANT、DBTYPE_SQLVARIANT|  
|**Sysname**|DBTYPE_WSTR|  
|**text**|DBTYPE_STR|  
|**タイムスタンプ**|DBTYPE_BYTES|  
|**tinyint**|DBTYPE_UI1|  
|**UDT**|DBTYPE_UDT|  
|**UNIQUEIDENTIFIER**|DBTYPE_GUID|  
|**varbinary**|DBTYPE_BYTES|  
|**varchar**|DBTYPE_STR|  
|**XML**|DBTYPE_XML|  
  
 ネイティブ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアント OLE DB プロバイダーは、図に示すように、コンシューマーが要求したデータ変換をサポートします。  
  
 **sql_variant** オブジェクトは、text、ntext、image、varchar(max)、nvarchar(max)、varbinary(max)、xml、timestamp、および Microsoft .NET Framework 共通言語ランタイム (CLR) のユーザー定義型を除く、任意の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型のデータを保持できます。 また、sql_variant データのインスタンスは、その基になる基本データ型として sql_variant を保持できません。 たとえば、一部の行の列に **smallint** 型の値を格納し、他の行の列に **float** 型の値を格納して、残りの行の列に **char**/**nchar** 型の値を格納できます。  
  
> [!NOTE]  
>  **sql_variant** データ型は、Microsoft Visual Basic® の Variant データ型や、OLE DB の DBTYPE_VARIANT および DBTYPE_SQLVARIANT に似ています。  
  
 **sql_variant** 型のデータを DBTYPE_VARIANT としてフェッチすると、このデータはバッファーの VARIANT 構造体内に格納されます。 ただし、VARIANT 構造体内のサブタイプは、**sql_variant** データ型で定義されているサブタイプにマップされない場合があります。 このため、すべてのサブタイプを一致させるには、**sql_variant** 型のデータを DBTYPE_SQLVARIANT としてフェッチする必要があります。  
  
## <a name="dbtype_sqlvariant-data-type"></a>DBTYPE_SQLVARIANT データ型  
 **sql_variant**データ型をサポートするために、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント OLE DB プロバイダーは、DBTYPE_SQLVARIANTと呼ばれるプロバイダー固有のデータ型を公開します。 **sql_variant** 型のデータを DBTYPE_SQLVARIANT としてフェッチすると、データはプロバイダー固有の SSVARIANT 構造体内に格納されます。 SSVARIANT 構造体には、**sql_variant** データ型のサブタイプに一致するすべてのサブタイプが含まれています。  
  
 また、セッション プロパティ SSPROP_ALLOWNATIVEVARIANT を TRUE に設定する必要もあります。  
  
## <a name="provider-specific-property-ssprop_allownativevariant"></a>プロバイダー固有のプロパティ SSPROP_ALLOWNATIVEVARIANT  
 データをフェッチするときに、列またはパラメーターに返すデータ型を明示的に指定できます。 また、**IColumnsInfo** を使用して列情報を取得し、その情報をバインドに使用することもできます。 **IColumnsInfo** を使用してバインド用の列情報を取得するときに、SSPROP_ALLOWNATIVEVARIANT セッション プロパティが FALSE (既定値) の場合、**sql_variant** 型の列には DBTYPE_VARIANT が返されます。 SSPROP_ALLOWNATIVEVARIANT プロパティが FALSE の場合、DBTYPE_SQLVARIANT はサポートされません。 SSPROP_ALLOWNATIVEVARIANT プロパティを TRUE に設定すると、列の型は DBTYPE_SQLVARIANT として返されます。この場合、バッファーには SSVARIANT 構造体が保持されます。 **sql_variant** 型のデータを DBTYPE_SQLVARIANT としてフェッチするときは、セッション プロパティ SSPROP_ALLOWNATIVEVARIANT が TRUE に設定されている必要があります。  
  
 SSPROP_ALLOWNATIVEVARIANT プロパティはプロバイダー固有の DBPROPSET_SQLSERVERSESSION プロパティ セットの一部であり、セッション プロパティです。  
  
 DBTYPE_VARIANT は、他のすべての OLE DB プロバイダーに適用されます。  
  
## <a name="ssprop_allownativevariant"></a>SSPROP_ALLOWNATIVEVARIANT  
 SSPROP_ALLOWNATIVEVARIANT はセッション プロパティで、DBPROPSET_SQLSERVERSESSION プロパティ セットの一部です。  
  
|||  
|-|-|  
|SSPROP_ALLOWNATIVEVARIANT|型 : VT_BOOL<br /><br /> R/W: 読み取り/書き込み<br /><br /> 既定値 : VARIANT_FALSE<br /><br /> 説明 : データを DBTYPE_VARIANT と DBTYPE_SQLVARIANT のどちらとしてフェッチするかを決定します。<br /><br /> VARIANT_TRUE: 列の型は DBTYPE_SQLVARIANT として返され、バッファーには SSVARIANT 構造体が保持されます。<br /><br /> VARIANT_FALSE: 列の型は DBTYPE_VARIANT として返され、バッファーには VARIANT 構造体が保持されます。|  
  
## <a name="see-also"></a>参照  
 [データ型 &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-data-types/data-types-ole-db.md)  
  
  

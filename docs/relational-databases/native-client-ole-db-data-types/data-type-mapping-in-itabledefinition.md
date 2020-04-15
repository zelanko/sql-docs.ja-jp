---
title: ITableDefinition でのデータ型のマッピング | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- mapping data types [OLE DB]
- SQL Server Native Client OLE DB provider, data types
- ITableDefinition interface
- DBCOLUMNDESC structure
- data types [OLE DB]
- CreateTable function
- OLE DB, data types
ms.assetid: 13292d1f-c17e-4d11-bf98-3460a10cbb18
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d3e828efa513db1ace272e59379f77d063220290
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297063"
---
# <a name="data-type-mapping-in-itabledefinition"></a>ITableDefinition でのデータ型のマッピング
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  **ITableDefinition::CreateTable**関数を使用してテーブルを作成する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]場合、ネイティブ クライアント OLE [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DB プロバイダー コンシューマーは、渡される DBCOLUMNDESC 配列の*pwszTypeName*メンバーのデータ型を指定できます。 コンシューマーが列のデータ型を名前で指定する場合、DBCOLUMNDESC 構造体の *wType* メンバーで示される OLE DB データ型のマッピングは無視されます。  
  
 DBCOLUMNDESC 構造体*wType*メンバーを使用して OLE DB データ型を持つ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]新しい列データ型を指定する場合、ネイティブ クライアント OLE DB プロバイダーは、次のように OLE DB データ型をマップします。  
  
|OLE DB データ型|SQL Server<br /><br /> データ型 (data type)|関連情報|  
|----------------------|------------------------------|----------------------------|  
|DBTYPE_BOOL|**bit**||  
|DBTYPE_BYTES|**binary**、**varbinary**、**image**、**varbinary(max)**|ネイティブ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアント OLE DB プロバイダーは、構造体の*ulColumnSize*メンバーを検査します。 インスタンスの値とバージョンに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]基づいて、ネイティブ クライアントの OLE DB プロバイダは型を**image**にマップします。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<br /><br /> *ulColumnSize*の値が**バイナリ**データ型列の最大長より小さい場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント OLE DB プロバイダーは、DBCOLUMNDESC *rgPropertySets*メンバーを検査します。 DBPROP_COL_FIXEDLENGTHがVARIANT_TRUE場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、ネイティブ クライアントの OLE DB プロバイダは型を**バイナリ**にマップします。 プロパティの値がVARIANT_FALSE場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアントの OLE DB プロバイダは型を**varbinary**にマップします。 いずれの場合も、DBCOLUMNDESC の *ulColumnSize* メンバーによって、作成される SQL Server の列の幅が決まります。|  
|DBTYPE_CY|**money**||  
|DBTYPE_DBTIMESTAMP|**datetime**||  
|DBTYPE_GUID|**UNIQUEIDENTIFIER**||  
|DBTYPE_I2|**smallint**||  
|DBTYPE_I4|**int**||  
|DBTYPE_NUMERIC|**numeric**|ネイティブ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアント OLE DB プロバイダーは、**数値**列の精度とスケールを決定するために DBCOLUMDESC *bPrecision*と*bScale*メンバーを検査します。|  
|DBTYPE_R4|**real**||  
|DBTYPE_R8|**float**||  
|DBTYPE_STR|**char**、**varchar**、**text**、**varchar(max)**|ネイティブ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアント OLE DB プロバイダーは、構造体の*ulColumnSize*メンバーを検査します。 インスタンスの値とバージョンに基づいて、ネイティブ クライアントの OLE DB プロバイダは型を text にマップします。 **text** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<br /><br /> *ulColumnSize*の値がマルチバイト文字データ型列の最大長より小さい場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント OLE DB プロバイダーは、DBCOLUMNDESC *rgPropertySets*メンバーを検査します。 DBPROP_COL_FIXEDLENGTHがVARIANT_TRUE場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアントの OLE DB プロバイダは型を**char**にマップします。 プロパティの値がVARIANT_FALSE場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアントの OLE DB プロバイダは型を**varchar**にマップします。 いずれの場合も、DBCOLUMNDESC の *ulColumnSize* メンバーによって、作成される [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の列の幅が決まります。|  
|DBTYPE_UDT|**UDT**|UDT 列が必要な場合、**ITableDefinition::CreateTable** では、**DBCOLUMNDESC** 構造体の以下の情報が使用されます。<br /><br /> *pwSzTypeName* が無視されます。<br /><br /> *rgPropertySets* には、「[ユーザー定義型の使用](../../relational-databases/native-client/features/using-user-defined-types.md)」の**DBPROPSET_SQLSERVERCOLUMN** に関するセクションにある説明のとおり、**DBPROPSET_SQLSERVERCOLUMN** プロパティが設定されている必要があります。|  
|DBTYPE_UI1|**tinyint**||  
|DBTYPE_WSTR|**nchar**、**nvarchar**、**ntext**、**nvarchar(max)**|ネイティブ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアント OLE DB プロバイダーは、構造体の*ulColumnSize*メンバーを検査します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]値に基づいて、ネイティブ クライアント OLE DB プロバイダは型を**ntext**にマップします。<br /><br /> *ulColumnSize*の値が Unicode 文字データ型列の最大長より小さい場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント OLE DB プロバイダーは、DBCOLUMNDESC *rgPropertySets*メンバーを検査します。 DBPROP_COL_FIXEDLENGTHがVARIANT_TRUE場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント OLE DB プロバイダは型を**nchar**にマップします。 プロパティの値がVARIANT_FALSE場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアントの OLE DB プロバイダは型を**nvarchar**にマップします。 いずれの場合も、DBCOLUMNDESC の *ulColumnSize* メンバーによって、作成される [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の列の幅が決まります。|  
|DBTYPE_XML|**XML**||  
  
> [!NOTE]  
>  新しいテーブルの作成時には、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーによって上記の表に示した OLE DB データ型の列挙値のみがマップされます。 それ以外の OLE DB データ型の列が含まれたテーブルを作成すると、エラーが発生します。  
  
## <a name="see-also"></a>参照  
 [データ型 &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-data-types/data-types-ole-db.md)  
  
  

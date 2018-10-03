---
title: ITableDefinition でのデータ型マッピング |Microsoft Docs
description: ITableDefinition でのデータ型のマッピング
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- mapping data types [OLE DB]
- OLE DB Driver for SQL Server, data types
- ITableDefinition interface
- DBCOLUMNDESC structure
- data types [OLE DB]
- CreateTable function
- OLE DB, data types
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 4101c458b066ec34f010a5733510fb21e25e6840
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47834190"
---
# <a name="data-type-mapping-in-itabledefinition"></a>ITableDefinition でのデータ型のマッピング
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  OLE DB Driver for SQL Server のコンシューマーは、**ITableDefinition::CreateTable** 関数を使用してテーブルを作成するときに、渡される DBCOLUMNDESC 配列の *pwszTypeName* メンバーに [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のデータ型を指定できます。 コンシューマーが列のデータ型を名前で指定する場合、DBCOLUMNDESC 構造体の *wType* メンバーで示される OLE DB データ型のマッピングは無視されます。  
  
 DBCOLUMNDESC 構造体の *wType* メンバーを使用して、列の新しいデータ型を OLE DB データ型で指定するときは、OLE DB Driver for SQL Server では OLE DB データ型が次のようにマップされます。  
  
|OLE DB データ型|SQL Server<br /><br /> データ型 (data type)|関連情報|  
|----------------------|------------------------------|----------------------------|  
|DBTYPE_BOOL|**bit**||  
|DBTYPE_BYTES|**binary**、**varbinary**、**image**、**varbinary(max)**|OLE DB Driver for SQL Server を検査、 *ulColumnSize* DBCOLUMNDESC 構造体のメンバー。 値、およびのバージョンに基づいて、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]インスタンスの場合は、SQL Server にマップする型の OLE DB Driver**イメージ**します。<br /><br /> *ulColumnSize* の値が **binary** データ型の列の最大長よりも小さい場合、OLE DB Driver for SQL Server によって、DBCOLUMNDESC の *rgPropertySets* メンバーが調査されます。 OLE DB Driver for SQL Server にマップする型 DBPROP_COL_FIXEDLENGTH が VARIANT_TRUE の場合は、**バイナリ**します。 型をマッピングする、OLE DB Driver for SQL Server がサポートされるプロパティの値が VARIANT_FALSE の場合は、 **varbinary**します。 いずれの場合も、DBCOLUMNDESC の *ulColumnSize* メンバーによって、作成される SQL Server の列の幅が決まります。|  
|DBTYPE_CY|**money**||  
|DBTYPE_DBTIMESTAMP|**datetime2**||  
|DBTYPE_GUID|**uniqueidentifier**||  
|DBTYPE_I2|**smallint**||  
|DBTYPE_I4|**int**||  
|DBTYPE_I8|**bigint**||
|DBTYPE_NUMERIC|**numeric**|OLE DB Driver for SQL Server によって DBCOLUMDESC の *bPrecision* メンバーと *bScale* メンバーが調査され、**numeric** 型の列の有効桁数と小数点以下桁数が決定されます。|  
|DBTYPE_R4|**real**||  
|DBTYPE_R8|**float**||  
|DBTYPE_STR|**char**、**varchar**、**text**、**varchar(max)**|OLE DB Driver for SQL Server を検査、 *ulColumnSize* DBCOLUMNDESC 構造体のメンバー。 値とのバージョンに基づいて、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]インスタンスの場合は、SQL Server にマップする型の OLE DB Driver**テキスト**します。<br /><br /> *ulColumnSize* の値がマルチバイト文字のデータ型の列の最大長よりも小さい場合、OLE DB Driver for SQL Server によって、DBCOLUMNDESC の *rgPropertySets* メンバーが調査されます。 OLE DB Driver for SQL Server にマップする型 DBPROP_COL_FIXEDLENGTH が VARIANT_TRUE の場合は、 **char**します。 型をマッピングする、OLE DB Driver for SQL Server がサポートされるプロパティの値が VARIANT_FALSE の場合は、 **varchar**します。 いずれの場合も、DBCOLUMNDESC の *ulColumnSize* メンバーによって、作成される [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の列の幅が決まります。|  
|DBTYPE_UDT|**UDT**|UDT 列が必要な場合、**ITableDefinition::CreateTable** では、**DBCOLUMNDESC** 構造体の以下の情報が使用されます。<br /><br /> *pwSzTypeName*は無視されます。<br /><br /> *rgPropertySets*含める必要があります、 **DBPROPSET_SQLSERVERCOLUMN**プロパティに関するセクションで説明したように設定**DBPROPSET_SQLSERVERCOLUMN**の[ユーザーの種類](../../oledb/features/using-user-defined-types.md).|  
|DBTYPE_UI1|**tinyint**||  
|DBTYPE_VARIANT|**sql_variant**||
|DBTYPE_WSTR|**nchar**、**nvarchar**、**ntext**、**nvarchar(max)**|OLE DB Driver for SQL Server を検査、 *ulColumnSize* DBCOLUMNDESC 構造体のメンバー。 型にマップされます、OLE DB Driver for SQL Server の値に基づいて、 **ntext**します。<br /><br /> *ulColumnSize* の値が Unicode 文字のデータ型の列の最大長よりも小さい場合、OLE DB Driver for SQL Server によって、DBCOLUMNDESC の *rgPropertySets* メンバーが調査されます。 OLE DB Driver for SQL Server にマップする型 DBPROP_COL_FIXEDLENGTH が VARIANT_TRUE の場合は、 **nchar**します。 型をマッピングする、OLE DB Driver for SQL Server がサポートされるプロパティの値が VARIANT_FALSE の場合は、 **nvarchar**します。 いずれの場合も、DBCOLUMNDESC の *ulColumnSize* メンバーによって、作成される [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の列の幅が決まります。|  
|DBTYPE_XML|**XML**||  

> [!NOTE]  
>  新しいテーブルの作成時には、OLE DB Driver for SQL Server によって、上記の表に示した OLE DB データ型の列挙値のみがマップされます。 それ以外の OLE DB データ型の列が含まれたテーブルを作成すると、エラーが発生します。  

## <a name="see-also"></a>参照  
 [データ型&#40;OLE DB&#41;](../../oledb/ole-db-data-types/data-types-ole-db.md)  
  
  

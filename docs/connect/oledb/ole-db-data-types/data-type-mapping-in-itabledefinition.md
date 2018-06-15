---
title: ITableDefinition でのデータ型マッピング |Microsoft ドキュメント
description: ITableDefinition でのデータ型マッピング
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-data-types
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
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
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: d613fc7be394bbf16c86c5e217e3dfe83a4296a1
ms.sourcegitcommit: e1bc8c486680e6d6929c0f5885d97d013a537149
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2018
ms.locfileid: "35666352"
---
# <a name="data-type-mapping-in-itabledefinition"></a>ITableDefinition でのデータ型のマッピング
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  使用してテーブルを作成するときに、 **itabledefinition::createtable** 、OLE DB Driver for SQL Server コンシューマーが指定できる関数、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]データ型、 *pwszTypeName*のメンバー、渡される DBCOLUMNDESC 配列。 OLE DB データ型で表されるマッピングのコンシューマーは、名前によって列のデータ型を指定する場合、 *wType* DBCOLUMNDESC 構造体のメンバーは無視されます。  
  
 DBCOLUMNDESC 構造体を使用して OLE DB データ型を持つ新しい列のデータ型を指定するときに*wType*メンバー、SQL Server の OLE DB Driver は、OLE DB データ型を次のようにマップします。  
  
|OLE DB データ型|SQL Server<br /><br /> データ型 (data type)|関連情報|  
|----------------------|------------------------------|----------------------------|  
|DBTYPE_BOOL|**bit**||  
|DBTYPE_BYTES|**バイナリ**、 **varbinary**、**イメージ、** または**varbinary (max)**|SQL Server の OLE DB ドライバーを検査、 *ulColumnSize* DBCOLUMNDESC 構造体のメンバーです。 値、およびのバージョンに基づいて、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]インスタンスの場合は、SQL Server にマップする型の OLE DB Driver**イメージ**です。<br /><br /> 場合の値*ulColumnSize*の最大長よりも小さい、**バイナリ**SQL Server の OLE DB Driver は、DBCOLUMNDESC を検査し、データ型の列、 *rgPropertySets*メンバー。 SQL Server の OLE DB ドライバーに型をマップ DBPROP_COL_FIXEDLENGTH が VARIANT_TRUE の場合は、**バイナリ**です。 SQL Server の OLE DB ドライバーに型をマップ プロパティの値が VARIANT_FALSE の場合は、 **varbinary**です。 どちらの場合、DBCOLUMNDESC の*ulColumnSize*メンバーが作成された SQL Server の列の幅を決定します。|  
|DBTYPE_CY|**money**||  
|DBTYPE_DBTIMESTAMP|**datetime2**||  
|DBTYPE_GUID|**uniqueidentifier**||  
|DBTYPE_I2|**smallint**||  
|DBTYPE_I4|**int**||  
|DBTYPE_I8|**bigint**||
|DBTYPE_NUMERIC|**numeric**|SQL Server の OLE DB Driver は、DBCOLUMDESC を検査*bPrecision*と*bScale*有効桁数を決定し、対応するメンバー、**数値**列です。|  
|DBTYPE_R4|**real**||  
|DBTYPE_R8|**float**||  
|DBTYPE_STR|**char**、 **varchar**、**テキスト、** または**varchar (max)**|SQL Server の OLE DB ドライバーを検査、 *ulColumnSize* DBCOLUMNDESC 構造体のメンバーです。 値とのバージョンに基づいて、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]インスタンスの場合は、SQL Server にマップする型の OLE DB Driver**テキスト**です。<br /><br /> 場合の値*ulColumnSize*は SQL Server は、DBCOLUMNDESC を検査し、マルチバイト文字のデータ型の列で、OLE DB ドライバーの最大長よりも小さい*rgPropertySets*メンバー。 SQL Server の OLE DB ドライバーに型をマップ DBPROP_COL_FIXEDLENGTH が VARIANT_TRUE の場合は、 **char**です。 SQL Server の OLE DB ドライバーに型をマップ プロパティの値が VARIANT_FALSE の場合は、 **varchar**です。 どちらの場合、DBCOLUMNDESC の*ulColumnSize*メンバーの幅を決定する、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]列を作成します。|  
|DBTYPE_UDT|**UDT**|次の情報が使用される**DBCOLUMNDESC**構造体**itabledefinition::createtable** UDT 列が必要な場合。<br /><br /> *pwSzTypeName*は無視されます。<br /><br /> *rgPropertySets*含める必要があります、 **DBPROPSET_SQLSERVERCOLUMN**プロパティに関するセクションで説明したように設定**DBPROPSET_SQLSERVERCOLUMN**の[ユーザーの種類](../../oledb/features/using-user-defined-types.md).|  
|DBTYPE_UI1|**tinyint**||  
|DBTYPE_VARIANT|**sql_variant**||
|DBTYPE_WSTR|**nchar**、 **nvarchar**、 **ntext、** または**nvarchar (max)**|SQL Server の OLE DB ドライバーを検査、 *ulColumnSize* DBCOLUMNDESC 構造体のメンバーです。 SQL Server の OLE DB Driver に型をマップ値に基づいて、 **ntext**です。<br /><br /> 場合の値*ulColumnSize*は SQL Server を検査、DBCOLUMNDESC の Unicode 文字データ型列、OLE DB ドライバーの最大長よりも小さい*rgPropertySets*メンバー。 SQL Server の OLE DB ドライバーに型をマップ DBPROP_COL_FIXEDLENGTH が VARIANT_TRUE の場合は、 **nchar**です。 SQL Server の OLE DB ドライバーに型をマップ プロパティの値が VARIANT_FALSE の場合は、 **nvarchar**です。 どちらの場合、DBCOLUMNDESC の*ulColumnSize*メンバーの幅を決定する、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]列を作成します。|  
|DBTYPE_XML|**XML**||  

> [!NOTE]  
>  新しいテーブルを作成するときに、OLE DB Driver for SQL Server は、OLE DB データ型の列挙値のみ、前の表で指定されたをマップします。 それ以外の OLE DB データ型の列が含まれたテーブルを作成すると、エラーが発生します。  

## <a name="see-also"></a>参照  
 [データ型&#40;OLE DB&#41;](../../oledb/ole-db-data-types/data-types-ole-db.md)  
  
  

---
title: ITableDefinition でのデータ型マッピング |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-ole-db-data-types
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
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
caps.latest.revision: 35
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: f87118e72b1ab36a72c8ee28369551792e37d677
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="data-type-mapping-in-itabledefinition"></a>ITableDefinition でのデータ型のマッピング
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  使用してテーブルを作成するときに、 **itabledefinition::createtable** 、関数、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーのコンシューマーが指定できます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型、 *pwszTypeName*渡される DBCOLUMNDESC 配列のメンバーです。 OLE DB データ型で表されるマッピングのコンシューマーは、名前によって列のデータ型を指定する場合、 *wType* DBCOLUMNDESC 構造体のメンバーは無視されます。  
  
 DBCOLUMNDESC 構造体を使用して OLE DB データ型を持つ新しい列のデータ型を指定するときに*wType* 、メンバー、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーが OLE DB データ型を次のようにマップします。  
  
|OLE DB データ型|SQL Server<br /><br /> データ型 (data type)|関連情報|  
|----------------------|------------------------------|----------------------------|  
|DBTYPE_BOOL|**bit**||  
|DBTYPE_BYTES|**バイナリ**、 **varbinary**、**イメージ、**または**varbinary (max)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーによって、 *ulColumnSize* DBCOLUMNDESC 構造体のメンバーです。 値、およびのバージョンに基づいて、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、インスタンス、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーの型をマップする**イメージ**です。<br /><br /> 場合の値*ulColumnSize*の最大長よりも小さい、**バイナリ**データ型の列、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーによって、DBCOLUMNDESC *rgPropertySets*メンバー。 DBPROP_COL_FIXEDLENGTH が VARIANT_TRUE の場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーの型をマップする**バイナリ**です。 プロパティの値が VARIANT_FALSE の場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーの型をマップする**varbinary**です。 どちらの場合、DBCOLUMNDESC の*ulColumnSize*メンバーが作成された SQL Server の列の幅を決定します。|  
|DBTYPE_CY|**money**||  
|DBTYPE_DBTIMESTAMP|**datetime**||  
|DBTYPE_GUID|**uniqueidentifier**||  
|DBTYPE_I2|**smallint**||  
|DBTYPE_I4|**int**||  
|DBTYPE_NUMERIC|**numeric**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーを検査、DBCOLUMDESC *bPrecision*と*bScale*有効桁数を決定し、対応するメンバー、**数値**列です。|  
|DBTYPE_R4|**real**||  
|DBTYPE_R8|**float**||  
|DBTYPE_STR|**char**、 **varchar**、**テキスト、**または**varchar (max)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーによって、 *ulColumnSize* DBCOLUMNDESC 構造体のメンバーです。 値とのバージョンに基づいて、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、インスタンス、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーの型をマップする**テキスト**です。<br /><br /> 場合の値*ulColumnSize*マルチバイト文字データ型の列の最大長よりも小さい、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーによって、DBCOLUMNDESC *rgPropertySets*メンバー。 DBPROP_COL_FIXEDLENGTH が VARIANT_TRUE の場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーの型をマップする**char**です。 プロパティの値が VARIANT_FALSE の場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーの型をマップする**varchar**です。 どちらの場合、DBCOLUMNDESC の*ulColumnSize*メンバーの幅を決定する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]列を作成します。|  
|DBTYPE_UDT|**UDT**|次の情報が使用される**DBCOLUMNDESC**構造体**itabledefinition::createtable** UDT 列が必要な場合。<br /><br /> *pwSzTypeName*は無視されます。<br /><br /> *rgPropertySets*含める必要があります、 **DBPROPSET_SQLSERVERCOLUMN**プロパティに関するセクションで説明したように設定**DBPROPSET_SQLSERVERCOLUMN**の[ユーザーの種類](../../relational-databases/native-client/features/using-user-defined-types.md).|  
|DBTYPE_UI1|**tinyint**||  
|DBTYPE_WSTR|**nchar**、 **nvarchar**、 **ntext、**または**nvarchar (max)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーによって、 *ulColumnSize* DBCOLUMNDESC 構造体のメンバーです。 値に基づいて、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーの型をマップする**ntext**です。<br /><br /> 場合の値*ulColumnSize*の Unicode 文字データ型列の最大サイズよりも小さい、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーによって、DBCOLUMNDESC *rgPropertySets*メンバー。 DBPROP_COL_FIXEDLENGTH が VARIANT_TRUE の場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーの型をマップする**nchar**です。 プロパティの値が VARIANT_FALSE の場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーの型をマップする**nvarchar**です。 どちらの場合、DBCOLUMNDESC の*ulColumnSize*メンバーの幅を決定する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]列を作成します。|  
|DBTYPE_XML|**XML**||  
  
> [!NOTE]  
>  新しいテーブルの作成時には、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーによって上記の表に示した OLE DB データ型の列挙値のみがマップされます。 それ以外の OLE DB データ型の列が含まれたテーブルを作成すると、エラーが発生します。  
  
## <a name="see-also"></a>参照  
 [データ型 &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-data-types/data-types-ole-db.md)  
  
  

---
title: ITableDefinition | でのデータ型マッピングMicrosoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e561742406c173b69bfb5040c2f2f51efdf5ed64
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63201215"
---
# <a name="data-type-mapping-in-itabledefinition"></a>ITableDefinition でのデータ型のマッピング
  **Itabledefinition:: CreateTable**関数を使用してテーブルを作成する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]場合、Native Client OLE DB プロバイダーコンシューマー [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は、渡される dbcolumndesc 配列の*pwszTypeName*メンバーにデータ型を指定できます。 コンシューマーが列のデータ型を名前で指定する場合、DBCOLUMNDESC 構造体の *wType* メンバーで示される OLE DB データ型のマッピングは無視されます。  
  
 DBCOLUMNDESC 構造の*Wtype*メンバーを使用して OLE DB データ型で新しい列のデータ型[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を指定する場合、Native Client OLE DB プロバイダーは OLE DB のデータ型を次のようにマップします。  
  
|OLE DB データ型|SQL Server<br /><br /> データ型|追加情報|  
|----------------------|------------------------------|----------------------------|  
|DBTYPE_BOOL|**bit**||  
|DBTYPE_BYTES|**binary**、 **varbinary**、 **image、** または**varbinary (max)**|Native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client OLE DB プロバイダーは、DBCOLUMNDESC 構造体の*ulcolumnsize*メンバーを検査します。 Native Client OLE DB プロバイダーは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、値とインスタンスのバージョンに基づいて、型を**image**にマップします。<br /><br /> *Ulcolumnsize*の値が**binary**データ型の列の最大長よりも小さい場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] NATIVE CLIENT OLE DB プロバイダーは dbcolumndesc *rgPropertySets*メンバーを検査します。 DBPROP_COL_FIXEDLENGTH が VARIANT_TRUE 場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーによって型が**バイナリ**にマップされます。 プロパティの値が VARIANT_FALSE 場合、Native Client OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]プロバイダーはその型を**varbinary**にマップします。 いずれの場合も、DBCOLUMNDESC の *ulColumnSize* メンバーによって、作成される SQL Server の列の幅が決まります。|  
|DBTYPE_CY|**money**||  
|DBTYPE_DBTIMESTAMP|**DATETIME**||  
|DBTYPE_GUID|**UNIQUEIDENTIFIER**||  
|DBTYPE_I2|**smallint**||  
|DBTYPE_I4|**int**||  
|DBTYPE_NUMERIC|**番号**|Native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client OLE DB プロバイダーは、**数値**列の有効桁数と小数点以下桁数を決定するために、Dbcolumn desc *Bprecision*メンバーと*bprecision*メンバーを検査します。|  
|DBTYPE_R4|**本当の**||  
|DBTYPE_R8|**float**||  
|DBTYPE_STR|**char**、 **varchar**、 **text、** または**varchar (max)**|Native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client OLE DB プロバイダーは、DBCOLUMNDESC 構造体の*ulcolumnsize*メンバーを検査します。 Native Client OLE DB プロバイダーは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスの値とバージョン[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に基づいて、型を**テキスト**にマップします。<br /><br /> *Ulcolumnsize*の値がマルチバイト文字のデータ型の列の最大長よりも小さい場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT OLE DB プロバイダーは dbcolumndesc *rgPropertySets*メンバーを検査します。 DBPROP_COL_FIXEDLENGTH が VARIANT_TRUE 場合、Native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client OLE DB プロバイダーは型を**char**にマップします。 プロパティの値が VARIANT_FALSE 場合、Native Client OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]プロバイダーは型を**varchar**にマップします。 いずれの場合も、DBCOLUMNDESC の *ulColumnSize* メンバーによって、作成される [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の列の幅が決まります。|  
|DBTYPE_UDT|**UDT**|UDT 列が必要な場合`DBCOLUMNDESC`は、次の情報を**Itabledefinition:: CreateTable**によって構造体で使用します。<br /><br /> -   *pwSzTypeName*は無視されます。<br />-   *rgPropertySets*には`DBPROPSET_SQLSERVERCOLUMN`、 `DBPROPSET_SQLSERVERCOLUMN` 「」の「[ユーザー定義型の使用](../native-client/features/using-user-defined-types.md)」で説明されているように、プロパティセットを含める必要があります。|  
|DBTYPE_UI1|**tinyint**||  
|DBTYPE_WSTR|**nchar**、 **nvarchar**、 **ntext、** または**nvarchar (max)**|Native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client OLE DB プロバイダーは、DBCOLUMNDESC 構造体の*ulcolumnsize*メンバーを検査します。 Native Client OLE DB プロバイダーは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、値に基づいて、型を**ntext**にマップします。<br /><br /> *Ulcolumnsize*の値が Unicode 文字のデータ型の列の最大長よりも小さい場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT OLE DB プロバイダーは dbcolumndesc *rgPropertySets*メンバーを検査します。 DBPROP_COL_FIXEDLENGTH が VARIANT_TRUE 場合、Native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client OLE DB プロバイダーはその型を**nchar**にマップします。 プロパティの値が VARIANT_FALSE 場合は、Native Client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB プロバイダーによって型が**nvarchar**にマップされます。 いずれの場合も、DBCOLUMNDESC の *ulColumnSize* メンバーによって、作成される [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の列の幅が決まります。|  
|DBTYPE_XML|**XML**||  
  
> [!NOTE]  
>  新しいテーブルの作成時には、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーによって上記の表に示した OLE DB データ型の列挙値のみがマップされます。 それ以外の OLE DB データ型の列が含まれたテーブルを作成すると、エラーが発生します。  
  
## <a name="see-also"></a>参照  
 [データ型 &#40;OLE DB&#41;](data-types-ole-db.md)  
  
  

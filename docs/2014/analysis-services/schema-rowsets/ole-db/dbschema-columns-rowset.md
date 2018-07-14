---
title: DBSCHEMA_COLUMNS 行セット |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- DBSCHEMA_COLUMNS
topic_type:
- apiref
helpviewer_keywords:
- DBSCHEMA_COLUMNS rowset
ms.assetid: 653bdd07-a533-4a99-8b6a-6e5c7322e1f3
caps.latest.revision: 40
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6fa933eb153b0d8de4c2fec4ba92b072954be141
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37267578"
---
# <a name="dbschemacolumns-rowset"></a>DBSCHEMA_COLUMNS 行セット
  指定された制約条件を満たすすべての列の列情報を提供します。  
  
## <a name="rowset-columns"></a>行セットの列  
 `DBSCHEMA_COLUMNS`行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|説明|  
|-----------------|--------------------|------------|-----------------|  
|`TABLE_CATALOG`|`DBTYPE_WSTR`||データベースの名前。|  
|`TABLE_SCHEMA`|`DBTYPE_WSTR`||サポートされていません。|  
|`TABLE_NAME`|`DBTYPE_WSTR`||キューブの名前。|  
|`COLUMN_NAME`|`DBTYPE_WSTR`||属性階層またはメジャーの名前。|  
|`COLUMN_GUID`|`DBTYPE_GUID`||サポートされていません。|  
|`COLUMN_PROPID`|`DBTYPE_UI4`||サポートされていません。|  
|`ORDINAL_POSITION`|`DBTYPE_UI4`||1 から始まる列の位置。|  
|`COLUMN_HAS_DEFAULT`|`DBTYPE_BOOL`||サポートされていません。|  
|`COLUMN_DEFAULT`|`DBTYPE_WSTR`||サポートされていません。|  
|`COLUMN_FLAGS`|`DBTYPE_UI4`||列のプロパティを示す `DBCOLUMNFLAGS` ビットマスク。 DBCOLUMNFLAGS Enumerated Type' を参照してください[icolumnsinfo::getcolumninfo](http://msdn2.microsoft.com/library/ms722704.aspx)|  
|`IS_NULLABLE`|`DBTYPE_BOOL`||常に返します`false`します。|  
|`DATA_TYPE`|`DBTYPE_WSTR`<br /><br /> `DBTYPE_VARIANT`||列のデータ型。 ディメンション列の文字列とメジャーのバリアントが返ります。|  
|`TYPE_GUID`|`DBTYPE_GUID`||サポートされていません。|  
|`CHARACTER_MAXIMUM_LENGTH`|`DBTYPE_UI4`||列内の値の可能な最大長。<br /><br /> これは `DataSize` 内の `DataItem` プロパティから取得されます。|  
|`CHARACTER_OCTET_LENGTH`|`DBTYPE_UI4`||文字またはバイナリの列について、列に格納できる値の最大の長さ (単位はバイト)。<br /><br /> 値ゼロ (0) は、列に最大の長さがないことを示します。<br /><br /> バイナリまたは文字のデータ型を返さない列には `NULL` が返されます。|  
|`NUMERIC_PRECISION`|`DBTYPE_UI2`||`DBTYPE_VARNUMERIC` 以外の数値データ型の列の最大有効桁数。|  
|`NUMERIC_SCALE`|`DBTYPE_I2`||`DBTYPE_DECIMAL`、`DBTYPE_NUMERIC`、`DBTYPE_VARNUMERIC` の小数点以下の桁数。 それ以外の場合は `NULL` になります。|  
|`DATETIME_PRECISION`|`DBTYPE_UI4`||サポートされていません。|  
|`CHARACTER_SET_CATALOG`|`DBTYPE_WSTR`||サポートされていません。|  
|`CHARACTER_SET_SCHEMA`|`DBTYPE_WSTR`||サポートされていません。|  
|`CHARACTER_SET_NAME`|`DBTYPE_WSTR`||サポートされていません。|  
|`COLLATION_CATALOG`|`DBTYPE_WSTR`||サポートされていません。|  
|`COLLATION_SCHEMA`|`DBTYPE_WSTR`||サポートされていません。|  
|`COLLATION_NAME`|`DBTYPE_WSTR`||サポートされていません。|  
|`DOMAIN_CATALOG`|`DBTYPE_WSTR`||サポートされていません。|  
|`DOMAIN_SCHEMA`|`DBTYPE_WSTR`||サポートされていません。|  
|`DOMAIN_NAME`|`DBTYPE_WSTR`||サポートされていません。|  
|`DESCRIPTION`|`DBTYPE_WSTR`||サポートされていません。|  
|`COLUMN_OLAP_TYPE`|`DBTYPE_WSTR`||オブジェクトの OLAP 型。<br /><br /> `MEASURE` は、オブジェクトがメジャーであることを示します。<br /><br /> `ATTRIBUTE` は、オブジェクトがディメンション属性であることを示します。<br /><br /> `SCHEMA` は、オブジェクトがスキーマ内の列であることを示します。|  
  
 行セットは、`TABLE_CATALOG`、`TABLE_SCHEMA`、`TABLE_NAME` を基準に並べ替えることができます。  
  
## <a name="restriction-columns"></a>制限の列  
 `DBSCHEMA_COLUMNS`行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|`TABLE_CATALOG`|`DBTYPE_WSTR`|省略可|  
|`TABLE_SCHEMA`|`DBTYPE_WSTR`|省略可|  
|`TABLE_NAME`|`DBTYPE_WSTR`|省略可|  
|`COLUMN_NAME`|`DBTYPE_WSTR`|省略可|  
|`COLUMN_OLAP_TYPE`|`DBTYPE_WSTR`|省略可|  
  
## <a name="see-also"></a>参照  
 [OLE DB Schema 行セット](ole-db-schema-rowsets.md)  
  
  

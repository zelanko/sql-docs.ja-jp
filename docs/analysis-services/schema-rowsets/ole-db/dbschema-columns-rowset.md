---
title: DBSCHEMA_COLUMNS 行セット |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2bb1fec6a1633f545f0c65feda93c7e19c649a6e
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34029693"
---
# <a name="dbschemacolumns-rowset"></a>DBSCHEMA_COLUMNS 行セット
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  指定された制約条件を満たすすべての列の列情報を提供します。  
  
## <a name="rowset-columns"></a>行セットの列  
 **DBSCHEMA_COLUMNS**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|Description|  
|-----------------|--------------------|------------|-----------------|  
|**TABLE_CATALOG**|**DBTYPE_WSTR**||データベースの名前。|  
|**TABLE_SCHEMA**|**DBTYPE_WSTR**||サポートされていません。|  
|**TABLE_NAME**|**DBTYPE_WSTR**||キューブの名前。|  
|**COLUMN_NAME**|**DBTYPE_WSTR**||属性階層またはメジャーの名前。|  
|**COLUMN_GUID**|**DBTYPE_GUID 型**||サポートされていません。|  
|**COLUMN_PROPID**|**DBTYPE_UI4**||サポートされていません。|  
|**ORDINAL_POSITION**|**DBTYPE_UI4**||1 から始まる列の位置。|  
|**COLUMN_HAS_DEFAULT**|**DBTYPE_BOOL**||サポートされていません。|  
|**COLUMN_DEFAULT**|**DBTYPE_WSTR**||サポートされていません。|  
|**COLUMN_FLAGS**|**DBTYPE_UI4**||A **DBCOLUMNFLAGS**列のプロパティを示すビットマスク。 'DBCOLUMNFLAGS Enumerated Type」を参照してください[icolumnsinfo::getcolumninfo](http://msdn2.microsoft.com/library/ms722704.aspx)|  
|**IS_NULLABLE**|**DBTYPE_BOOL**||常に返します**false**です。|  
|**DATA_TYPE**|**DBTYPE_WSTR**<br /><br /> **DBTYPE_VARIANT**||列のデータ型。 ディメンション列の文字列とメジャーのバリアントが返ります。|  
|**TYPE_GUID**|**DBTYPE_GUID 型**||サポートされていません。|  
|**CHARACTER_MAXIMUM_LENGTH**|**DBTYPE_UI4**||列内の値の可能な最大長。<br /><br /> これから取得されますが、 **DataSize**プロパティに、 **DataItem**です。|  
|**CHARACTER_OCTET_LENGTH**|**DBTYPE_UI4**||文字またはバイナリの列について、列に格納できる値の最大の長さ (単位はバイト)。<br /><br /> 値ゼロ (0) は、列に最大の長さがないことを示します。<br /><br /> **NULL**バイナリまたは文字のデータ型を返さない列が返されます。|  
|**NUMERIC_PRECISION**|**DBTYPE_UI2**||数値データの列の最大有効桁数の型以外の**DBTYPE_VARNUMERIC**です。|  
|**NUMERIC_SCALE**|**DBTYPE_I2**||小数点の右側にある数字の数**DBTYPE_DECIMAL**、 **DBTYPE_NUMERIC**、 **DBTYPE_VARNUMERIC**です。 これは、それ以外の場合、 **NULL**です。|  
|**DATETIME_PRECISION**|**DBTYPE_UI4**||サポートされていません。|  
|**CHARACTER_SET_CATALOG**|**DBTYPE_WSTR**||サポートされていません。|  
|**CHARACTER_SET_SCHEMA**|**DBTYPE_WSTR**||サポートされていません。|  
|**CHARACTER_SET_NAME**|**DBTYPE_WSTR**||サポートされていません。|  
|**COLLATION_CATALOG**|**DBTYPE_WSTR**||サポートされていません。|  
|**COLLATION_SCHEMA**|**DBTYPE_WSTR**||サポートされていません。|  
|**COLLATION_NAME**|**DBTYPE_WSTR**||サポートされていません。|  
|**DOMAIN_CATALOG**|**DBTYPE_WSTR**||サポートされていません。|  
|**DOMAIN_SCHEMA**|**DBTYPE_WSTR**||サポートされていません。|  
|**ドメイン名**|**DBTYPE_WSTR**||サポートされていません。|  
|**DESCRIPTION**|**DBTYPE_WSTR**||サポートされていません。|  
|**COLUMN_OLAP_TYPE**|**DBTYPE_WSTR**||オブジェクトの OLAP 型。<br /><br /> **メジャー**オブジェクトがメジャーであることを示します。<br /><br /> **属性**オブジェクトが、ディメンション属性であることを示します。<br /><br /> **スキーマ**オブジェクトがスキーマ内の列であることを示します。|  
  
 行セットが並べ替えられて**TABLE_CATALOG**、 **、table_schema、**、 **TABLE_NAME**です。  
  
## <a name="restriction-columns"></a>制限の列  
 **DBSCHEMA_COLUMNS**行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|**TABLE_CATALOG**|**DBTYPE_WSTR**|省略可|  
|**TABLE_SCHEMA**|**DBTYPE_WSTR**|省略可|  
|**TABLE_NAME**|**DBTYPE_WSTR**|省略可|  
|**COLUMN_NAME**|**DBTYPE_WSTR**|省略可|  
|**COLUMN_OLAP_TYPE**|**DBTYPE_WSTR**|省略可|  
  
## <a name="see-also"></a>参照  
 [OLE DB スキーマ行セット](../../../analysis-services/schema-rowsets/ole-db/ole-db-schema-rowsets.md)  
  
  

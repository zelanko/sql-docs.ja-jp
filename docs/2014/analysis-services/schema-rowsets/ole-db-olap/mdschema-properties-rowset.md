---
title: MDSCHEMA_PROPERTIES 行セット |Microsoft ドキュメント
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
- MDSCHEMA_PROPERTIES
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_PROPERTIES rowset
ms.assetid: 95c480f7-c525-44ba-a59b-cd36f5855a4f
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 7c0e0506be8f531018285bba9145a587448e743e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36074267"
---
# <a name="mdschemaproperties-rowset"></a>MDSCHEMA_PROPERTIES 行セット
  データベース内のメンバーのプロパティについて記述します。  
  
## <a name="rowset-columns"></a>行セットの列  
 `MDSCHEMA_PROPERTIES`行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|説明|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||データベースの名前。|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||このプロパティが所属するスキーマの名前。 プロバイダーでスキーマがサポートされていない場合は `NULL` になります。|  
|`CUBE_NAME`|`DBTYPE_WSTR`||キューブの名前。|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`||ディメンションの一意の名前。 修飾によって一意な名前を生成するプロバイダーの場合、この名前の各コンポーネントは区切り記号付きです。|  
|`HIERARCHY_UNIQUE_NAME`|`DBTYPE_WSTR`||階層の一意な名前。 修飾によって一意な名前を生成するプロバイダーの場合、この名前の各コンポーネントは区切り記号付きです。|  
|`LEVEL_UNIQUE_NAME`|`DBTYPE_WSTR`||このプロパティが所属するレベルの一意の名前。 プロバイダーで名前付きレベルがサポートされていない場合は、このフィールドに対して `DIMENSION_UNIQUE_NAME` 値が返されます。 修飾によって一意な名前を生成するプロバイダーの場合、この名前の各コンポーネントは区切り記号付きです。|  
|`MEMBER_UNIQUE_NAME`|`DBTYPE_WSTR`||このプロパティが所属するメンバーの一意の名前。 名前付きレベルをサポートしないデータ ストアや、プロパティがメンバー単位であるデータ ストアに対して使用されます。 プロパティがレベル内のすべてのメンバーに適用される場合、この列は `NULL` になります。 修飾によって一意な名前を生成するプロバイダーの場合、この名前の各コンポーネントは区切り記号付きです。|  
|`PROPERTY_TYPE`|`DBTYPE_I2`||プロパティの種類を指定するビットマップ。<br /><br /> -   `MDPROP_MEMBER` (`1`) メンバーのプロパティを識別します。 このプロパティは、SELECT ステートメントの DIMENSION PROPERTIES 句で使用できます。<br />-   `MDPROP_CELL` (`2`) セルのプロパティを識別します。 このプロパティは、SELECT ステートメントの最後にある CELL PROPERTIES 句で使用できます。<br />-   `MDPROP_SYSTEM` (`4`) 内部プロパティを識別します。<br />-   `MDPROP_BLOB` (`8`) をバイナリ ラージ オブジェクト (blob) を格納するプロパティを識別します。|  
|`PROPERTY_NAME`|`DBTYPE_WSTR`||プロパティの名前。 プロパティのキーがプロパティの名前と同じである場合、`PROPERTY_NAME` は空白になります。|  
|`PROPERTY_CAPTION`|`DBTYPE_WSTR`||プロパティに関連付けられ、主に表示目的に使用されるラベルまたはキャプション。 キャプションが存在しない場合は、`PROPERTY_NAME` を返します。|  
|`DATA_TYPE`|`DBTYPE_UI2`||プロパティのデータ型。|  
|`CHARACTER_MAXIMUM_LENGTH`|`DBTYPE_UI4`||プロパティのデータ型が文字、バイナリ、またはビットである場合は、プロパティで可能な最大の長さになります。<br /><br /> ゼロは、最大の長さが定義されていないことを意味します。<br /><br /> 他のすべてのデータ型である場合は、`NULL` を返します。|  
|`CHARACTER_OCTET_LENGTH`|`DBTYPE_UI4`||プロパティのデータ型が文字またはバイナリである場合は、プロパティで可能な最大の長さをバイト単位で表したものになります。<br /><br /> ゼロは、最大の長さが定義されていないことを意味します。<br /><br /> 他のすべてのデータ型である場合は、`NULL` を返します。|  
|`NUMERIC_PRECISION`|`DBTYPE_UI2`||プロパティのデータ型が数値である場合は、プロパティの最大有効桁数になります。<br /><br /> 他のすべてのデータ型である場合は、`NULL` を返します。|  
|`NUMERIC_SCALE`|`DBTYPE_I2`||データ型が `DBTYPE_NUMERIC` または `DBTYPE_DECIMAL` である場合は、小数点以下の桁数になります。<br /><br /> 他のすべてのデータ型である場合は、`NULL` を返します。|  
|`DESCRIPTION`|`DBTYPE_WSTR`||人が判読できる、プロパティについての説明。 説明が存在しない場合は `NULL` になります。|  
|`PROPERTY_CONTENT_TYPE`|`DBTYPE_I2`||プロパティの型。 次のいずれかの列挙になります。<br /><br /> -   **MD_PROPTYPE_REGULAR** (`0x00`)<br />-   **MD_PROPTYPE_ID** (`0x01`)<br />-   **MD_PROPTYPE_RELATION_TO_PARENT** (`0x02`)<br />-   **MD_PROPTYPE_ROLLUP_OPERATOR** (`0x03`)<br />-   **MD_PROPTYPE_ORG_TITLE** (`0x11`)<br />-   **MD_PROPTYPE_CAPTION** (`0x21`)<br />-   **MD_PROPTYPE_CAPTION_SHORT** (`0x22`)<br />-   **MD_PROPTYPE_CAPTION_DESCRIPTION** (`0x23`)<br />-   **MD_PROPTYPE_CAPTION_ABREVIATION** (`0x24`)<br />-   **MD_PROPTYPE_WEB_URL** (`0x31`)<br />-   **MD_PROPTYPE_WEB_HTML** (`0x32`)<br />-   **MD_PROPTYPE_WEB_XML_OR_XSL** (`0x33`)<br />-   **MD_PROPTYPE_WEB_MAIL_ALIAS** (`0x34`)<br />-   **MD_PROPTYPE_ADDRESS** (`0x41`)<br />-   **MD_PROPTYPE_ADDRESS_STREET** (`0x42`)<br />-   **MD_PROPTYPE_ADDRESS_HOUSE** (`0x43`)<br />-   **MD_PROPTYPE_ADDRESS_CITY** (`0x44`)<br />-   **MD_PROPTYPE_ADDRESS_STATE_OR_PROVINCE** (`0x45`)<br />-   **MD_PROPTYPE_ADDRESS_ZIP** (`0x46`)<br />-   **MD_PROPTYPE_ADDRESS_QUARTER** (`0x47`)<br />-   **MD_PROPTYPE_ADDRESS_COUNTRY** (`0x48`)<br />-   **MD_PROPTYPE_ADDRESS_BUILDING** (`0x49`)<br />-   **MD_PROPTYPE_ADDRESS_ROOM** (`0x4A`)<br />-   **MD_PROPTYPE_ADDRESS_FLOOR** (`0x4B`)<br />-   **MD_PROPTYPE_ADDRESS_FAX** (`0x4C`)<br />-   **MD_PROPTYPE_ADDRESS_PHONE** (`0x4D`)<br />-   **MD_PROPTYPE_GEO_CENTROID_X** (`0x61`)<br />-   **MD_PROPTYPE_GEO_CENTROID_Y** (`0x62`)<br />-   **MD_PROPTYPE_GEO_CENTROID_Z** (`0x63`)<br />-   **MD_PROPTYPE_GEO_BOUNDARY_TOP** (`0x64`)<br />-   **MD_PROPTYPE_GEO_BOUNDARY_LEFT** (`0x65`)<br />-   **MD_PROPTYPE_GEO_BOUNDARY_BOTTOM** (`0x66`)<br />-   **MD_PROPTYPE_GEO_BOUNDARY_RIGHT** (`0x67`)<br />-   **MD_PROPTYPE_GEO_BOUNDARY_FRONT** (`0x68`)<br />-   **MD_PROPTYPE_GEO_BOUNDARY_REAR** (`0x69`)<br />-   **MD_PROPTYPE_GEO_BOUNDARY_POLYGON** (`0x6A`)<br />-   **MD_PROPTYPE_PHYSICAL_SIZE** (`0x71`)<br />-   **MD_PROPTYPE_PHYSICAL_COLOR** (`0x72`)<br />-   **MD_PROPTYPE_PHYSICAL_WEIGHT** (`0x73`)<br />-   **MD_PROPTYPE_PHYSICAL_HEIGHT** (`0x74`)<br />-   **MD_PROPTYPE_PHYSICAL_WIDTH** (`0x75`)<br />-   **MD_PROPTYPE_PHYSICAL_DEPTH** (`0x76`)<br />-   **MD_PROPTYPE_PHYSICAL_VOLUME** (`0x77`)<br />-   **MD_PROPTYPE_PHYSICAL_DENSITY** (`0x78`)<br />-   **MD_PROPTYPE_PERSON_FULL_NAME** (`0x82`)<br />-   **MD_PROPTYPE_PERSON_FIRST_NAME** (`0x83`)<br />-   **MD_PROPTYPE_PERSON_LAST_NAME** (`0x84`)<br />-   **MD_PROPTYPE_PERSON_MIDDLE_NAME** (`0x85`)<br />-   **MD_PROPTYPE_PERSON_DEMOGRAPHIC** (`0x86`)<br />-   **MD_PROPTYPE_PERSON_CONTACT** (`0x87`)<br />-   **MD_PROPTYPE_QTY_RANGE_LOW** (`0x91`)<br />-   **MD_PROPTYPE_QTY_RANGE_HIGH** (`0x92`)<br />-   **MD_PROPTYPE_FORMATTING_COLOR** (`0xA1`)<br />-   **MD_PROPTYPE_FORMATTING_ORDER** (`0xA2`)<br />-   **MD_PROPTYPE_FORMATTING_FONT** (`0xA3`)<br />-   **MD_PROPTYPE_FORMATTING_FONT_EFFECTS** (`0xA4`)<br />-   **MD_PROPTYPE_FORMATTING_FONT_SIZE** (`0xA5`)<br />-   **MD_PROPTYPE_FORMATTING_SUB_TOTAL** (`0xA6`)<br />-   **MD_PROPTYPE_DATE** (`0xB1`)<br />-   **MD_PROPTYPE_DATE_START** (`0xB2`)<br />-   **MD_PROPTYPE_DATE_ENDED** (`0xB3`)<br />-   **MD_PROPTYPE_DATE_CANCELED** (`0xB4`)<br />-   **MD_PROPTYPE_DATE_MODIFIED** (`0xB5`)<br />-   **MD_PROPTYPE_DATE_DURATION** (`0xB6`)<br />-   **MD_PROPTYPE_VERSION** (`0xC1`)|  
|`SQL_COLUMN_NAME`|`DBTYPE_WSTR`||キューブ ディメンションまたはデータベース ディメンションからの SQL クエリで使用されるプロパティの名前。|  
|`LANGUAGE`|`DBTYPE_UI2`||`LCID` として表される翻訳。 プロパティの翻訳に対してのみ有効です。|  
|`PROPERTY_ORIGIN`|`DBTYPE_UI2`||プロパティが適用される階層の種類を識別します。<br /><br /> -   `MD_USER_DEFINED` (`1`) プロパティは、ユーザー定義階層を示します<br />-   `MD_SYSTEM_ENABLED` (`2`) プロパティは、属性階層を示します<br />-   `MD_SYSTEM_DISABLED` (`4`) プロパティは、属性階層が有効になっていないことを示します。|  
|`PROPERTY_ATTRIBUTE_HIERARCHY_NAME`|`DBTYPE_WSTR`||このプロパティの基になる属性階層の名前。|  
|`PROPERTY_CARDINALITY`|`DBTYPE_WSTR`||プロパティのカーディナリティ。 次のいずれかの文字列になります。<br /><br /> -   `ONE`<br />-   `MANY`|  
|`MIME_TYPE`|`DBTYPE_WSTR`||バイナリ ラージ オブジェクト (BLOB) の MIME の種類。|  
|`PROPERTY_IS_VISIBLE`|`DBTYPE_BOOL`||プロパティが表示されるかどうかを示すブール値。<br /><br /> プロパティが表示される場合は `TRUE`、表示されない場合は `FALSE` になります。|  
  
 このスキーマ行セットは並べ替えられません。  
  
## <a name="restriction-columns"></a>制限の列  
 `MDSCHEMA_PROPERTIES`行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|必須|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|省略可|  
|`CUBE_NAME`|`DBTYPE_WSTR`|省略可|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`|省略可|  
|`HIERARCHY_UNIQUE_NAME`|`DBTYPE_WSTR`|省略可|  
|`LEVEL_UNIQUE_NAME`|`DBTYPE_WSTR`|省略可|  
|`MEMBER_UNIQUE_NAME`|`DBTYPE_WSTR`|省略可|  
|`PROPERTY_TYPE`|`DBTYPE_I2`|省略可|  
|`PROPERTY_NAME`|`DBTYPE_WSTR`|省略可|  
|`PROPERTY_CONTENT_TYPE`|`DBTYPE_I2`|(省略可) 既定の制限は、`MDPROP_MEMBER` または `MDPROP_CELL` に適用されます。|  
|`PROPERTY_ORIGIN`|`DBTYPE_UI2`|(省略可) 既定の制限は、`MD_USER_DEFINED` または `MD_SYSTEM_ENABLED` に適用されます。|  
|`CUBE_SOURCE`|`DBTYPE_UI2`|(省略可) 次のいずれかの有効値を含むビットマップ。<br /><br /> -1 のキューブ<br />2 つのディメンション<br /><br /> 既定の制限の値は 1 です。|  
|`PROPERTY_VISIBILITY`|`DBTYPE_UI2`|(省略可) 次のいずれかの有効値を含むビットマップ。<br /><br /> -1 の表示<br />-2 not 表示<br /><br /> 既定の制限の値は 1 です。|  
  
## <a name="see-also"></a>参照  
 [OLE DB for OLAP Schema 行セット](ole-db-for-olap-schema-rowsets.md)  
  
  
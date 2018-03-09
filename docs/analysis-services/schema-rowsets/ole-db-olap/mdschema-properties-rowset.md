---
title: "MDSCHEMA_PROPERTIES 行セット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: MDSCHEMA_PROPERTIES
apitype: NA
applies_to: SQL Server 2016 Preview
helpviewer_keywords: MDSCHEMA_PROPERTIES rowset
ms.assetid: 95c480f7-c525-44ba-a59b-cd36f5855a4f
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 43ec669b0b72775645f12ff51d0e4ede962b7700
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="mdschemaproperties-rowset"></a>MDSCHEMA_PROPERTIES 行セット
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]データベース内のメンバーのプロパティについて説明します。  
  
## <a name="rowset-columns"></a>行セットの列  
 **MDSCHEMA_PROPERTIES**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|Description|  
|-----------------|--------------------|------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**||データベースの名前。|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**||このプロパティが所属するスキーマの名前。 **NULL**プロバイダーがスキーマをサポートしていない場合。|  
|**CUBE_NAME**|**DBTYPE_WSTR**||キューブの名前。|  
|**DIMENSION_UNIQUE_NAME**|**DBTYPE_WSTR**||ディメンションの一意の名前。 修飾によって一意な名前を生成するプロバイダーの場合、この名前の各コンポーネントは区切り記号付きです。|  
|**HIERARCHY_UNIQUE_NAME**|**DBTYPE_WSTR**||階層の一意な名前。 修飾によって一意な名前を生成するプロバイダーの場合、この名前の各コンポーネントは区切り記号付きです。|  
|**LEVEL_UNIQUE_NAME**|**DBTYPE_WSTR**||このプロパティが所属するレベルの一意の名前。 かどうか、プロバイダーによってサポートされない名前付きレベルが返されます、 **DIMENSION_UNIQUE_NAME**このフィールドの値。 修飾によって一意な名前を生成するプロバイダーの場合、この名前の各コンポーネントは区切り記号付きです。|  
|**MEMBER_UNIQUE_NAME**|**DBTYPE_WSTR**||このプロパティが所属するメンバーの一意の名前。 名前付きレベルをサポートしないデータ ストアや、プロパティがメンバー単位であるデータ ストアに対して使用されます。 この列は、このプロパティは、レベル内のすべてのメンバーに適用する場合**NULL**です。 修飾によって一意な名前を生成するプロバイダーの場合、この名前の各コンポーネントは区切り記号付きです。|  
|**PROPERTY_TYPE**|**DBTYPE_I2**||プロパティの種類を指定するビットマップ。<br /><br /> **MDPROP_MEMBER** (**1**) メンバーのプロパティを識別します。 このプロパティは、SELECT ステートメントの DIMENSION PROPERTIES 句で使用できます。<br /><br /> **MDPROP_CELL** (**2**) セルのプロパティを識別します。 このプロパティは、SELECT ステートメントの最後にある CELL PROPERTIES 句で使用できます。<br /><br /> **MDPROP_SYSTEM** (**4**) 内部プロパティを識別します。<br /><br /> **MDPROP_BLOB** (**8**) をバイナリ ラージ オブジェクト (blob) を格納するプロパティを識別します。|  
|**PROPERTY_NAME**|**DBTYPE_WSTR**||プロパティの名前。 プロパティのキーは、プロパティの名前と同じ場合**PROPERTY_NAME**は空白になります。|  
|**PROPERTY_CAPTION**|**DBTYPE_WSTR**||プロパティに関連付けられ、主に表示目的に使用されるラベルまたはキャプション。 返します**PROPERTY_NAME**キャプションが存在しない場合。|  
|**DATA_TYPE**|**DBTYPE_UI2**||プロパティのデータ型。|  
|**CHARACTER_MAXIMUM_LENGTH**|**DBTYPE_UI4**||プロパティのデータ型が文字、バイナリ、またはビットである場合は、プロパティで可能な最大の長さになります。<br /><br /> ゼロは、最大の長さが定義されていないことを意味します。<br /><br /> 返します**NULL**他のすべてのデータ型。|  
|**CHARACTER_OCTET_LENGTH**|**DBTYPE_UI4**||プロパティのデータ型が文字またはバイナリである場合は、プロパティで可能な最大の長さをバイト単位で表したものになります。<br /><br /> ゼロは、最大の長さが定義されていないことを意味します。<br /><br /> 返します**NULL**他のすべてのデータ型。|  
|**NUMERIC_PRECISION**|**DBTYPE_UI2**||プロパティのデータ型が数値である場合は、プロパティの最大有効桁数になります。<br /><br /> 返します**NULL**他のすべてのデータ型。|  
|**NUMERIC_SCALE**|**DBTYPE_I2**||ある場合、小数点の位置の右側にある数字の数、 **DBTYPE_NUMERIC**または**DBTYPE_DECIMAL**型です。<br /><br /> 返します**NULL**他のすべてのデータ型。|  
|**DESCRIPTION**|**DBTYPE_WSTR**||人が判読できる、プロパティについての説明。 **NULL**説明が存在しない場合。|  
|**PROPERTY_CONTENT_TYPE**|**DBTYPE_I2**||プロパティの型。 次のいずれかの列挙になります。<br /><br /> **MD_PROPTYPE_REGULAR** (**0x00**)<br /><br /> **MD_PROPTYPE_ID** (**0x01**)<br /><br /> **MD_PROPTYPE_RELATION_TO_PARENT** (**0x02**)<br /><br /> **MD_PROPTYPE_ROLLUP_OPERATOR** (**0x03**)<br /><br /> **MD_PROPTYPE_ORG_TITLE** (**パターン**)<br /><br /> **MD_PROPTYPE_CAPTION** (**0x21**)<br /><br /> **MD_PROPTYPE_CAPTION_SHORT** (**0x22**)<br /><br /> **MD_PROPTYPE_CAPTION_DESCRIPTION** (**0x23**)<br /><br /> **MD_PROPTYPE_CAPTION_ABREVIATION** (**0x24**)<br /><br /> **MD_PROPTYPE_WEB_URL** (**0x31**)<br /><br /> **MD_PROPTYPE_WEB_HTML** (**0x32**)<br /><br /> **MD_PROPTYPE_WEB_XML_OR_XSL** (**0x33**)<br /><br /> **MD_PROPTYPE_WEB_MAIL_ALIAS** (**0x34**)<br /><br /> **MD_PROPTYPE_ADDRESS** (**0x41**)<br /><br /> **MD_PROPTYPE_ADDRESS_STREET** (**0x42**)<br /><br /> **MD_PROPTYPE_ADDRESS_HOUSE** (**示します**)<br /><br /> **MD_PROPTYPE_ADDRESS_CITY** (**0x44**)<br /><br /> **MD_PROPTYPE_ADDRESS_STATE_OR_PROVINCE** (**0x45**)<br /><br /> **MD_PROPTYPE_ADDRESS_ZIP** (**0x46**)<br /><br /> **MD_PROPTYPE_ADDRESS_QUARTER** (**0x47**)<br /><br /> **MD_PROPTYPE_ADDRESS_COUNTRY** (**0x48**)<br /><br /> **MD_PROPTYPE_ADDRESS_BUILDING** (**0x49**)<br /><br /> **MD_PROPTYPE_ADDRESS_ROOM** (**0x4A**)<br /><br /> **MD_PROPTYPE_ADDRESS_FLOOR** (**0x4B**)<br /><br /> **MD_PROPTYPE_ADDRESS_FAX** (**0x4C**)<br /><br /> **MD_PROPTYPE_ADDRESS_PHONE** (**0x4D**)<br /><br /> **MD_PROPTYPE_GEO_CENTROID_X** (**0x61**)<br /><br /> **MD_PROPTYPE_GEO_CENTROID_Y** (**0x62**)<br /><br /> **MD_PROPTYPE_GEO_CENTROID_Z** (**など**)<br /><br /> **MD_PROPTYPE_GEO_BOUNDARY_TOP** (**0x64**)<br /><br /> **MD_PROPTYPE_GEO_BOUNDARY_LEFT** (**0x65**)<br /><br /> **MD_PROPTYPE_GEO_BOUNDARY_BOTTOM** (**0x66**)<br /><br /> **MD_PROPTYPE_GEO_BOUNDARY_RIGHT** (**0x67**)<br /><br /> **MD_PROPTYPE_GEO_BOUNDARY_FRONT** (**0x68**)<br /><br /> **MD_PROPTYPE_GEO_BOUNDARY_REAR** (**0x69**)<br /><br /> **MD_PROPTYPE_GEO_BOUNDARY_POLYGON** (**0x6A**)<br /><br /> **MD_PROPTYPE_PHYSICAL_SIZE** (**0x71**)<br /><br /> **MD_PROPTYPE_PHYSICAL_COLOR** (**0x72**)<br /><br /> **MD_PROPTYPE_PHYSICAL_WEIGHT** (**0x73**)<br /><br /> **MD_PROPTYPE_PHYSICAL_HEIGHT** (**0x74**)<br /><br /> **MD_PROPTYPE_PHYSICAL_WIDTH** (**0x75**)<br /><br /> **MD_PROPTYPE_PHYSICAL_DEPTH** (**0x76**)<br /><br /> **MD_PROPTYPE_PHYSICAL_VOLUME** (**0x77**)<br /><br /> **MD_PROPTYPE_PHYSICAL_DENSITY** (**0x78**)<br /><br /> **MD_PROPTYPE_PERSON_FULL_NAME** (**0x82**)<br /><br /> **MD_PROPTYPE_PERSON_FIRST_NAME** (**0x83**)<br /><br /> **MD_PROPTYPE_PERSON_LAST_NAME** (**0x84**)<br /><br /> **MD_PROPTYPE_PERSON_MIDDLE_NAME** (**0x85**)<br /><br /> **MD_PROPTYPE_PERSON_DEMOGRAPHIC** (**0x86**)<br /><br /> **MD_PROPTYPE_PERSON_CONTACT** (**0x87**)<br /><br /> **MD_PROPTYPE_QTY_RANGE_LOW** (**0x91**)<br /><br /> **MD_PROPTYPE_QTY_RANGE_HIGH** (**0x92**)<br /><br /> **MD_PROPTYPE_FORMATTING_COLOR** (**0xA1**)<br /><br /> **MD_PROPTYPE_FORMATTING_ORDER** (**0xA2**)<br /><br /> **MD_PROPTYPE_FORMATTING_FONT** (**0xA3**)<br /><br /> **MD_PROPTYPE_FORMATTING_FONT_EFFECTS** (**0xA4**)<br /><br /> **MD_PROPTYPE_FORMATTING_FONT_SIZE** (**0xA5**)<br /><br /> **MD_PROPTYPE_FORMATTING_SUB_TOTAL** (**0xA6**)<br /><br /> **MD_PROPTYPE_DATE** (**0xB1**)<br /><br /> **MD_PROPTYPE_DATE_START** (**0xB2**)<br /><br /> **MD_PROPTYPE_DATE_ENDED** (**0xB3**)<br /><br /> **MD_PROPTYPE_DATE_CANCELED** (**繰り返し、0xB4**)<br /><br /> **MD_PROPTYPE_DATE_MODIFIED** (**0xB5**)<br /><br /> **MD_PROPTYPE_DATE_DURATION** (**0xB6**)<br /><br /> **MD_PROPTYPE_VERSION** (**0xC1**)|  
|**SQL_COLUMN_NAME**|**DBTYPE_WSTR**||キューブ ディメンションまたはデータベース ディメンションからの SQL クエリで使用されるプロパティの名前。|  
|**LANGUAGE**|**DBTYPE_UI2**||として表される、翻訳、 **LCID**です。 プロパティの翻訳に対してのみ有効です。|  
|**PROPERTY_ORIGIN**|**DBTYPE_UI2**||プロパティが適用される階層の種類を識別します。<br /><br /> **MD_USER_DEFINED** (**1**) プロパティは、ユーザー定義階層を示します<br /><br /> **MD_SYSTEM_ENABLED** (**2**) プロパティは、属性階層を示します<br /><br /> **MD_SYSTEM_DISABLED** (**4**) プロパティは、属性階層が有効になっていないことを示します。|  
|**PROPERTY_ATTRIBUTE_HIERARCHY_NAME**|**DBTYPE_WSTR**||このプロパティの基になる属性階層の名前。|  
|**PROPERTY_CARDINALITY**|**DBTYPE_WSTR**||プロパティの基数。 次のいずれかの文字列になります。<br /><br /> **1 つ**<br /><br /> **多く**|  
|**MIME_TYPE**|**DBTYPE_WSTR**||バイナリ ラージ オブジェクト (BLOB) の MIME の種類。|  
|**PROPERTY_IS_VISIBLE**|**DBTYPE_BOOL**||プロパティが表示されるかどうかを示すブール値。<br /><br /> **TRUE**プロパティが表示されている、それ以外の場合**FALSE**です。|  
  
 このスキーマ行セットは並べ替えられません。  
  
## <a name="restriction-columns"></a>制限の列  
 **MDSCHEMA_PROPERTIES**行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|必須|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|省略可|  
|**CUBE_NAME**|**DBTYPE_WSTR**|省略可|  
|**DIMENSION_UNIQUE_NAME**|**DBTYPE_WSTR**|省略可|  
|**HIERARCHY_UNIQUE_NAME**|**DBTYPE_WSTR**|省略可|  
|**LEVEL_UNIQUE_NAME**|**DBTYPE_WSTR**|省略可|  
|**MEMBER_UNIQUE_NAME**|**DBTYPE_WSTR**|省略可|  
|**PROPERTY_TYPE**|**DBTYPE_I2**|省略可|  
|**PROPERTY_NAME**|**DBTYPE_WSTR**|省略可|  
|**PROPERTY_CONTENT_TYPE**|**DBTYPE_I2**|(省略可能)既定の制限されている**MDPROP_MEMBER**または**MDPROP_CELL**です。|  
|**PROPERTY_ORIGIN**|**DBTYPE_UI2**|(省略可能)既定の制限されている**、MD_USER_DEFINED**または**MD_SYSTEM_ENABLED**です。|  
|**CUBE_SOURCE**|**DBTYPE_UI2**|(省略可能)既定の制限は、1 の値です。  有効な値は次のいずれかのビットマップ。<br /><br /> 1 キューブ<br /><br /> 2 ディメンション|  
|**PROPERTY_VISIBILITY**|**DBTYPE_UI2**|(省略可能)既定の制限は、1 の値です。 有効な値は次のいずれかのビットマップ。<br /><br /> 1 表示<br /><br /> 2 not 表示|  
  
## <a name="see-also"></a>参照  
 [OLE DB for OLAP Schema 行セット](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  

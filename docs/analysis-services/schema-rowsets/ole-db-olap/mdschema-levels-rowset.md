---
title: "MDSCHEMA_LEVELS 行セット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: schema-rowsets
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- MDSCHEMA_LEVELS
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- MDSCHEMA_LEVELS rowset
ms.assetid: 4313e268-33f4-4e99-96d7-2ec26775c580
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 8d9a56387365489615b6b7665dedb3edc7f367f6
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="mdschemalevels-rowset"></a>MDSCHEMA_LEVELS 行セット
  特定の階層内の各レベルについて記述します。  
  
## <a name="rowset-columns"></a>行セットの列  
 **MDSCHEMA_LEVELS**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|Description|  
|-----------------|--------------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|このレベルが所属するカタログの名前。 **NULL**プロバイダーがカタログをサポートしていない場合。|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|このレベルが所属するスキーマの名前。 **NULL**プロバイダーがスキーマをサポートしていない場合。|  
|**CUBE_NAME**|**DBTYPE_WSTR**|このレベルが所属するキューブの名前。|  
|**DIMENSION_UNIQUE_NAME**|**DBTYPE_WSTR**|このレベルが所属するディメンションの一意の名前。 修飾によって一意な名前を生成するプロバイダーの場合、この名前の各コンポーネントは区切り記号付きです。|  
|**HIERARCHY_UNIQUE_NAME**|**DBTYPE_WSTR**|階層の一意な名前。 レベルが複数の階層に所属している場合は、そのメンバーが所属する階層ごとに対応する行があります。 修飾によって一意な名前を生成するプロバイダーの場合、この名前の各コンポーネントは区切り記号付きです。|  
|**LEVEL_NAME**|**DBTYPE_WSTR**|レベルの名前です。|  
|**LEVEL_UNIQUE_NAME**|**DBTYPE_WSTR**|適切にエスケープされたレベルの一意の名前。|  
|**LEVEL_GUID**|**DBTYPE_GUID 型**|サポートされていません。|  
|**LEVEL_CAPTION**|**DBTYPE_WSTR**|階層に関連付けられたラベルまたはキャプション。 主に表示のために使用されます。 キャプションが存在しない場合**LEVEL_NAME**が返されます。|  
|**LEVEL_NUMBER**|**DBTYPE_UI4**|階層のルートからレベルまでの距離。 ルート レベルはゼロ (**0)**です。|  
|**LEVEL_CARDINALITY**|**DBTYPE_UI4**|レベル内のメンバーの数。|  
|**LEVEL_TYPE**|**DBTYPE_I4**|レベルの種類。<br /><br /> **MDLEVEL_TYPE_GEO_CONTINENT** (**0x2001**)<br /><br /> **MDLEVEL_TYPE_GEO_REGION** (**0x2002**)<br /><br /> **MDLEVEL_TYPE_GEO_COUNTRY** (**0x2003**)<br /><br /> **MDLEVEL_TYPE_GEO_STATE_OR_PROVINCE** (**0x2004**)<br /><br /> **MDLEVEL_TYPE_GEO_COUNTY** (**0x2005**)<br /><br /> **MDLEVEL_TYPE_GEO_CITY** (**0x2006**)<br /><br /> **MDLEVEL_TYPE_GEO_POSTALCODE** (**0x2007**)<br /><br /> **MDLEVEL_TYPE_GEO_POINT** (**0x2008**)<br /><br /> **MDLEVEL_TYPE_ORG_UNIT** (**0x1011**)<br /><br /> **MDLEVEL_TYPE_BOM_RESOURCE** (**0x1012**)<br /><br /> **MDLEVEL_TYPE_QUANTITATIVE** (**0x1013**)<br /><br /> **MDLEVEL_TYPE_ACCOUNT** (**0x1014**)<br /><br /> **MDLEVEL_TYPE_CUSTOMER** (**0x1021**)<br /><br /> **MDLEVEL_TYPE_CUSTOMER_GROUP** (**0x1022**)<br /><br /> **MDLEVEL_TYPE_CUSTOMER_HOUSEHOLD** (**0x1023**)<br /><br /> **MDLEVEL_TYPE_PRODUCT** (**0x1031**)<br /><br /> **MDLEVEL_TYPE_PRODUCT_GROUP** (**0x1032**)<br /><br /> **MDLEVEL_TYPE_SCENARIO** (**0x1015**)<br /><br /> **MDLEVEL_TYPE_UTILITY** (**0x1016**)<br /><br /> **MDLEVEL_TYPE_PERSON** (**0x1041**)<br /><br /> **MDLEVEL_TYPE_COMPANY** (**0x1042**)<br /><br /> **MDLEVEL_TYPE_CURRENCY_SOURCE** (**0x1051**)<br /><br /> **MDLEVEL_TYPE_CURRENCY_DESTINATION** (**0x1052**)<br /><br /> **MDLEVEL_TYPE_CHANNEL** (**0x1061**)<br /><br /> **MDLEVEL_TYPE_REPRESENTATIVE** (**0x1062**)<br /><br /> **MDLEVEL_TYPE_PROMOTION** (**0x1071**)|  
|**DESCRIPTION**|**DBTYPE_WSTR**|レベルに関して人が認識できる説明。 説明が存在しない場合は NULL になります。|  
|**CUSTOM_ROLLUP_SETTINGS**|**DBTYPE_I4**|カスタム ロールアップ オプションを指定するビットマップ。<br /><br /> **MDLEVELS_CUSTOM_ROLLUP_EXPRESSION** (**0x01**) 式は、このレベルが存在することを示します。 (非推奨)。<br /><br /> **MDLEVELS_CUSTOM_ROLLUP_COLUMN** (**0x02**) このレベルのカスタム ロールアップ列があることを示します。<br /><br /> **MDLEVELS_SKIPPED_LEVELS** (**0x04**) このレベルのメンバーに関連付けられているスキップされたレベルがあることを示します。<br /><br /> **MDLEVELS_CUSTOM_MEMBER_PROPERTIES** (**0x08**) レベルのメンバーは、カスタム メンバー プロパティであることを示します。<br /><br /> **MDLEVELS_UNARY_OPERATOR** (**0x10**) レベルのメンバーに単項演算子があることを示します。|  
|**LEVEL_UNIQUE_SETTINGS**|**DBTYPE_I4**|レベルに一意の名前またはキーを持つメンバーのみが含まれている場合に、一意の値を含んでいる列を示すビットマップ。 Msmd.h ファイルは、このビットマップに対して次のビット値定数を定義します。<br /><br /> **MDDIMENSIONS_MEMBER_KEY_UNIQUE** (**1**)<br /><br /> **MDDIMENSIONS_MEMBER_NAME_UNIQUE** (**2**)<br /><br /> <br /><br /> キーが内で一意では常にことに注意してください[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。 名前が一意で、属性の設定がある場合がある**UniqueInDimension**または**UniqueInAttribute**|  
|**LEVEL_IS_VISIBLE**|**DBTYPE_BOOL**|レベルが表示されるかどうかを示すブール値。<br /><br /> 常に True を返します。 レベルが表示されていない場合は、スキーマ行セットに含まれません。|  
|**LEVEL_ORDERING_PROPERTY**|**DBTYPE_WSTR**|レベルの並べ替えに使用する属性の ID。|  
|**LEVEL_DBTYPE**|**DBTYPE_I4**|**DBTYPE**レベルの属性に使用されるメンバー キー列を列挙します。<br /><br /> 連結されたキーをメンバー キー列として使用する場合は NULL になります。|  
|**LEVEL_MASTER_UNIQUE_NAME**|**DBTYPE_WSTR**|常に NULL が返されます。|  
|**LEVEL_NAME_SQL_COLUMN_NAME**|**DBTYPE_WSTR**|レベル メンバー名の SQL 表現。|  
|**LEVEL_KEY_SQL_COLUMN_NAME**|**DBTYPE_WSTR**|レベル メンバー キー値の SQL 表現。|  
|**LEVEL_UNIQUE_NAME_SQL_COLUMN_NAME**|**DBTYPE_WSTR**|一意のメンバー名の SQL 表現。|  
|**LEVEL_ATTRIBUTE_HIERARCHY_NAME**|**DBTYPE_WSTR**|レベルのソースを提供する属性階層の名前。|  
|**LEVEL_KEY_CARDINALITY**|**DBTYPE_UI2**|レベル キー内の列の数。|  
|**LEVEL_ORIGIN**|**DBTYPE_UI2**|レベルのソースを定義するビットマップ。<br /><br /> **MD_ORIGIN_USER_DEFINED**ユーザー定義階層内のレベルを識別します。<br /><br /> **MD_ORIGIN_ATTRIBUTE**属性階層内のレベルを識別します。<br /><br /> **MD_ORIGIN_KEY_ATTRIBUTE**キー属性階層内のレベルを識別します。<br /><br /> **MD_ORIGIN_INTERNAL**無効になっている属性階層のレベルを識別します。|  
  
 行セットが並べ替えられて**CATALOG_NAME**、 **SCHEMA_NAME**、 **CUBE_NAME**、 **DIMENSION_UNIQUE_NAME**、 **hierarchy _UNIQUE_NAME**、 **LEVEL_NUMBER**です。  
  
## <a name="restriction-columns"></a>制限の列  
 **MDSCHEMA_LEVELS**行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|省略可。|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|省略可。|  
|**CUBE_NAME**|**DBTYPE_WSTR**|省略可。|  
|**DIMENSION_UNIQUE_NAME**|**DBTYPE_WSTR**|省略可。|  
|**HIERARCHY_UNIQUE_NAME**|**DBTYPE_WSTR**|省略可。|  
|**LEVEL_NAME**|**DBTYPE_WSTR**|省略可。|  
|**LEVEL_UNIQUE_NAME**|**DBTYPE_WSTR**|省略可。|  
|**LEVEL_ORIGIN**|**DBTYPE_UI2**|(省略可能)既定の制限はでは有効に**、MD_USER_DEFINED**と**MD_SYSTEM_ENABLED**|  
|**CUBE_SOURCE**|**DBTYPE_UI2**|(省略可能)既定の制限は、1 の値です。 有効な値は次のいずれかのビットマップ。<br /><br /> 1 キューブ<br /><br /> 2 ディメンション|  
|**LEVEL_VISIBILITY**|**DBTYPE_UI2**|(省略可能)既定の制限は、1 の値です。 次の値のいずれかのビットマップ。<br /><br /> 1 表示<br /><br /> 2 not 表示|  
  
## <a name="see-also"></a>参照  
 [OLE DB for OLAP スキーマ行セット](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  


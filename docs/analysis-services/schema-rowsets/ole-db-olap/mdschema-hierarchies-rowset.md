---
title: MDSCHEMA_HIERARCHIES 行セット |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7b2be443b6059a3def3197448ef75bf89586e156
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34036533"
---
# <a name="mdschemahierarchies-rowset"></a>MDSCHEMA_HIERARCHIES 行セット
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  特定のディメンション内の各階層について記述します。  
  
## <a name="rowset-columns"></a>行セットの列  
 **MDSCHEMA_HIERARCHIES**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|Description|  
|-----------------|--------------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|この階層が所属するカタログの名前。 **NULL**プロバイダーがカタログをサポートしていない場合。|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|サポートされていません|  
|**CUBE_NAME**|**DBTYPE_WSTR**|(必須) この階層が所属するキューブの名前。|  
|**DIMENSION_UNIQUE_NAME**|**DBTYPE_WSTR**|この階層が所属するディメンションの一意の名前。 修飾によって一意な名前を生成するプロバイダーの場合、この名前の各コンポーネントは区切り記号付きです。|  
|**HIERARCHY_NAME**|**DBTYPE_WSTR**|階層の名前です。 ディメンションに階層が 1 つしかない場合は空白です。 これが常に値[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。|  
|**HIERARCHY_UNIQUE_NAME**|**DBTYPE_WSTR**|階層の一意な名前。|  
|**HIERARCHY_GUID**|**DBTYPE_GUID 型**|サポートされていません|  
|**HIERARCHY_CAPTION**|**DBTYPE_WSTR**|ラベルまたは階層に関連付けられているキャプションです。 主に表示のために使用されます。 キャプションが存在しない場合**HIERARCHY_NAME**が返されます。 ディメンションに階層が含まれていないか、階層が 1 つしかない場合、この列にはディメンションの名前が格納されます。|  
|**DIMENSION_TYPE**|**DBTYPE_I2**|ディメンションの種類。 有効な値には、次の値があります。<br /><br /> **MD_DIMTYPE_UNKNOWN** (**0**)<br /><br /> **MD_DIMTYPE_TIME** (**1**)<br /><br /> **MD_DIMTYPE_MEASURE** (**2**)<br /><br /> **MD_DIMTYPE_OTHER** (**3**)<br /><br /> **MD_DIMTYPE_QUANTITATIVE** (**5**)<br /><br /> **MD_DIMTYPE_ACCOUNTS** (**6**)<br /><br /> **MD_DIMTYPE_CUSTOMERS** (**7**)<br /><br /> **MD_DIMTYPE_PRODUCTS** (**8**)<br /><br /> **MD_DIMTYPE_SCENARIO** (**9**)<br /><br /> **MD_DIMTYPE_UTILIY** (**10**)<br /><br /> **MD_DIMTYPE_CURRENCY** (**11**)<br /><br /> **MD_DIMTYPE_RATES** (**12**)<br /><br /> **MD_DIMTYPE_CHANNEL** (**13**)<br /><br /> **MD_DIMTYPE_PROMOTION** (**14**)<br /><br /> **MD_DIMTYPE_ORGANIZATION** (**15**)<br /><br /> **MD_DIMTYPE_BILL_OF_MATERIALS** (**16**)<br /><br /> **MD_DIMTYPE_GEOGRAPHY** (**17**)|  
|**HIERARCHY_CARDINALITY**|**DBTYPE_UI4**|階層内のメンバーの数。|  
|**DEFAULT_MEMBER**|**DBTYPE_WSTR**|この階層の既定のメンバー。 これは一意の名前です。 すべての階層に既定のメンバーが必要です。|  
|**ALL_MEMBER**|**DBTYPE_WSTR**|ロールアップの最高レベルのメンバー。|  
|**DESCRIPTION**|**DBTYPE_WSTR**|階層に関する人間が判読できる説明。 **NULL**説明が存在しない場合。|  
|**構造体**|**DBTYPE_I2**|階層の構造。 有効な値には、次の値があります。<br /><br /> **MD_STRUCTURE_FULLYBALANCED** (**0**)<br /><br /> **MD_STRUCTURE_RAGGEDBALANCED** (**1**)<br /><br /> **MD_STRUCTURE_UNBALANCED** (**2**)<br /><br /> **MD_STRUCTURE_NETWORK** (**3**)|  
|**IS_VIRTUAL**|**DBTYPE_BOOL**|常に返します**False**です。|  
|**IS_READWRITE**|**DBTYPE_BOOL**|ディメンション列への書き戻しが有効になっているかどうかを示すブール値。<br /><br /> 返します**TRUE**場合、**ディメンションへの書き戻し**この階層を表す列が有効になっています。|  
|**DIMENSION_UNIQUE_SETTINGS**|**DBTYPE_I4**|常に返します**MDDIMENSIONS_MEMBER_KEY_UNIQUE** (**1**)。|  
|**DIMENSION_MASTER_UNIQUE_NAME**|**DBTYPE_WSTR**|常に返します**NULL**です。|  
|**DIMENSION_IS_VISIBLE**|**DBTYPE_BOOL**|常に返します**true**です。 ディメンションが表示されていない場合は、スキーマ行セットに表示されません。|  
|**HIERARCHY_ORDINAL**|**DBTYPE_UI4**|キューブの全階層にわたる階層の序数。|  
|**DIMENSION_IS_SHARED**|**DBTYPE_BOOL**|常に返します**TRUE**です。|  
|**HIERARCHY_IS_VISIBLE**|**DBTYPE_BOOL**|階層が表示されるかどうかを示すブール値。<br /><br /> 返します**TRUE**階層が表示されている、それ以外の場合**FALSE**です。|  
|**HIERARCHY_ORIGIN**|**DBTYPE_UI2**|階層のソースを決定するビット マスク。<br /><br /> **MD_USER_DEFINED**ユーザー定義階層を示しの値を持つ**0x0000001**です。<br /><br /> **MD_SYSTEM_ENABLED**属性階層を示しの値を持つ**0x0000002**です。<br /><br /> **MD_SYSTEM_INTERNAL**属性階層のないと属性を識別し、値を持つ**0x0000004**です。<br /><br /> <br /><br /> 親/子の属性階層は、両方とも **、MD_USER_DEFINED**と**MD_SYSTEM_ENABLED**です。|  
|**HIERARCHY_DISPLAY_FOLDER**|**DBTYPE_WSTR**|ユーザー インターフェイスでの階層の表示に使用するパス。 フォルダー名はセミコロン (;) で区切られます。 入れ子になったフォルダーは円記号で示されます (\\)。|  
|**INSTANCE_SELECTION**|**DBTYPE_UI2**|階層の表示方法に関するクライアント アプリケーションへのヒント。 有効な値には、次の値があります。<br /><br /> **MD_INSTANCE_SELECTION_NONE**<br /><br /> **MD_INSTANCE_SELECTION_DROPDOWN**<br /><br /> **MD_INSTANCE_SELECTION_LIST**<br /><br /> **MD_INSTANCE_SELECTION_FILTEREDLIST**<br /><br /> **MD_INSTANCE_SELECTION_MANDATORYFILTER**|  
|**GROUPING_BEHAVIOR**|**DBTYPE_I2**|この階層のクライアントに期待されるグループ化の動作を指定する列挙。 次の値を指定できます。<br /><br /> **EncourageGrouping** (1)<br /><br /> **DiscourageGrouping** (2)|  
|**STRUCTURE_TYPE**|**DBTYPE_WSTR**|階層の種類を示します。 有効な値には、次の値があります。<br /><br /> **自然です**<br /><br /> **不自然**<br /><br /> **Unknown**|  
  
 行セットが並べ替えられて**CATALOG_NAME**、 **SCHEMA_NAME**、 **CUBE_NAME**、 **DIMENSION_UNIQUE_NAME**、 **hierarchy _名前**です。  
  
## <a name="restriction-columns"></a>制限の列  
 **MDSCHEMA_HIERARCHIES**行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|省略可。|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|省略可。|  
|**CUBE_NAME**|**DBTYPE_WSTR**|省略可。|  
|**DIMENSION_UNIQUE_NAME**|**DBTYPE_WSTR**|省略可。|  
|**HIERARCHY_NAME**|**DBTYPE_WSTR**|省略可。|  
|**HIERARCHY_UNIQUE_NAME**|**DBTYPE_WSTR**|省略可。|  
|**HIERARCHY_ORIGIN**|**DBTYPE_UI2**|(省略可) 既定の制限は、MD_USER_DEFINED と MD_SYSTEM_ENABLED で有効です。|  
|**CUBE_SOURCE**|**DBTYPE_UI2**|(省略可能)既定の制限は、1 の値です。 有効な値は次のいずれかのビットマップ。<br /><br /> 1 キューブ<br /><br /> 2 ディメンション|  
|**HIERARCHY_VISIBILITY**|**DBTYPE_UI2**|(省略可能)既定の制限は、1 の値です。 有効な値は次のいずれかのビットマップ。<br /><br /> 1 表示<br /><br /> 2 not 表示|  
  
## <a name="see-also"></a>参照  
 [OLE DB for OLAP スキーマ行セット](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  

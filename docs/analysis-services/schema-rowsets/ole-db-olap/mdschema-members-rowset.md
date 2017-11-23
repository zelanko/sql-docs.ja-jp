---
title: "MDSCHEMA_MEMBERS 行セット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
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
apiname: MDSCHEMA_MEMBERS
apitype: NA
applies_to: SQL Server 2016 Preview
helpviewer_keywords: MDSCHEMA_MEMBERS rowset
ms.assetid: 0b1aada0-67f8-4ef6-81b2-0100b65e0c2f
caps.latest.revision: "36"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: a5ac98919c5ac10900eb69c9fe7319c6e8b22a75
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="mdschemamembers-rowset"></a>MDSCHEMA_MEMBERS 行セット
  データベース内のメンバーについて記述します。  
  
## <a name="rowset-columns"></a>行セットの列  
 **MDSCHEMA_MEMBERS**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|Description|  
|-----------------|--------------------|------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**||このメンバーが所属するデータベースの名前。|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**||このメンバーが所属するスキーマの名前。|  
|**CUBE_NAME**|**DBTYPE_WSTR**||このメンバーが所属するキューブの名前。|  
|**DIMENSION_UNIQUE_NAME**|**DBTYPE_WSTR**||このメンバーが所属するディメンションの一意な名前。|  
|**HIERARCHY_UNIQUE_NAME**|**DBTYPE_WSTR**||このメンバーが所属する階層の一意の名前。|  
|**LEVEL_UNIQUE_NAME**|**DBTYPE_WSTR**||このメンバーが所属するレベルの一意の名前。|  
|**LEVEL_NUMBER**|**DBTYPE_UI4**||階層のルートからメンバーまでの距離。 ルートのレベルはゼロ (0) です。|  
|**MEMBER_ORDINAL**|**DBTYPE_UI4**||(非推奨)常に返します**0**します。|  
|**MEMBER_NAME**|**DBTYPE_WSTR**||メンバーの名前。|  
|**MEMBER_UNIQUE_NAME**|**DBTYPE_WSTR**||メンバーの一意な名前。|  
|**MEMBER_TYPE**|**DBTYPE_I4**||メンバーの種類:<br /><br /> **MDMEMBER_TYPE_UNKNOWN** (**0**)<br /><br /> **MDMEMBER_TYPE_REGULAR** (**1**)<br /><br /> **MDMEMBER_TYPE_ALL** (**2**)<br /><br /> **MDMEMBER_TYPE_MEASURE** (**3**)<br /><br /> **MDMEMBER_TYPE_FORMULA** (**4**)<br /><br /> <br /><br /> 注意してください。 <br />                    **MDMEMBER_TYPE_FORMULA**よりも優先**MDMEMBER_TYPE_MEASURE**です。 たとえば、メジャー ディメンションに数式 (計算される) メンバーがある場合として記載されている**MDMEMBER_TYPE_FORMULA**です。|  
|**MEMBER_GUID**|**DBTYPE_GUID 型**||メンバーの GUID。 **NULL** GUID が存在しない場合。|  
|**MEMBER_CAPTION**|**DBTYPE_WSTR**||メンバーに関連付けられたラベルまたはキャプション。 主に表示のために使用されます。 キャプションが存在しない場合**MEMBER_NAME**が返されます。|  
|**CHILDREN_CARDINALITY**|**DBTYPE_UI4**||メンバーが持つ子の数。 子の数は推定値の場合があります。したがって、この数値を正確な数として使用しないでください。 プロバイダーは、正確な数に最も近い推定値を返します。|  
|**PARENT_LEVEL**|**DBTYPE_UI4**||階層のルート レベルからメンバーの親までの距離。 ルートのレベルはゼロ (0) です。|  
|**PARENT_UNIQUE_NAME**|**DBTYPE_WSTR**||メンバーの親の一意の名前。 ルート レベルのメンバーに対しては**NULL** を返します。|  
|**PARENT_COUNT**|**DBTYPE_UI4**||このメンバーが持つ親の数。|  
|**DESCRIPTION**|**DBTYPE_WSTR**||この列は常に返します、 **NULL**値。<br /><br /> この列は、下位互換性を維持するためにあります。|  
|**式**|**DBTYPE_WSTR**||メンバーが型の場合は、計算の式**MDMEMBER_TYPE_FORMULA**です。|  
|**MEMBER_KEY**|**DBTYPE_WSTR**||メンバーのキー列の値。 返します**NULL**メンバー複合キーがある場合。|  
|**IS_PLACEHOLDERMEMBER**|**DBTYPE_BOOL**||メンバーがディメンション階層内の空の位置のプレースホルダー メンバーであるかどうかを示すブール値。<br /><br /> 有効である場合にのみ、 **MDX Compatibility**プロパティを 2 に設定されています。|  
|**IS_DATAMEMBER**|**DBTYPE_BOOL**||メンバーがデータ メンバーであるかどうかを示すブール値。<br /><br /> メンバーがデータ メンバーである場合は True を返します。|  
|**スコープ**|**DBTYPE_I4**||メンバーのスコープ。 メンバーは、セッションの計算されるメンバーまたはグローバルの計算されるメンバーです。 列を返します**NULL**計算されないメンバーにします。 この列は、次のいずれかの値になります。<br /><br /> MDMEMBER_SCOPE_GLOBAL=1<br /><br /> MDMEMBER_SCOPE_SESSION=2|  
|**0 個以上の列**|**DBTYPE_UI2**||複数のレベルからメンバーが返される可能性がある場合は、プロパティを返しません。 たとえば、ツリー演算子が**親**と**SELF**非親子階層のメンバー プロパティは返されません。<br /><br /> これは、ツリー演算子が異なるレベルのメンバーを返す可能性のある不規則な階層に適用されます (たとえば、前のレベルにホールが含まれており、メンバーに対する親が要求された場合など)。|  
  
 行セットが並べ替えられて**CATALOG_NAME**、 **SCHEMA_NAME**、 **CUBE_NAME**、 **DIMENSION_UNIQUE_NAME**、 **hierarchy _UNIQUE_NAME**、**される LEVEL_UNIQUE_NAME**、 **LEVEL_NUMBER**、 **MEMBER_ORDINAL**です。  
  
## <a name="restriction-columns"></a>制限の列  
 **MDSCHEMA_MEMBERS**行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|省略可。|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|省略可。|  
|**CUBE_NAME**|**DBTYPE_WSTR**|省略可。|  
|**DIMENSION_UNIQUE_NAME**|**DBTYPE_WSTR**|省略可。|  
|**HIERARCHY_UNIQUE_NAME**|**DBTYPE_WSTR**|省略可。|  
|**LEVEL_UNIQUE_NAME**|**DBTYPE_WSTR**|省略可。|  
|**LEVEL_NUMBER**|**DBTYPE_UI4**|省略可。|  
|**MEMBER_NAME**|**DBTYPE_WSTR**|省略可。|  
|**MEMBER_UNIQUE_NAME**|**DBTYPE_WSTR**|省略可。|  
|**MEMBER_CAPTION**|**DBTYPE_WSTR**|省略可。|  
|**MEMBER_TYPE**|**DBTYPE_I4**|省略可。|  
|**TREE_OP**|**DBTYPE_I4**|(省略可) 1 つのメンバーにのみ適用されます。<br /><br /> **MDTREEOP_ANCESTORS** (**0x20**) すべての先祖を返します。<br /><br /> **MDTREEOP_CHILDREN** (**0x01**) 直接の子のみを返します。<br /><br /> **MDTREEOP_SIBLINGS** (**0x02**) と同じレベルにメンバーを返します。<br /><br /> **MDTREEOP_PARENT** (**0x04**) 直接の親のみを返します。<br /><br /> **MDTREEOP_SELF** (**0x08**) 返される行の一覧でそれ自体を返します。<br /><br /> **MDTREEOP_DESCENDANTS** (**0x10**) すべての子孫を返します。|  
|**CUBE_SOURCE**|**DBTYPE_UI2**|(省略可能)既定の制限は、1 の値です。 有効な値は次のいずれかのビットマップ。<br /><br /> 1 キューブ<br /><br /> 2 ディメンション|  
  
## <a name="see-also"></a>参照  
 [OLE DB for OLAP Schema 行セット](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  

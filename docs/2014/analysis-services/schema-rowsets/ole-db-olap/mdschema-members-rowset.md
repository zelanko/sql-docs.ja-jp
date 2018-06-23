---
title: MDSCHEMA_MEMBERS 行セット |Microsoft ドキュメント
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
- MDSCHEMA_MEMBERS
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_MEMBERS rowset
ms.assetid: 0b1aada0-67f8-4ef6-81b2-0100b65e0c2f
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 2473797ef34c0fd204c878da8c6044a307cc1ee3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36177417"
---
# <a name="mdschemamembers-rowset"></a>MDSCHEMA_MEMBERS 行セット
  データベース内のメンバーについて記述します。  
  
## <a name="rowset-columns"></a>行セットの列  
 `MDSCHEMA_MEMBERS`行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|説明|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||このメンバーが所属するデータベースの名前。|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||このメンバーが所属するスキーマの名前。|  
|`CUBE_NAME`|`DBTYPE_WSTR`||このメンバーが所属するキューブの名前。|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`||このメンバーが所属するディメンションの一意な名前。|  
|`HIERARCHY_UNIQUE_NAME`|`DBTYPE_WSTR`||このメンバーが所属する階層の一意の名前。|  
|`LEVEL_UNIQUE_NAME`|`DBTYPE_WSTR`||このメンバーが所属するレベルの一意の名前。|  
|`LEVEL_NUMBER`|`DBTYPE_UI4`||階層のルートからメンバーまでの距離。 ルートのレベルはゼロ (0) です。|  
|`MEMBER_ORDINAL`|`DBTYPE_UI4`||(非推奨) 常に `0` を返します。|  
|`MEMBER_NAME`|`DBTYPE_WSTR`||メンバーの名前。|  
|`MEMBER_UNIQUE_NAME`|`DBTYPE_WSTR`||メンバーの一意な名前。|  
|`MEMBER_TYPE`|`DBTYPE_I4`||メンバーの種類:<br /><br /> -   `MDMEMBER_TYPE_REGULAR` (`1`)<br />-   `MDMEMBER_TYPE_ALL` (`2`)<br />-   `MDMEMBER_TYPE_MEASURE` (`3`)<br />-   `MDMEMBER_TYPE_FORMULA` (`4`)<br />-   `MDMEMBER_TYPE_UNKNOWN` (`0`)<br />-   `MDMEMBER_TYPE_FORMULA` も優先`MDMEMBER_TYPE_MEASURE`です。 たとえば、メジャー ディメンションに式 (計算される) メンバーがある場合、そのメンバーは `MDMEMBER_TYPE_FORMULA` として示されます。|  
|`MEMBER_GUID`|`DBTYPE_GUID`||メンバーの GUID。 GUID が存在しない場合は、`NULL` です。|  
|`MEMBER_CAPTION`|`DBTYPE_WSTR`||メンバーに関連付けられたラベルまたはキャプション。 主に表示のために使用されます。 キャプションが存在しない場合`MEMBER_NAME`が返されます。|  
|`CHILDREN_CARDINALITY`|`DBTYPE_UI4`||メンバーが持つ子の数。 子の数は推定値の場合があります。したがって、この数値を正確な数として使用しないでください。 プロバイダーは、正確な数に最も近い推定値を返します。|  
|`PARENT_LEVEL`|`DBTYPE_UI4`||階層のルート レベルからメンバーの親までの距離。 ルートのレベルはゼロ (0) です。|  
|`PARENT_UNIQUE_NAME`|`DBTYPE_WSTR`||メンバーの親の一意の名前。 `NULL` ルート レベルのノードに対しては NULL を返します。|  
|`PARENT_COUNT`|`DBTYPE_UI4`||このメンバーが持つ親の数。|  
|`DESCRIPTION`|`DBTYPE_WSTR`||この列は常に `NULL` 値を返します。<br /><br /> この列は、下位互換性を維持するためにあります。|  
|`EXPRESSION`|`DBTYPE_WSTR`||メンバーの種類が `MDMEMBER_TYPE_FORMULA` の場合は、計算の式。|  
|`MEMBER_KEY`|`DBTYPE_WSTR`||メンバーのキー列の値。 メンバーが複合キーを持っている場合は、`NULL` を返します。|  
|`IS_PLACEHOLDERMEMBER`|`DBTYPE_BOOL`||メンバーがディメンション階層内の空の位置のプレースホルダー メンバーであるかどうかを示すブール値。<br /><br /> `MDX Compatibility` プロパティが 2 に設定されている場合にのみ有効です。|  
|`IS_DATAMEMBER`|`DBTYPE_BOOL`||メンバーがデータ メンバーであるかどうかを示すブール値。<br /><br /> メンバーがデータ メンバーである場合は True を返します。|  
|`SCOPE`|`DBTYPE_I4`||メンバーのスコープ。 メンバーは、セッションの計算されるメンバーまたはグローバルの計算されるメンバーです。 計算されないメンバーに対しては、`NULL` を返します。<br /><br /> この列は、次のいずれかの値になります。<br /><br /> -MDMEMBER_SCOPE_GLOBAL = 1<br />-MDMEMBER_SCOPE_SESSION = 2|  
|`Zero or more additional columns`|`DBTYPE_UI2`||複数のレベルからメンバーが返される可能性がある場合は、プロパティを返しません。 たとえば、非親子階層のツリー演算子が `PARENT` と `SELF` である場合、メンバー プロパティは返されません。<br /><br /> これは、ツリー演算子が異なるレベルのメンバーを返す可能性のある不規則な階層に適用されます (たとえば、前のレベルにホールが含まれており、メンバーに対する親が要求された場合など)。|  
  
 行セットは、`CATALOG_NAME`、`SCHEMA_NAME`、`CUBE_NAME`、`DIMENSION_UNIQUE_NAME`、`HIERARCHY_UNIQUE_NAME`、`LEVEL_UNIQUE_NAME`、`LEVEL_NUMBER`、`MEMBER_ORDINAL` を基準に並べ替えることができます。  
  
## <a name="restriction-columns"></a>制限の列  
 `MDSCHEMA_MEMBERS`行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|任意。|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|任意。|  
|`CUBE_NAME`|`DBTYPE_WSTR`|任意。|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`|任意。|  
|`HIERARCHY_UNIQUE_NAME`|`DBTYPE_WSTR`|任意。|  
|`LEVEL_UNIQUE_NAME`|`DBTYPE_WSTR`|任意。|  
|`LEVEL_NUMBER`|`DBTYPE_UI4`|任意。|  
|`MEMBER_NAME`|`DBTYPE_WSTR`|任意。|  
|`MEMBER_UNIQUE_NAME`|`DBTYPE_WSTR`|任意。|  
|`MEMBER_CAPTION`|`DBTYPE_WSTR`|任意。|  
|`MEMBER_TYPE`|`DBTYPE_I4`|任意。|  
|`TREE_OP`|`DBTYPE_I4`|(省略可) 1 つのメンバーにのみ適用されます。<br /><br /> -   `MDTREEOP_ANCESTORS` (`0x20`) すべての先祖を返します。<br />-   `MDTREEOP_CHILDREN` (`0x01`) 直接の子のみを返します。<br />-   `MDTREEOP_SIBLINGS` (`0x02`) と同じレベルにメンバーを返します。<br />-   `MDTREEOP_PARENT` (`0x04`) 直接の親のみを返します。<br />-   `MDTREEOP_SELF` (`0x08`) 返される行の一覧でそれ自体を返します。<br />-   `MDTREEOP_DESCENDANTS` (`0x10`) すべての子孫を返します。|  
|`CUBE_SOURCE`|`DBTYPE_UI2`|(省略可) 次のいずれかの有効値を含むビットマップ。<br /><br /> -1 のキューブ<br />2 つのディメンション<br /><br /> 既定の制限の値は 1 です。|  
  
## <a name="see-also"></a>参照  
 [OLE DB for OLAP Schema 行セット](ole-db-for-olap-schema-rowsets.md)  
  
  
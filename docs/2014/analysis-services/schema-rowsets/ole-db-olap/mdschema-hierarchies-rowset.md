---
title: MDSCHEMA_HIERARCHIES 行セット |Microsoft ドキュメント
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
- MDSCHEMA_HIERARCHIES
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_HIERARCHIES rowset
ms.assetid: 2e5b2a81-366e-4d5b-af1e-1d372bf596d9
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: e8c6fa75c935256235d64ad337500923b5974c68
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36084888"
---
# <a name="mdschemahierarchies-rowset"></a>MDSCHEMA_HIERARCHIES 行セット
  特定のディメンション内の各階層について記述します。  
  
## <a name="rowset-columns"></a>行セットの列  
 `MDSCHEMA_HIERARCHIES`行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|説明|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||この階層が所属するカタログの名前。 プロバイダーがカタログをサポートしない場合は `NULL` です。|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||サポートされていません|  
|`CUBE_NAME`|`DBTYPE_WSTR`||(必須) この階層が所属するキューブの名前。|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`||この階層が所属するディメンションの一意の名前。 修飾によって一意な名前を生成するプロバイダーの場合、この名前の各コンポーネントは区切り記号付きです。|  
|`HIERARCHY_NAME`|`DBTYPE_WSTR`||階層の名前です。 ディメンションに階層が 1 つしかない場合は空白です。 これが常に値[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。|  
|`HIERARCHY_UNIQUE_NAME`|`DBTYPE_WSTR`||階層の一意な名前。|  
|`HIERARCHY_GUID`|`DBTYPE_GUID`||サポートされていません|  
|`HIERARCHY_CAPTION`|`DBTYPE_WSTR`||ラベルまたは階層に関連付けられているキャプションです。 主に表示のために使用されます。 キャプションが存在しない場合`HIERARCHY_NAME`が返されます。 ディメンションに階層が含まれていないか、階層が 1 つしかない場合、この列にはディメンションの名前が格納されます。|  
|`DIMENSION_TYPE`|`DBTYPE_I2`||ディメンションの種類。 有効な値には、次の値があります。<br /><br /> -   `MD_DIMTYPE_UNKNOWN` (`0`)<br />-   `MD_DIMTYPE_TIME` (`1`)<br />-   `MD_DIMTYPE_MEASURE` (`2`)<br />-   `MD_DIMTYPE_OTHER` (`3`)<br />-   `MD_DIMTYPE_QUANTITATIVE` (`5`)<br />-   `MD_DIMTYPE_ACCOUNTS` (`6`)<br />-   `MD_DIMTYPE_CUSTOMERS` (`7`)<br />-   `MD_DIMTYPE_PRODUCTS` (`8`)<br />-   `MD_DIMTYPE_SCENARIO` (`9`)<br />-   `MD_DIMTYPE_UTILIY` (`10`)<br />-   `MD_DIMTYPE_CURRENCY` (`11`)<br />-   `MD_DIMTYPE_RATES` (`12`)<br />-   `MD_DIMTYPE_CHANNEL` (`13`)<br />-   `MD_DIMTYPE_PROMOTION` (`14`)<br />-   `MD_DIMTYPE_ORGANIZATION` (`15`)<br />-   `MD_DIMTYPE_BILL_OF_MATERIALS` (`16`)<br />-   `MD_DIMTYPE_GEOGRAPHY` (`17`)|  
|`HIERARCHY_CARDINALITY`|`DBTYPE_UI4`||階層内のメンバーの数。|  
|`DEFAULT_MEMBER`|`DBTYPE_WSTR`||この階層の既定のメンバー。 これは一意の名前です。 すべての階層に既定のメンバーが必要です。|  
|`ALL_MEMBER`|`DBTYPE_WSTR`||ロールアップの最高レベルのメンバー。|  
|`DESCRIPTION`|`DBTYPE_WSTR`||階層に関する人間が判読できる説明。 説明が存在しない場合は `NULL` になります。|  
|`STRUCTURE`|`DBTYPE_I2`||階層の構造。 有効な値には、次の値があります。<br /><br /> -   `MD_STRUCTURE_FULLYBALANCED` (`0`)<br />-   `MD_STRUCTURE_RAGGEDBALANCED` (`1`)<br />-   `MD_STRUCTURE_UNBALANCED` (`2`)<br />-   `MD_STRUCTURE_NETWORK` (`3`)|  
|`IS_VIRTUAL`|`DBTYPE_BOOL`||常に返します`False`です。|  
|`IS_READWRITE`|`DBTYPE_BOOL`||ディメンション列への書き戻しが有効になっているかどうかを示すブール値。<br /><br /> この階層を表す `TRUE` 列が有効になっている場合は、`Write Back to dimension` を返します。|  
|`DIMENSION_UNIQUE_SETTINGS`|`DBTYPE_I4`||常に `MDDIMENSIONS_MEMBER_KEY_UNIQUE` (`1`) を返します。|  
|`DIMENSION_MASTER_UNIQUE_NAME`|`DBTYPE_WSTR`||常に返します`NULL`です。|  
|`DIMENSION_IS_VISIBLE`|`DBTYPE_BOOL`||常に返します`true`です。 ディメンションが表示されていない場合は、スキーマ行セットに表示されません。|  
|`HIERARCHY_ORDINAL`|`DBTYPE_UI4`||キューブの全階層にわたる階層の序数。|  
|`DIMENSION_IS_SHARED`|`DBTYPE_BOOL`||常に返します`TRUE`です。|  
|`HIERARCHY_IS_VISIBLE`|`DBTYPE_BOOL`||階層が表示されるかどうかを示すブール値。<br /><br /> 階層が表示される場合は `TRUE` を、表示されない場合は `FALSE` を返します。|  
|`HIERARCHY_ORIGIN`|`DBTYPE_UI2`||階層のソースを決定するビット マスク。<br /><br /> -   `MD_USER_DEFINED` ユーザー定義階層を示しの値を持つ`0x0000001`します。<br />-   `MD_SYSTEM_ENABLED` 属性階層を示しの値を持つ`0x0000002`します。<br />-   `MD_SYSTEM_INTERNAL` 属性階層のないと属性を識別し、値を持つ**0x0000004**です。<br /><br /> 親子属性階層は、`MD_USER_DEFINED` と `MD_SYSTEM_ENABLED` の両方です。|  
|`HIERARCHY_DISPLAY_FOLDER`|`DBTYPE_WSTR`||ユーザー インターフェイスでの階層の表示に使用するパス。 フォルダー名はセミコロン (;) で区切られます。 入れ子になったフォルダーは円記号で示されます (\\)。|  
|`INSTANCE_SELECTION`|`DBTYPE_UI2`||階層の表示方法に関するクライアント アプリケーションへのヒント。 有効な値には、次の値があります。<br /><br /> -   `MD_INSTANCE_SELECTION_NONE`<br />-   `MD_INSTANCE_SELECTION_DROPDOWN`<br />-   `MD_INSTANCE_SELECTION_LIST`<br />-   `MD_INSTANCE_SELECTION_FILTEREDLIST`<br />-   `MD_INSTANCE_SELECTION_MANDATORYFILTER`|  
|`GROUPING_BEHAVIOR`|`DBTYPE_I2`||この階層のクライアントに期待されるグループ化の動作を指定する列挙。 次の値を指定できます。<br /><br /> -   **EncourageGrouping** (1)<br />-   **DiscourageGrouping** (2)|  
|`STRUCTURE_TYPE`|`DBTYPE_WSTR`||階層の種類を示します。 有効な値には、次の値があります。<br /><br /> -   `Natural`<br />-   `Unnatural`<br />-   `Unknown`|  
  
 行セットは、`CATALOG_NAME`、`SCHEMA_NAME`、`CUBE_NAME`、`DIMENSION_UNIQUE_NAME`、`HIERARCHY_NAME` を基準に並べ替えることができます。  
  
## <a name="restriction-columns"></a>制限の列  
 `MDSCHEMA_HIERARCHIES`行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|任意。|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|任意。|  
|`CUBE_NAME`|`DBTYPE_WSTR`|任意。|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`|任意。|  
|`HIERARCHY_NAME`|`DBTYPE_WSTR`|任意。|  
|`HIERARCHY_UNIQUE_NAME`|`DBTYPE_WSTR`|任意。|  
|`HIERARCHY_ORIGIN`|`DBTYPE_UI2`|(省略可) 既定の制限は、MD_USER_DEFINED と MD_SYSTEM_ENABLED で有効です。|  
|`CUBE_SOURCE`|`DBTYPE_UI2`|(省略可) 次のいずれかの有効値を含むビットマップ。<br /><br /> -1 のキューブ<br />2 つのディメンション<br /><br /> 既定の制限の値は 1 です。|  
|`HIERARCHY_VISIBILITY`|`DBTYPE_UI2`|(省略可) 次のいずれかの有効値を含むビットマップ。<br /><br /> -1 の表示<br />-2 not 表示<br /><br /> 既定の制限の値は 1 です。|  
  
## <a name="see-also"></a>参照  
 [OLE DB for OLAP Schema 行セット](ole-db-for-olap-schema-rowsets.md)  
  
  
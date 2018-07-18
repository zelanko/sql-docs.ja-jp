---
title: MDSCHEMA_DIMENSIONS 行セット |Microsoft Docs
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
- MDSCHEMA_DIMENSIONS
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_DIMENSIONS rowset
ms.assetid: a0fd94bb-359a-4df6-93a6-d60d50223944
caps.latest.revision: 29
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 69cb4e0c997d3d786a55a6673327e50d0aac27a2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37273398"
---
# <a name="mdschemadimensions-rowset"></a>MDSCHEMA_DIMENSIONS 行セット
  データベース内の共有ディメンションとプライベート ディメンションについて記述します。  
  
## <a name="rowset-columns"></a>行セットの列  
 `MDSCHEMA_DIMENSIONS`行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|説明|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||データベースの名前。|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||サポートされていません。|  
|`CUBE_NAME`|`DBTYPE_WSTR`||キューブの名前。|  
|`DIMENSION_NAME`|`DBTYPE_WSTR`||ディメンションの名前。 ディメンションが複数のキューブまたはメジャー グループの一部である場合は、ディメンション、メジャー グループ、およびキューブの一意の組み合わせごとに 1 つの行が存在します。|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`||ディメンションの一意の名前。|  
|`DIMENSION_GUID`|`DBTYPE_GUID`||サポートされていません。|  
|`DIMENSION_CAPTION`|`DBTYPE_WSTR`||ディメンションのキャプション。 ユーザー インターフェイスやレポートなどでディメンションの名前をユーザーに対して表示する場合に使用します。|  
|`DIMENSION_ORDINAL`|`DBTYPE_UI4`||キューブ内のディメンションの位置。|  
|`DIMENSION_TYPE`|`DBTYPE_I2`||ディメンションの種類。 有効な値は次のとおりです。<br /><br /> -   `MD_DIMTYPE_UNKNOWN` (`0`)<br />-   `MD_DIMTYPE_TIME` (`1`)<br />-   `MD_DIMTYPE_MEASURE` (`2`)<br />-   `MD_DIMTYPE_OTHER` (`3`)<br />-   `MD_DIMTYPE_QUANTITATIVE` (`5`)<br />-   `MD_DIMTYPE_ACCOUNTS` (`6`)<br />-   `MD_DIMTYPE_CUSTOMERS` (`7`)<br />-   `MD_DIMTYPE_PRODUCTS` (`8`)<br />-   `MD_DIMTYPE_SCENARIO` (`9`)<br />-   `MD_DIMTYPE_UTILIY` (`10`)<br />-   `MD_DIMTYPE_CURRENCY` (`11`)<br />-   `MD_DIMTYPE_RATES` (`12`)<br />-   `MD_DIMTYPE_CHANNEL` (`13`)<br />-   `MD_DIMTYPE_PROMOTION` (`14`)<br />-   `MD_DIMTYPE_ORGANIZATION` (`15`)<br />-   `MD_DIMTYPE_BILL_OF_MATERIALS` (`16`)<br />-   `MD_DIMTYPE_GEOGRAPHY` (`17`)|  
|`DIMENSION_CARDINALITY`|`DBTYPE_UI4`||キー属性内のメンバーの数。|  
|`DEFAULT_HIERARCHY`|`DBTYPE_WSTR`||ディメンションの階層。 これは旧バージョンとの互換性のために保持されています。|  
|`DESCRIPTION`|`DBTYPE_WSTR`||ディメンションについてのわかりやすい説明。|  
|`IS_VIRTUAL`|`DBTYPE_BOOL`||常に `FALSE` です。|  
|`IS_READWRITE`|`DBTYPE_BOOL`||ディメンションが書き込み許可されているかどうかを示すブール値。<br /><br /> ディメンションが書き込み許可されている場合は、`TRUE` になります。|  
|`DIMENSION_UNIQUE_SETTINGS`|`DBTYPE_I4`||ディメンションに一意の名前を持つメンバーのみが含まれている場合に、一意な値を含んでいる列を示すビットマップ。 このビットマップの Msmd.h では、次のビット値定数が定義されています。<br /><br /> -   `MDDIMENSIONS_MEMBER_KEY_UNIQUE`|  
|`DIMENSION_MASTER_UNIQUE_NAME`|`DBTYPE_WSTR`||常に `NULL` です。|  
|`DIMENSION_IS_VISIBLE`|`DBTYPE_BOOL`||常に `TRUE` です。 **注:** ディメンションが表示されていない限り、ディメンション内の 1 つまたは複数の階層が表示されます。|  
  
 行セットは、`CATALOG_NAME`、`SCHEMA_NAME`、`CUBE_NAME`、`DIMENSION_NAME` を基準に並べ替えることができます。  
  
## <a name="restriction-columns"></a>制限の列  
 `MDSCHEMA_DIMENSIONS`行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|任意。|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|任意。|  
|`CUBE_NAME`|`DBTYPE_WSTR`|任意。|  
|`DIMENSION_NAME`|`DBTYPE_WSTR`|任意。|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`|任意。|  
|`CUBE_SOURCE`|`DBTYPE_UI2`|(省略可) 次のいずれかの有効値を含むビットマップ。<br /><br /> -1 のキューブ<br />-2 つのディメンション<br /><br /> 既定の制限の値は 1 です。|  
|`DIMENSION_VISIBILITY`|`DBTYPE_UI2`|(省略可) 次のいずれかの有効値を含むビットマップ。<br /><br /> -1 の表示<br />-2 の非表示<br /><br /> 既定の制限の値は 1 です。|  
  
## <a name="see-also"></a>参照  
 [OLE DB for OLAP Schema 行セット](ole-db-for-olap-schema-rowsets.md)  
  
  

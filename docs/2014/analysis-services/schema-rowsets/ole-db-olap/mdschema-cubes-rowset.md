---
title: MDSCHEMA_CUBES 行セット |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- MDSCHEMA_CUBES
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_CUBES rowset
ms.assetid: 5f1b63d4-aa3f-48c6-b866-7ffd91675044
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 0044c9943b2f2819ea216c735f298b7e30de7a3a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36174250"
---
# <a name="mdschemacubes-rowset"></a>MDSCHEMA_CUBES 行セット
  データベース内のキューブの構造について記述します。  
  
## <a name="rowset-columns"></a>行セットの列  
 `MDSCHEMA_CUBES`行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|説明|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||データベースの名前。|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||サポートされていません。|  
|`CUBE_NAME`|`DBTYPE_WSTR`||キューブまたはディメンションの名前。 ディメンション名の先頭にはドル記号 ($) が付いています。 **注:** ディメンションから作成されたキューブを表示するアクセス許可を持つサーバーとデータベース管理者だけです。|  
|`CUBE_TYPE`|`DBTYPE_WSTR`||キューブの種類。 有効な値は、<br /><br /> -   `CUBE`<br />-   `DIMENSION`|  
|`CUBE_GUID`|`DBTYPE_GUID`||サポートされていません。|  
|`CREATED_ON`|`DBTYPE_DBTIMESTAMP`||サポートされていません。|  
|`LAST_SCHEMA_UPDATE`|`DBTYPE_DBTIMESTAMP`||キューブの最終処理時刻。|  
|`SCHEMA_UPDATED_BY`|`DBTYPE_WSTR`||サポートされていません。|  
|`LAST_DATA_UPDATE`|`DBTYPE_DBTIMESTAMP`||キューブの最終処理時刻。|  
|`DATA_UPDATED_BY`|`DBTYPE_WSTR`||サポートされていません。|  
|`DESCRIPTION`|`DBTYPE_WSTR`||キューブについてのわかりやすい説明。|  
|`IS_DRILLTHROUGH_ENABLED`|`DBTYPE_BOOL`||ブール値を常に true を返します。|  
|`IS_LINKABLE`|`DBTYPE_BOOL`||キューブをリンク キューブ内で使用できるかどうかを示すブール値。|  
|`IS_WRITE_ENABLED`|`DBTYPE_BOOL`||キューブが書き込み許可されているかどうかを示すブール値。|  
|`IS_SQL_ENABLED`|`DBTYPE_BOOL`||SQL をキューブで使用できるかどうかを示すブール値。|  
|`CUBE_CAPTION`|`DBTYPE_WSTR`||キューブのキャプション。|  
|`BASE_CUBE_NAME`|`DBTYPE_WSTR`||このキューブがパースペクティブキューブである場合は、ソース キューブの名前。|  
|`ANNOTATIONS`|`DBTYPE_WSTR`||(省略可) XML 形式のメモのセット。|  
  
 行セットは、`CATALOG_NAME`、`SCHEMA_NAME`、`CUBE_NAME` を基準に並べ替えることができます。  
  
## <a name="restriction-columns"></a>制限の列  
 `MDSCHEMA_CUBES`行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|任意。|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|任意。|  
|`CUBE_NAME`|`DBTYPE_WSTR`|任意。|  
|`CUBE_SOURCE`|`DBTYPE_UI2`|(省略可) 次のいずれかの有効値を含むビットマップ。 <br /><br /> -1 のキューブ<br />2 つのディメンション<br /><br /> 既定の制限の値は 1 です。|  
|`Base Cube_Name`|`DBTYPE_WSTR`|任意。|  
  
## <a name="see-also"></a>参照  
 [OLE DB for OLAP Schema 行セット](ole-db-for-olap-schema-rowsets.md)  
  
  
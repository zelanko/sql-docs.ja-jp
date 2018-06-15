---
title: MDSCHEMA_CUBES 行セット |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: da0fc34fedcd6980f8dd19e199314fc1295c78bb
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34037073"
---
# <a name="mdschemacubes-rowset"></a>MDSCHEMA_CUBES 行セット
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  データベース内のキューブの構造について記述します。  
  
## <a name="rowset-columns"></a>行セットの列  
 **MDSCHEMA_CUBES**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|Description|  
|-----------------|--------------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|データベースの名前。|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|サポートされていません。|  
|**CUBE_NAME**|**DBTYPE_WSTR**|キューブまたはディメンションの名前。 ディメンション名の先頭にはドル記号 ($) が付いています。<br /><br /> 注: サーバーとデータベース管理者のみに対する権限、ディメンションから作成されたキューブを参照してください。|  
|**CUBE_TYPE**|**DBTYPE_WSTR**|キューブの種類。 以下の値が有効です。<br /><br /> **キューブ**<br /><br /> **ディメンション**|  
|**CUBE_GUID**|**DBTYPE_GUID 型**|サポートされていません。|  
|**CREATED_ON**|**DBTYPE_DBTIMESTAMP**|サポートされていません。|  
|**LAST_SCHEMA_UPDATE**|**DBTYPE_DBTIMESTAMP**|キューブの最終処理時刻。|  
|**SCHEMA_UPDATED_BY**|**DBTYPE_WSTR**|サポートされていません。|  
|**LAST_DATA_UPDATE**|**DBTYPE_DBTIMESTAMP**|キューブの最終処理時刻。|  
|**DATA_UPDATED_BY**|**DBTYPE_WSTR**|サポートされていません。|  
|**DESCRIPTION**|**DBTYPE_WSTR**|キューブについてのわかりやすい説明。|  
|**IS_DRILLTHROUGH_ENABLED**|**DBTYPE_BOOL**|ブール値を常に true を返します。|  
|**IS_LINKABLE**|**DBTYPE_BOOL**|キューブをリンク キューブ内で使用できるかどうかを示すブール値。|  
|**IS_WRITE_ENABLED**|**DBTYPE_BOOL**|キューブが書き込み許可されているかどうかを示すブール値。|  
|**IS_SQL_ENABLED**|**DBTYPE_BOOL**|SQL をキューブで使用できるかどうかを示すブール値。|  
|**CUBE_CAPTION**|**DBTYPE_WSTR**|キューブのキャプション。|  
|**BASE_CUBE_NAME**|**DBTYPE_WSTR**|このキューブがパースペクティブキューブである場合は、ソース キューブの名前。|  
|**注釈**|**DBTYPE_WSTR**|(省略可) XML 形式のメモのセット。|  
  
 行セットが並べ替えられて**CATALOG_NAME**、 **SCHEMA_NAME**、 **CUBE_NAME**です。  
  
## <a name="restriction-columns"></a>制限の列  
 **MDSCHEMA_CUBES**行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|省略可。|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|省略可。|  
|**CUBE_NAME**|**DBTYPE_WSTR**|省略可。|  
|**CUBE_SOURCE**|**DBTYPE_UI2**|(省略可能)既定の制限は、1 の値です。 これらの有効な値のいずれかのビットマップ。<br /><br /> 1 キューブ<br /><br /> 2 ディメンション|  
|**基本 Cube_Name**|**DBTYPE_WSTR**|省略可。|  
  
## <a name="see-also"></a>参照  
 [OLE DB for OLAP スキーマ行セット](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  

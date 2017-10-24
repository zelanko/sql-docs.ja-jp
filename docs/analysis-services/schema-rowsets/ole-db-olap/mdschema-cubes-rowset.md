---
title: "MDSCHEMA_CUBES 行セット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- MDSCHEMA_CUBES
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- MDSCHEMA_CUBES rowset
ms.assetid: 5f1b63d4-aa3f-48c6-b866-7ffd91675044
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9a3fa75f9ea6bcab54d123d6e914d5d77077b44e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="mdschemacubes-rowset"></a>MDSCHEMA_CUBES 行セット
  データベース内のキューブの構造について記述します。  
  
## <a name="rowset-columns"></a>行セットの列  
 **MDSCHEMA_CUBES**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|Description|  
|-----------------|--------------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|データベースの名前。|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|サポートされていません。|  
|**CUBE_NAME**|**DBTYPE_WSTR**|キューブまたはディメンションの名前。 ディメンション名の先頭にはドル記号 ($) が付いています。<br /><br /> 注: サーバーとデータベース管理者のみに対する権限、ディメンションから作成されたキューブを参照してください。|  
|**CUBE_TYPE**|**DBTYPE_WSTR**|キューブの種類。 有効な値は、<br /><br /> **キューブ**<br /><br /> **ディメンション**|  
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
  
  


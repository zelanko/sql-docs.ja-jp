---
title: DBSCHEMA_TABLES 行セット |Microsoft ドキュメント
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
- DBSCHEMA_TABLES
topic_type:
- apiref
helpviewer_keywords:
- DBSCHEMA_TABLES rowset
ms.assetid: 14c16e6b-0aff-4ad1-b98f-cdb7df0f8d73
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 9033dc2f48b74bc13268d06f66a084f4ada22cfc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36085967"
---
# <a name="dbschematables-rowset"></a>DBSCHEMA_TABLES 行セット
  メジャー グループおよび内のテーブルとして公開されているディメンションを識別[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。  
  
## <a name="rowset-columns"></a>行セットの列  
 `DBSCHEMA_TABLES`行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|説明|  
|-----------------|--------------------|------------|-----------------|  
|`TABLE_CATALOG`|`DBTYPE_WSTR`|255|このオブジェクトが所属するカタログの名前。|  
|`TABLE_SCHEMA`|`DBTYPE_WSTR`|255|このオブジェクトが所属するキューブの名前。|  
|`TABLE_NAME`|`DBTYPE_WSTR`|255|`TABLE_TYPE` が `TABLE` である場合、オブジェクトの名前。|  
|`TABLE_TYPE`|`DBTYPE_WSTR`||テーブルの型。<br /><br /> `TABLE` は、オブジェクトがメジャー グループであることを示します。<br /><br /> `SYSTEM TABLE` オブジェクトが、ディメンションであることを示します。|  
|`TABLE_GUID`|`DBTYPE_GUID`||サポートされていません。|  
|`DESCRIPTION`|`DBTYPE_WSTR`||オブジェクトに関して人が認識できる説明。|  
|`TABLE_PROPID`|`DBTYPE_UI4`||サポートされていません。|  
|`DATE_CREATED`|`DBTYPE_DBTIMESTAMP`||サポートされていません。|  
|`DATE_MODIFIED`|`DBTYPE_DBTIMESTAMP`||オブジェクトの最終変更日。|  
|`TABLE_OLAP_TYPE`|`DBTYPE_WSTR`||オブジェクトの OLAP 型。<br /><br /> **MEASURE_GROUP**オブジェクトがメジャー グループであることを示します。<br /><br /> `CUBE_DIMENSION` は、オブジェクトがディメンションであることを示します。|  
  
 行セットは、`TABLE_TYPE`、`TABLE_CATALOG`、`TABLE_SCHEMA`、および `TABLE_NAME` を基準に並べ替えることができます。  
  
## <a name="restriction-columns"></a>制限の列  
 `DBSCHEMA_TABLES`行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|`TABLE_CATALOG`|`DBTYPE_WSTR`|省略可|  
|`TABLE_SCHEMA`|`DBTYPE_WSTR`|省略可|  
|`TABLE_NAME`|`DBTYPE_WSTR`|省略可|  
|`TABLE_TYPE`|`DBTYPE_WSTR`|省略可|  
|`TABLE_OLAP_TYPE`|`DBTYPE_WSTR`|省略可|  
  
## <a name="see-also"></a>参照  
 [OLE DB Schema 行セット](ole-db-schema-rowsets.md)  
  
  
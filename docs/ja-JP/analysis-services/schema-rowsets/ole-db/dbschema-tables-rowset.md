---
title: DBSCHEMA_TABLES 行セット |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DBSCHEMA_TABLES
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DBSCHEMA_TABLES rowset
ms.assetid: 14c16e6b-0aff-4ad1-b98f-cdb7df0f8d73
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 1e6117a2a17457a919e202a6dfeef411a766e0f3
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="dbschematables-rowset"></a>DBSCHEMA_TABLES 行セット
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  メジャー グループおよび内のテーブルとして公開されているディメンションを識別[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。  
  
## <a name="rowset-columns"></a>行セットの列  
 **DBSCHEMA_TABLES**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|Description|  
|-----------------|--------------------|------------|-----------------|  
|**TABLE_CATALOG**|**DBTYPE_WSTR**|255|このオブジェクトが所属するカタログの名前。|  
|**TABLE_SCHEMA**|**DBTYPE_WSTR**|255|このオブジェクトが所属するキューブの名前。|  
|**TABLE_NAME**|**DBTYPE_WSTR**|255|オブジェクトの名前場合**TABLE_TYPE**は**テーブル**です。|  
|**TABLE_TYPE**|**DBTYPE_WSTR**||テーブルの型。<br /><br /> **テーブル**オブジェクトがメジャー グループであることを示します。<br /><br /> **システム テーブル**オブジェクトが、ディメンションであることを示します。|  
|**TABLE_GUID**|**DBTYPE_GUID 型**||サポートされていません。|  
|**DESCRIPTION**|**DBTYPE_WSTR**||オブジェクトに関して人が認識できる説明。|  
|**TABLE_PROPID**|**DBTYPE_UI4**||サポートされていません。|  
|**DATE_CREATED**|**DBTYPE_DBTIMESTAMP**||サポートされていません。|  
|**DATE_MODIFIED**|**DBTYPE_DBTIMESTAMP**||オブジェクトの最終変更日。|  
|**TABLE_OLAP_TYPE**|**DBTYPE_WSTR**||オブジェクトの OLAP 型。<br /><br /> **MEASURE_GROUP**オブジェクトがメジャー グループであることを示します。<br /><br /> **CUBE_DIMENSION**ディメンション オブジェクトを示しています。|  
  
 行セットが並べ替えられて**TABLE_TYPE**、 **TABLE_CATALOG**、 **、table_schema、**、および**TABLE_NAME**です。  
  
## <a name="restriction-columns"></a>制限の列  
 **DBSCHEMA_TABLES**行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|**TABLE_CATALOG**|**DBTYPE_WSTR**|省略可|  
|**TABLE_SCHEMA**|**DBTYPE_WSTR**|省略可|  
|**TABLE_NAME**|**DBTYPE_WSTR**|省略可|  
|**TABLE_TYPE**|**DBTYPE_WSTR**|省略可|  
|**TABLE_OLAP_TYPE**|**DBTYPE_WSTR**|省略可|  
  
## <a name="see-also"></a>参照  
 [OLE DB スキーマ行セット](../../../analysis-services/schema-rowsets/ole-db/ole-db-schema-rowsets.md)  
  
  

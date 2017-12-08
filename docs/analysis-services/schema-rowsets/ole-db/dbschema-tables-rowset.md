---
title: "DBSCHEMA_TABLES 行セット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
apiname: DBSCHEMA_TABLES
apitype: NA
applies_to: SQL Server 2016 Preview
helpviewer_keywords: DBSCHEMA_TABLES rowset
ms.assetid: 14c16e6b-0aff-4ad1-b98f-cdb7df0f8d73
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 50ba3f0ac4c0dc0090df5fd3122dcff7e7e6923a
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="dbschematables-rowset"></a>DBSCHEMA_TABLES 行セット
  メジャー グループおよび内のテーブルとして公開されているディメンションを識別[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。  
  
## <a name="rowset-columns"></a>行セットの列  
 **DBSCHEMA_TABLES**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|Description|  
|-----------------|--------------------|------------|-----------------|  
|**TABLE_CATALOG**|**DBTYPE_WSTR**|255|このオブジェクトが所属するカタログの名前。|  
|**TABLE_SCHEMA、**|**DBTYPE_WSTR**|255|このオブジェクトが所属するキューブの名前。|  
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
|**TABLE_SCHEMA、**|**DBTYPE_WSTR**|省略可|  
|**TABLE_NAME**|**DBTYPE_WSTR**|省略可|  
|**TABLE_TYPE**|**DBTYPE_WSTR**|省略可|  
|**TABLE_OLAP_TYPE**|**DBTYPE_WSTR**|省略可|  
  
## <a name="see-also"></a>参照  
 [OLE DB Schema 行セット](../../../analysis-services/schema-rowsets/ole-db/ole-db-schema-rowsets.md)  
  
  

---
title: DBSCHEMA_CATALOGS 行セット |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DBSCHEMA_CATALOGS
topic_type:
- apiref
helpviewer_keywords:
- DBSCHEMA_CATALOGS rowset
ms.assetid: f02dc75d-5442-4eea-b33a-567dc816be7a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f9c503d60de405836d90938caa6bff10f96378a1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48163232"
---
# <a name="dbschemacatalogs-rowset"></a>DBSCHEMA_CATALOGS 行セット
  データベース管理システム (DBMS) からアクセス可能なカタログに関連付けられている物理属性を識別します。  
  
## <a name="rowset-columns"></a>行セットの列  
 `DBSCHEMA_CATALOGS`行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|説明|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|255|カタログ名。 null にすることはできません。|  
|`DESCRIPTION`|`DBTYPE_WSTR`||テーブルに関して人が認識できる説明。|  
|`ROLES`|`DBTYPE_WSTR`||現在のユーザーが所属するロールのコンマ区切りの一覧。<br /><br /> アスタリスク (\*) は、現在のユーザーがサーバーまたはデータベース管理者の場合、ロールとして含まれます。<br /><br /> いずれかのロールで動的なセキュリティを使用する場合は、`Username` が `ROLES` に追加されます。|  
|`DATE_MODIFIED`|`DBTYPE_DBTIMESTAMP`||カタログの最後変更日。|  
  
 行セットは、`CATALOG_NAME` を基準に並べ替えることができます。  
  
## <a name="restriction-columns"></a>制限の列  
 `DBSCHEMA_CATALOGS`行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|省略可|  
  
## <a name="see-also"></a>関連項目  
 [OLE DB Schema 行セット](ole-db-schema-rowsets.md)  
  
  

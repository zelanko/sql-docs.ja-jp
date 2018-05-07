---
title: DBSCHEMA_CATALOGS 行セット |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0180ba3bc28335246cdd5b85cff9b60e5044dd21
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="dbschemacatalogs-rowset"></a>DBSCHEMA_CATALOGS 行セット
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  データベース管理システム (DBMS) からアクセス可能なカタログに関連付けられている物理属性を識別します。  
  
## <a name="rowset-columns"></a>行セットの列  
 **DBSCHEMA_CATALOGS**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|Description|  
|-----------------|--------------------|------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|255|カタログ名。 null にすることはできません。|  
|**DESCRIPTION**|**DBTYPE_WSTR**||テーブルに関して人が認識できる説明。|  
|**ロール**|**DBTYPE_WSTR**||現在のユーザーが所属するロールのコンマ区切りの一覧。<br /><br /> アスタリスク (\*)、現在のユーザーがサーバーまたはデータベース管理者の場合は、ロールとして含まれます。<br /><br /> **ユーザー名**に付加されます**ロール**動的なセキュリティを使用して、ロールのいずれかの場合。|  
|**DATE_MODIFIED**|**DBTYPE_DBTIMESTAMP**||カタログの最後変更日。|  
  
 行セットが並べ替えられて**CATALOG_NAME**です。  
  
## <a name="restriction-columns"></a>制限の列  
 **DBSCHEMA_CATALOGS**行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|省略可|  
  
## <a name="see-also"></a>参照  
 [OLE DB スキーマ行セット](../../../analysis-services/schema-rowsets/ole-db/ole-db-schema-rowsets.md)  
  
  

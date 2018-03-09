---
title: "LINKEDSERVERS 行セット (OLE DB) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- LINKEDSERVERS rowset
- enumerating data sources [OLE DB]
ms.assetid: 2633fd8a-65e7-498d-9aed-8e4b1cca2381
caps.latest.revision: "29"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6d2eb6f83bf15e555826fc7cba6ddcaa9d45b860
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="schema-rowsets---linkedservers-rowset"></a>スキーマ行セットの LINKEDSERVERS 行セット
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  **LINKEDSERVERS**行セットに含めることが組織のデータ ソースを列挙する[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]分散クエリ。  
  
 **LINKEDSERVERS**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|Description|  
|-----------------|--------------------|-----------------|  
|SVR_NAME|DBTYPE_WSTR|リンク サーバーの名前です。|  
|SVR_PRODUCT|DBTYPE_WSTR|メーカーなどの名前。リンク サーバーの名前で表されるデータ ストアの種類を識別します。|  
|SVR_PROVIDERNAME|DBTYPE_WSTR|サーバーからのデータにアクセスする場合に使用する OLE DB プロバイダーの表示名。|  
|SVR_DATASOURCE|DBTYPE_WSTR|プロバイダーからデータ ソースを取得する場合に使用する OLE DB DBPROP_INIT_DATASOURCE 文字列。|  
|SVR_PROVIDERSTRING|DBTYPE_WSTR|プロバイダーからデータ ソースを取得する場合に使用する OLE DB DBPROP_INIT_PROVIDERSTRING 値。|  
|SVR_LOCATION|DBTYPE_WSTR|プロバイダーからデータ ソースを取得する場合に使用する OLE DB DBPROP_INIT_LOCATION 文字列。|  
  
 行セットは SRV_NAME で並べ替えられます。SRV_NAME では 1 つの制限がサポートされます。  
  
## <a name="see-also"></a>参照  
 [スキーマ行セットのサポート &#40;OLE DB&#41;](../../../relational-databases/native-client/ole-db/schema-rowset-support-ole-db.md)  
  
  

---
title: LINKEDSERVERS 行セット (OLE DB) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-ole-db
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- LINKEDSERVERS rowset
- enumerating data sources [OLE DB]
ms.assetid: 2633fd8a-65e7-498d-9aed-8e4b1cca2381
caps.latest.revision: 29
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 2db65b2c936143c2f1f4987ac6ba79482e7b06b3
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39539672"
---
# <a name="schema-rowsets---linkedservers-rowset"></a>スキーマ行セット - LINKEDSERVERS 行セット
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  **LINKEDSERVERS** 行セットは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 分散クエリに参加できる、組織のデータ ソースを列挙します。  
  
 **LINKEDSERVERS** 行セットは、次の列で構成されます。  
  
|列名|型を表すインジケーター|説明|  
|-----------------|--------------------|-----------------|  
|SVR_NAME|DBTYPE_WSTR|リンク サーバーの名前。|  
|SVR_PRODUCT|DBTYPE_WSTR|メーカーなどの名前。リンク サーバーの名前で表されるデータ ストアの種類を識別します。|  
|SVR_PROVIDERNAME|DBTYPE_WSTR|サーバーからのデータにアクセスする場合に使用する OLE DB プロバイダーの表示名。|  
|SVR_DATASOURCE|DBTYPE_WSTR|プロバイダーからデータ ソースを取得する場合に使用する OLE DB DBPROP_INIT_DATASOURCE 文字列。|  
|SVR_PROVIDERSTRING|DBTYPE_WSTR|プロバイダーからデータ ソースを取得する場合に使用する OLE DB DBPROP_INIT_PROVIDERSTRING 値。|  
|SVR_LOCATION|DBTYPE_WSTR|プロバイダーからデータ ソースを取得する場合に使用する OLE DB DBPROP_INIT_LOCATION 文字列。|  
  
 行セットは SRV_NAME で並べ替えられます。SRV_NAME では 1 つの制限がサポートされます。  
  
## <a name="see-also"></a>参照  
 [スキーマ行セットのサポート &#40;OLE DB&#41;](../../../relational-databases/native-client/ole-db/schema-rowset-support-ole-db.md)  
  
  

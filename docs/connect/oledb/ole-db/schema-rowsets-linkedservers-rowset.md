---
title: LINKEDSERVERS 行セット (OLE DB) | Microsoft Docs
description: LINKEDSERVERS 行セット (OLE DB)
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- LINKEDSERVERS rowset
- enumerating data sources [OLE DB]
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 75b443df235fd99f262cf3fda0abf6a6354da413
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "67993878"
---
# <a name="schema-rowsets---linkedservers-rowset"></a>スキーマ行セット - LINKEDSERVERS 行セット
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

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
 [スキーマ行セットのサポート &#40;OLE DB&#41;](../../oledb/ole-db/schema-rowset-support-ole-db.md)  
  
  

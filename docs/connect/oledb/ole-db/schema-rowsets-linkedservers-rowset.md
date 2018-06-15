---
title: LINKEDSERVERS 行セット (OLE DB) |Microsoft ドキュメント
description: LINKEDSERVERS 行セット (OLE DB)
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- LINKEDSERVERS rowset
- enumerating data sources [OLE DB]
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: ff4c35178b5cc047fb711821b332f43cf0094fc8
ms.sourcegitcommit: 354ed9c8fac7014adb0d752518a91d8c86cdce81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/14/2018
ms.locfileid: "35611727"
---
# <a name="schema-rowsets---linkedservers-rowset"></a>スキーマ行セットの LINKEDSERVERS 行セット
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  **LINKEDSERVERS**行セットに含めることが組織のデータ ソースを列挙する[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]分散クエリ。  
  
 **LINKEDSERVERS**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|説明|  
|-----------------|--------------------|-----------------|  
|SVR_NAME|DBTYPE_WSTR|リンク サーバーの名前です。|  
|SVR_PRODUCT|DBTYPE_WSTR|メーカーなどの名前。リンク サーバーの名前で表されるデータ ストアの種類を識別します。|  
|SVR_PROVIDERNAME|DBTYPE_WSTR|サーバーからのデータにアクセスする場合に使用する OLE DB プロバイダーの表示名。|  
|SVR_DATASOURCE|DBTYPE_WSTR|プロバイダーからデータ ソースを取得する場合に使用する OLE DB DBPROP_INIT_DATASOURCE 文字列。|  
|SVR_PROVIDERSTRING|DBTYPE_WSTR|プロバイダーからデータ ソースを取得する場合に使用する OLE DB DBPROP_INIT_PROVIDERSTRING 値。|  
|SVR_LOCATION|DBTYPE_WSTR|プロバイダーからデータ ソースを取得する場合に使用する OLE DB DBPROP_INIT_LOCATION 文字列。|  
  
 行セットは SRV_NAME で並べ替えられます。SRV_NAME では 1 つの制限がサポートされます。  
  
## <a name="see-also"></a>参照  
 [スキーマ行セットのサポート&#40;OLE DB&#41;](../../oledb/ole-db/schema-rowset-support-ole-db.md)  
  
  

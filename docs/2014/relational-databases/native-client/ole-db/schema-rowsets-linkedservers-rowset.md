---
title: LINKEDSERVERS 行セット (OLE DB) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- LINKEDSERVERS rowset
- enumerating data sources [OLE DB]
ms.assetid: 2633fd8a-65e7-498d-9aed-8e4b1cca2381
caps.latest.revision: 28
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0901178fa2d99e4faf19c749026e2e1b1c17da7b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36164535"
---
# <a name="linkedservers-rowset-ole-db"></a>LINKEDSERVERS 行セット (OLE DB)
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
 [スキーマ行セットのサポート&#40;OLE DB&#41;](schema-rowset-support-ole-db.md)  
  
  
---
title: MDSCHEMA_INPUT_DATASOURCES 行セット |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- MDSCHEMA_INPUT_DATASOURCES
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_INPUT_DATASOURCES rowset
ms.assetid: 12482fd5-16e3-4171-9cb0-76d0d4f5308e
caps.latest.revision: 29
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: aedd2980b6c51872a9d78d6d1c2cbbecc84d7ec4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37249112"
---
# <a name="mdschemainputdatasources-rowset"></a>MDSCHEMA_INPUT_DATASOURCES 行セット
  データベース内で定義されたデータ ソースについて記述します。  
  
## <a name="rowset-columns"></a>行セットの列  
 `MDSCHEMA_INPUT_DATASOURCES`行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|説明|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||このデータ ソースが所属するカタログの名前。|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||サポートされていません。|  
|`DATASOURCE_NAME`|`DBTYPE_WSTR`||データ ソース オブジェクトの名前。|  
|`DATASOURCE_TYPE`|`DBTYPE_WSTR`||データ ソースの種類。 有効な値は次のとおりです。<br /><br /> -   `Relational`<br />-   `Olap`|  
|`CREATED_ON`|`DBTYPE_DBTIMESTAMP`||データ ソースの作成日。|  
|`LAST_SCHEMA_UPDATE`|`DBTYPE_DBTIMESTAMP`||データ ソースの最終変更日時。|  
|`DESCRIPTION`|`DBTYPE_WSTR`||アクションについてのわかりやすい説明。|  
|`TIMEOUT`|`DBTYPE_UI4`||データ ソースのタイムアウト。|  
  
 このスキーマ行セットは並べ替えられません。  
  
## <a name="restriction-columns"></a>制限の列  
 `MDSCHEMA_INPUT_DATASOURCES`行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|任意。|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|任意。|  
|`DATASOURCE_NAME`|`DBTYPE_WSTR`|任意。|  
|`DATASOURCE_TYPE`|`DBTYPE_WSTR`|任意。|  
  
## <a name="see-also"></a>参照  
 [OLE DB for OLAP Schema 行セット](ole-db-for-olap-schema-rowsets.md)  
  
  

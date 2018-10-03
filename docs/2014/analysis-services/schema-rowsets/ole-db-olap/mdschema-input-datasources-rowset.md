---
title: MDSCHEMA_INPUT_DATASOURCES 行セット |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MDSCHEMA_INPUT_DATASOURCES
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_INPUT_DATASOURCES rowset
ms.assetid: 12482fd5-16e3-4171-9cb0-76d0d4f5308e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fa2f372c4facb1b2e51561bbd82a8e35fe8ed134
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48210032"
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
  
  

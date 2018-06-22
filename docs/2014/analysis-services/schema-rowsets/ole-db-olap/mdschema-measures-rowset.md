---
title: MDSCHEMA_MEASURES 行セット |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- MDSCHEMA_MEASURES
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_MEASURES rowset
ms.assetid: 6ff5bd1a-aad0-49b8-9f8d-7df2637caacf
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 6608c64caa882499282ad7a7e30090ab4118b522
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36070557"
---
# <a name="mdschemameasures-rowset"></a>MDSCHEMA_MEASURES 行セット
  キューブ内の各メジャーについて記述します。  
  
## <a name="rowset-columns"></a>行セットの列  
 `MDSCHEMA_MEASURES`行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|説明|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||このメジャーが所属するカタログの名前。 プロバイダーがカタログをサポートしない場合は `NULL` です。|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||このメジャーが属するスキーマの名前。 プロバイダーでスキーマがサポートされていない場合は `NULL` になります。|  
|`CUBE_NAME`|`DBTYPE_WSTR`||このメジャーが所属するキューブの名前。|  
|`MEASURE_NAME`|`DBTYPE_WSTR`||メジャーの名前。|  
|`MEASURE_UNIQUE_NAME`|`DBTYPE_WSTR`||メジャーの一意の名前。 修飾によって一意な名前を生成するプロバイダーの場合、この名前の各コンポーネントは区切り記号付きです。|  
|`MEASURE_CAPTION`|`DBTYPE_WSTR`||メジャーに関連付けられたラベルまたはキャプション。 主に表示のために使用されます。 キャプションが存在しない場合`MEASURE_NAME`が返されます。|  
|`MEASURE_GUID`|`DBTYPE_GUID`||サポートされていません。|  
|`MEASURE_AGGREGATOR`|`DBTYPE_I4`||メジャーがどのように派生したかを識別する列挙。 次の値のいずれかです。<br /><br /> -   `MDMEASURE_AGGR_SUM` (`1`) からメジャーを集計することを識別`SUM`です。<br />-   `MDMEASURE_AGGR_COUNT` (`2`) からメジャーを集計することを識別`COUNT`です。<br />-   **MDMEASURE_AGGR_MIN** (`3`) からメジャーを集計することを識別`MIN`です。<br />-   **MDMEASURE_AGGR_MAX** (`4`) からメジャーを集計することを識別`MAX`です。<br />-   `MDMEASURE_AGGR_AVG` (`5`) からメジャーを集計することを識別`AVG`です。<br />-   `MDMEASURE_AGGR_VAR` (`6`) からメジャーを集計することを識別`VAR`です。<br />-   `MDMEASURE_AGGR_STD` (`7`) からメジャーを集計することを識別`STDEV`です。<br />-   `MDMEASURE_AGGR_DST` (`8`) からメジャーを集計することを識別`DISTINCT COUNT`です。<br />-   `MDMEASURE_AGGR_NONE` (`9`) からメジャーを集計することを識別`NONE`です。<br />-   `MDMEASURE_AGGR_AVGCHILDREN` (`10`) からメジャーを集計することを識別`AVERAGEOFCHILDREN`です。<br />-   `MDMEASURE_AGGR_FIRSTCHILD` (`11`) からメジャーを集計することを識別`FIRSTCHILD`です。<br />-   `MDMEASURE_AGGR_LASTCHILD` (`12`) からメジャーを集計することを識別`LASTCHILD`です。<br />-   `MDMEASURE_AGGR_FIRSTNONEMPTY` (`13`) からメジャーを集計することを識別`FIRSTNONEMPTY`、<br />-   `MDMEASURE_AGGR_LASTNONEMPTY` (`14`) からメジャーを集計することを識別`LASTNONEMPTY`です。<br />-   `MDMEASURE_AGGR_BYACCOUNT` (`15`) からメジャーを集計することを識別`BYACCOUNT`です。<br />-   `MDMEASURE_AGGR_CALCULATED` (`127`) が使用されて記の関数式からメジャーが派生したことを識別します。<br />-   `MDMEASURE_AGGR_UNKNOWN` (`0`)、不明な集計関数または式からメジャーが派生したことを識別します。|  
|`DATA_TYPE`|`DBTYPE_UI2`||メジャーのデータ型。|  
|`NUMERIC_PRECISION`|`DBTYPE_UI2`||メジャー オブジェクトのデータ型が真数の場合は、プロパティの最大有効桁数。 その他すべてのプロパティの型では `NULL`。|  
|`NUMERIC_SCALE`|`DBTYPE_I2`||メジャー オブジェクトの型インジケーターが `DBTYPE_NUMERIC` または `DBTYPE_DECIMAL` である場合は、小数点以下の桁数になります。 それ以外の場合、この値は `NULL` になります。|  
|`MEASURE_UNITS`|`DBTYPE_WSTR`||サポートされていません|  
|`DESCRIPTION`|`DBTYPE_WSTR`||メジャーの人間が判読できる説明。 説明が存在しない場合は `NULL` になります。|  
|`EXPRESSION`|`DBTYPE_WSTR`||メンバーの式。|  
|`MEASURE_IS_VISIBLE`|`DBTYPE_BOOL`||常に True を返すブール値。 メジャーが表示されてない場合は、スキーマ行セットに含まれません。|  
|`LEVELS_LIST`|`DBTYPE_WSTR`||常に `NULL` を返す文字列。|  
|`MEASURE_NAME_SQL_COLUMN_NAME`|`DBTYPE_WSTR`||メジャー名に対応する SQL クエリ内の列名。|  
|`MEASURE_UNQUALIFIED_CAPTION`|`DBTYPE_WSTR`||メジャー グループ名で修飾されていないメジャー名。|  
|`MEASUREGROUP_NAME`|`DBTYPE_WSTR`||このメジャーが所属するメジャー グループの名前。|  
|`MEASURE_DISPLAY_FOLDER`|`DBTYPE_WSTR`||ユーザー インターフェイスでのメジャーの表示に使用するパス。 フォルダー名はセミコロンで区切られます。 入れ子になったフォルダーは円記号で示されます (\\)。|  
|`DEFAULT_FORMAT_STRING`|`DBTYPE_WSTR`||メジャーの既定の書式設定文字列。|  
  
 行セットは、`CATALOG_NAME`、`SCHEMA_NAME`、`CUBE_NAME`、`MEASURE_NAME` を基準に並べ替えることができます。  
  
## <a name="restriction-columns"></a>制限の列  
 `MDSCHEMA_MEASURES`行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|任意。|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|任意。|  
|`CUBE_NAME`|`DBTYPE_WSTR`|任意。|  
|`MEASURE_NAME`|`DBTYPE_WSTR`|任意。|  
|`MEASURE_UNIQUE_NAME`|`DBTYPE_WSTR`|任意。|  
|`MEASUREGROUP_NAME`|`DBTYPE_WSTR`|任意。|  
|`CUBE_SOURCE`|`DBTYPE_UI2`|(省略可) 次のいずれかの有効値を含むビットマップ。<br /><br /> -1 のキューブ<br />2 つのディメンション<br /><br /> 既定の制限の値は 1 です。|  
|`MEASURE_VISIBILITY`|`DBTYPE_UI2`|(省略可) 次のいずれかの有効値を含むビットマップ。<br /><br /> -1 の表示<br />-2 非表示<br /><br /> 既定の制限の値は 1 です。|  
  
## <a name="see-also"></a>参照  
 [OLE DB for OLAP Schema 行セット](ole-db-for-olap-schema-rowsets.md)  
  
  
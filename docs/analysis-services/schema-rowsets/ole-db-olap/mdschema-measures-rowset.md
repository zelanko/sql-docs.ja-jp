---
title: "MDSCHEMA_MEASURES 行セット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: schema-rowsets
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: MDSCHEMA_MEASURES
apitype: NA
applies_to: SQL Server 2016 Preview
helpviewer_keywords: MDSCHEMA_MEASURES rowset
ms.assetid: 6ff5bd1a-aad0-49b8-9f8d-7df2637caacf
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: b6e2e862d6ad09659a19ce60498e2f5f06810eb2
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="mdschemameasures-rowset"></a>MDSCHEMA_MEASURES 行セット
  キューブ内の各メジャーについて記述します。  
  
## <a name="rowset-columns"></a>行セットの列  
 **MDSCHEMA_MEASURES**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|Description|  
|-----------------|--------------------|------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**||このメジャーが所属するカタログの名前。 **NULL**プロバイダーがカタログをサポートしていない場合。|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**||このメジャーが属するスキーマの名前。 **NULL**プロバイダーがスキーマをサポートしていない場合。|  
|**CUBE_NAME**|**DBTYPE_WSTR**||このメジャーが所属するキューブの名前。|  
|**MEASURE_NAME**|**DBTYPE_WSTR**||メジャーの名前。|  
|**MEASURE_UNIQUE_NAME**|**DBTYPE_WSTR**||メジャーの一意の名前。 修飾によって一意な名前を生成するプロバイダーの場合、この名前の各コンポーネントは区切り記号付きです。|  
|**MEASURE_CAPTION**|**DBTYPE_WSTR**||メジャーに関連付けられたラベルまたはキャプション。 主に表示のために使用されます。 キャプションが存在しない場合**MEASURE_NAME**が返されます。|  
|**MEASURE_GUID**|**DBTYPE_GUID 型**||サポートされていません。|  
|**MEASURE_AGGREGATOR**|**DBTYPE_I4**||メジャーがどのように派生したかを識別する列挙。 次の値のいずれかです。<br /><br /> **MDMEASURE_AGGR_SUM** (**1**) からメジャーを集計することを識別**合計**です。<br /><br /> **MDMEASURE_AGGR_COUNT** (**2**) からメジャーを集計することを識別**カウント**です。<br /><br /> **MDMEASURE_AGGR_MIN** (**3**) からメジャーを集計することを識別**MIN**です。<br /><br /> **MDMEASURE_AGGR_MAX** (**4**) からメジャーを集計することを識別**MAX**です。<br /><br /> **MDMEASURE_AGGR_AVG** (**5**) からメジャーを集計することを識別**AVG**です。<br /><br /> **MDMEASURE_AGGR_VAR** (**6**) からメジャーを集計することを識別**VAR**です。<br /><br /> **MDMEASURE_AGGR_STD** (**7**) からメジャーを集計することを識別**STDEV**です。<br /><br /> **MDMEASURE_AGGR_DST** (**8**) からメジャーを集計することを識別**個別のカウント**です。<br /><br /> **MDMEASURE_AGGR_NONE** (**9**) からメジャーを集計することを識別**NONE**です。<br /><br /> **MDMEASURE_AGGR_AVGCHILDREN** (**10**) からメジャーを集計することを識別**AVERAGEOFCHILDREN**です。<br /><br /> **MDMEASURE_AGGR_FIRSTCHILD** (**11**) からメジャーを集計することを識別**FIRSTCHILD**です。<br /><br /> **MDMEASURE_AGGR_LASTCHILD** (**12**) からメジャーを集計することを識別**LASTCHILD**です。<br /><br /> **MDMEASURE_AGGR_FIRSTNONEMPTY** (**13**) からメジャーを集計することを識別**FIRSTNONEMPTY**、<br /><br /> **MDMEASURE_AGGR_LASTNONEMPTY** (**14**) からメジャーを集計することを識別**LASTNONEMPTY**です。<br /><br /> **MDMEASURE_AGGR_BYACCOUNT** (**15**) からメジャーを集計することを識別**BYACCOUNT**です。<br /><br /> **MDMEASURE_AGGR_CALCULATED** (**127**) が使用されて記の関数式からメジャーが派生したことを識別します。<br /><br /> **MDMEASURE_AGGR_UNKNOWN** (**0**)、不明な集計関数または式からメジャーが派生したことを識別します。|  
|**DATA_TYPE**|**DBTYPE_UI2**||メジャーのデータ型。|  
|**NUMERIC_PRECISION**|**DBTYPE_UI2**||メジャー オブジェクトのデータ型が真数の場合は、プロパティの最大有効桁数。 **NULL**の他のすべてのプロパティの型。|  
|**NUMERIC_SCALE**|**DBTYPE_I2**||メジャー オブジェクトの型インジケーターがある場合、小数点の右側にある数字の数**DBTYPE_NUMERIC**または**DBTYPE_DECIMAL**です。 この値は、それ以外の場合、 **NULL**です。|  
|**MEASURE_UNITS**|**DBTYPE_WSTR**||サポートされていません|  
|**DESCRIPTION**|**DBTYPE_WSTR**||メジャーの人間が判読できる説明。 **NULL**説明が存在しない場合。|  
|**式**|**DBTYPE_WSTR**||メンバーの式。|  
|**MEASURE_IS_VISIBLE**|**DBTYPE_BOOL**||常に True を返すブール値。 メジャーが表示されてない場合は、スキーマ行セットに含まれません。|  
|**LEVELS_LIST**|**DBTYPE_WSTR**||常に返す文字列**NULL**です。|  
|**MEASURE_NAME_SQL_COLUMN_NAME**|**DBTYPE_WSTR**||メジャー名に対応する SQL クエリ内の列名。|  
|**MEASURE_UNQUALIFIED_CAPTION**|**DBTYPE_WSTR**||メジャー グループ名で修飾されていないメジャー名。|  
|**MEASUREGROUP_NAME**|**DBTYPE_WSTR**||このメジャーが所属するメジャー グループの名前。|  
|**MEASURE_DISPLAY_FOLDER**|**DBTYPE_WSTR**||ユーザー インターフェイスでのメジャーの表示に使用するパス。 フォルダー名はセミコロンで区切られます。 入れ子になったフォルダーは円記号で示されます (\\)。|  
|**DEFAULT_FORMAT_STRING**|**DBTYPE_WSTR**||メジャーの既定の書式設定文字列。|  
  
 行セットが並べ替えられて**CATALOG_NAME**、 **SCHEMA_NAME**、 **CUBE_NAME**、 **MEASURE_NAME**です。  
  
## <a name="restriction-columns"></a>制限の列  
 **MDSCHEMA_MEASURES**行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|省略可。|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|省略可。|  
|**CUBE_NAME**|**DBTYPE_WSTR**|省略可。|  
|**MEASURE_NAME**|**DBTYPE_WSTR**|省略可。|  
|**MEASURE_UNIQUE_NAME**|**DBTYPE_WSTR**|省略可。|  
|**MEASUREGROUP_NAME**|**DBTYPE_WSTR**|省略可。|  
|**CUBE_SOURCE**|**DBTYPE_UI2**|(省略可能)既定の制限は、1 の値です。 有効な値は次のいずれかのビットマップ。<br /><br /> 1 キューブ<br /><br /> 2 ディメンション|  
|**MEASURE_VISIBILITY**|**DBTYPE_UI2**|(省略可能)既定の制限は、1 の値です。 有効な値は次のいずれかのビットマップ。<br /><br /> 1 表示<br /><br /> 2 非表示|  
  
## <a name="see-also"></a>参照  
 [OLE DB for OLAP Schema 行セット](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  

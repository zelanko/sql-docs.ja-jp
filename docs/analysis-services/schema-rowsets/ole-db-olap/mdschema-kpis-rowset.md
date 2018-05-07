---
title: MDSCHEMA_KPIS 行セット |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bbf191fafa07bbc436c9971a5c16f4fb455f78bd
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="mdschemakpis-rowset"></a>MDSCHEMA_KPIS 行セット
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  データベース内の主要業績評価指標 (KPI) について記述します。  
  
## <a name="rowset-columns"></a>行セットの列  
 **MDSCHEMA_KPIS**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|Description|  
|-----------------|--------------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|ソース データベース。|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|サポートされていません。|  
|**CUBE_NAME**|**DBTYPE_WSTR**|KPI の親キューブ。|  
|**MEASUREGROUP_NAME**|**DBTYPE_WSTR**|KPI の関連メジャー グループ。<br /><br /> この列を使用して、KPI の次元を決定できます。 場合"**\<NULL >**"、KPI のすべてのメジャー グループでディメンションになります。<br /><br /> 既定値は"**\<NULL >**"です。|  
|**KPI 名**|**DBTYPE_WSTR**|KPI の名前。|  
|**KPI_CAPTION**|**DBTYPE_WSTR**|KPI に関連付けられたラベルまたはキャプション。 主に表示のために使用されます。 キャプションが存在しない場合**KPI_NAME**が返されます。|  
|**KPI_DESCRIPTION**|**DBTYPE_WSTR**|KPI に関して人が認識できる説明。|  
|**KPI_DISPLAY_FOLDER**|**DBTYPE_WSTR**|メンバーを表示するためにクライアント アプリケーションが使用する、表示フォルダーのパスを識別する文字列です。 フォルダー レベルの区切り記号は、クライアント アプリケーションによって定義されます。 ツールおよびクライアントによって提供される[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]、円記号 (\\) は、レベルの区切り記号。 複数の表示フォルダーを指定するには、セミコロン (;) を使用して、フォルダーを区切ります。|  
|**KPI_VALUE**|**DBTYPE_WSTR**|KPI 値のメジャー ディメンションに含まれるメンバーの一意の名前。|  
|**KPI_GOAL**|**DBTYPE_WSTR**|KPI 目標のメジャー ディメンションに含まれるメンバーの一意の名前。<br /><br /> 返します**NULL**かどうかは、目標の定義はありません。|  
|**KPI_STATUS**|**DBTYPE_WSTR**|KPI 状態のメジャー ディメンションに含まれるメンバーの一意の名前。<br /><br /> 返します**NULL**かどうかは、定義されている状態はありません。|  
|**KPI_TREND**|**DBTYPE_WSTR**|KPI 傾向のメジャー ディメンションに含まれるメンバーの一意の名前。<br /><br /> 返します**NULL**かどうかは、傾向が定義はありません。|  
|**KPI_STATUS_GRAPHIC**|**DBTYPE_WSTR**|KPI の既定のグラフィカル表現。|  
|**KPI_TREND_GRAPHIC**|**DBTYPE_WSTR**|KPI の既定のグラフィカル表現。|  
|**KPI_WEIGHT**|**DBTYPE_WSTR**|KPI 重みのメジャー ディメンションに含まれるメンバーの一意の名前。|  
|**KPI_CURRENT_TIME_MEMBER**|**DBTYPE_WSTR**|KPI の時間的コンテキストを定義する時間ディメンションに含まれるメンバーの一意の名前。<br /><br /> 返します**NULL**かどうかは、定義される時間メンバーはありません。|  
|**KPI_PARENT_KPI_NAME**|**DBTYPE_WSTR**|親 KPI の名前。|  
|**スコープ**|**DBTYPE_I4**|KPI のスコープ。 KPI は、セッション KPI またはグローバル KPI です。<br /><br /> この列は、次のいずれかの値になります。<br /><br /> MDKPI_SCOPE_GLOBAL=1<br /><br /> MDKPI_SCOPE_SESSION=2|  
|**注釈**|**DBTYPE_WSTR**|(省略可) XML 形式のメモのセット。|  
  
 このスキーマ行セットは並べ替えられません。  
  
## <a name="restriction-columns"></a>制限の列  
 **MDSCHEMA_KPIS**行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|省略可。|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|省略可。|  
|**CUBE_NAME**|**DBTYPE_WSTR**|省略可。|  
|**KPI 名**|**DBTYPE_WSTR**|省略可。|  
|**CUBE_SOURCE**|**DBTYPE_UI2**|(省略可能)既定の制限の値は**1**です。 有効な値は次のいずれかのビットマップ。<br /><br /> **1**キューブ<br /><br /> **2**ディメンション|  
  
## <a name="see-also"></a>参照  
 [OLE DB for OLAP スキーマ行セット](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  

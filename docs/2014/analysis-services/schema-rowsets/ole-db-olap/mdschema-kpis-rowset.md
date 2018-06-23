---
title: MDSCHEMA_KPIS 行セット |Microsoft ドキュメント
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
- MDSCHEMA_KPIS
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_KPIS rowset
ms.assetid: 40fb5112-6a90-4455-82b3-8b6322490222
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 28a5f4af179c058f822a773dc691383dbee028fd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36177854"
---
# <a name="mdschemakpis-rowset"></a>MDSCHEMA_KPIS 行セット
  データベース内の主要業績評価指標 (KPI) について記述します。  
  
## <a name="rowset-columns"></a>行セットの列  
 `MDSCHEMA_KPIS`行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|説明|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||ソース データベース。|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||サポートされていません。|  
|`CUBE_NAME`|`DBTYPE_WSTR`||KPI の親キューブ。|  
|`MEASUREGROUP_NAME`|`DBTYPE_WSTR`||KPI の関連メジャー グループ。<br /><br /> この列を使用して、KPI の次元を決定できます。 場合"**\<NULL >**"、KPI のすべてのメジャー グループでディメンションになります。<br /><br /> 既定値は"**\<NULL >**"です。|  
|`KPI_NAME`|`DBTYPE_WSTR`||KPI の名前。|  
|`KPI_CAPTION`|`DBTYPE_WSTR`||KPI に関連付けられたラベルまたはキャプション。 主に表示のために使用されます。 キャプションが存在しない場合`KPI_NAME`が返されます。|  
|`KPI_DESCRIPTION`|`DBTYPE_WSTR`||KPI に関して人が認識できる説明。|  
|`KPI_DISPLAY_FOLDER`|`DBTYPE_WSTR`||メンバーを表示するためにクライアント アプリケーションが使用する、表示フォルダーのパスを識別する文字列です。 フォルダー レベルの区切り記号は、クライアント アプリケーションによって定義されます。 ツールおよびクライアントによって提供される[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]、円記号 (\\) は、レベルの区切り記号。 複数の表示フォルダーを指定するには、セミコロン (;) を使用して、フォルダーを区切ります。|  
|`KPI_VALUE`|`DBTYPE_WSTR`||KPI 値のメジャー ディメンションに含まれるメンバーの一意の名前。|  
|`KPI_GOAL`|`DBTYPE_WSTR`||KPI 目標のメジャー ディメンションに含まれるメンバーの一意の名前。<br /><br /> 目標が定義されていない場合は、`NULL` を返します。|  
|`KPI_STATUS`|`DBTYPE_WSTR`||KPI 状態のメジャー ディメンションに含まれるメンバーの一意の名前。<br /><br /> 状態が定義されていない場合は、`NULL` を返します。|  
|`KPI_TREND`|`DBTYPE_WSTR`||KPI 傾向のメジャー ディメンションに含まれるメンバーの一意の名前。<br /><br /> 傾向が定義されていない場合は、`NULL` を返します。|  
|`KPI_STATUS_GRAPHIC`|`DBTYPE_WSTR`||KPI の既定のグラフィカル表現。|  
|`KPI_TREND_GRAPHIC`|`DBTYPE_WSTR`||KPI の既定のグラフィカル表現。|  
|`KPI_WEIGHT`|`DBTYPE_WSTR`||KPI 重みのメジャー ディメンションに含まれるメンバーの一意の名前。|  
|`KPI_CURRENT_TIME_MEMBER`|`DBTYPE_WSTR`||KPI の時間的コンテキストを定義する時間ディメンションに含まれるメンバーの一意の名前。<br /><br /> 時間メンバーが定義されていない場合は、`NULL` を返します。|  
|`KPI_PARENT_KPI_NAME`|`DBTYPE_WSTR`||親 KPI の名前。|  
|`SCOPE`|`DBTYPE_I4`||KPI のスコープ。 KPI は、セッション KPI またはグローバル KPI です。<br /><br /> この列は、次のいずれかの値になります。<br /><br /> -MDKPI_SCOPE_GLOBAL = 1<br />-MDKPI_SCOPE_SESSION = 2|  
|`ANNOTATIONS`|`DBTYPE_WSTR`||(省略可) XML 形式のメモのセット。|  
  
 このスキーマ行セットは並べ替えられません。  
  
## <a name="restriction-columns"></a>制限の列  
 `MDSCHEMA_KPIS`行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|任意。|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|任意。|  
|`CUBE_NAME`|`DBTYPE_WSTR`|任意。|  
|`KPI_NAME`|`DBTYPE_WSTR`|任意。|  
|`CUBE_SOURCE`|`DBTYPE_UI2`|(省略可) 次のいずれかの有効値を含むビットマップ。<br /><br /> -   `1` キューブ<br />-   `2` ディメンション<br /><br /> 既定の制限の値は `1` です。|  
  
## <a name="see-also"></a>参照  
 [OLE DB for OLAP Schema 行セット](ole-db-for-olap-schema-rowsets.md)  
  
  
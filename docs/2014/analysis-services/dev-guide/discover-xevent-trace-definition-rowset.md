---
title: DISCOVER_XEVENT_TRACE_DEFINITION 行セット |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: e1ce2d2d-f994-4318-801a-ee0385aecd84
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 826389eafb4fdf6a32e8d3b62ebfc1f333b62d4d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62731914"
---
# <a name="discover_xevent_trace_definition-rowset"></a>DISCOVER_XEVENT_TRACE_DEFINITION 行セット
  サーバー上で現在アクティブになっている XEvent トレースに関する情報を提供します。  
  
 **適用対象:** テーブルモデル、多次元モデル  
  
## <a name="rowset-columns"></a>行セットの列  
 行`DISCOVER_XEVENT_TRACE_DEFINITION`セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|Length|[説明]|  
|-----------------|--------------------|------------|-----------------|  
|`Data`|`DBTYPE_WSTR`||XEvent トレースの XML 定義。|  
  
 このスキーマ行セットは並べ替えられません。  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>ADOMD.NET を使用した行セットのリターン  
 ADOMD.NET とスキーマ行セットを使用してメタデータを取得する場合、GetSchemaDataSet メソッドで GUID または文字列を使用してスキーマ行セット オブジェクトを参照できます。 詳細については、「 [Working with Schema Rowsets in ADOMD.NET](https://docs.microsoft.com/bi-reference/adomd/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets)」を参照してください。  
  
 次の表に、この行セットを識別する GUID と文字列の値を示します。  
  
|引数|Value|  
|--------------|-----------|  
|GUID|a07ccd1c-8148-11d0-87bb-00c04fc33942|  
|String|DISCOVER_XEVENT_TRACE_DEFINITION|  
  
## <a name="see-also"></a>参照  
 [XML for Analysis スキーマ行セット](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/xml-for-analysis-schema-rowsets)   
 [SQL Server 拡張イベント &#40;Xevent&#41; を使用して監視 Analysis Services](../instances/monitor-analysis-services-with-sql-server-extended-events.md)   
 [Dmv&#41; &#40;動的管理ビューを使用して Analysis Services を監視する](../instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)  
  
  

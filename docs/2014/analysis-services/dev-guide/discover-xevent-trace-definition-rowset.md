---
title: DISCOVER_XEVENT_TRACE_DEFINITION 行セット |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: e1ce2d2d-f994-4318-801a-ee0385aecd84
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cc223ec3ef09b791772a42134f2c71c73245507a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48171212"
---
# <a name="discoverxeventtracedefinition-rowset"></a>DISCOVER_XEVENT_TRACE_DEFINITION 行セット
  サーバー上で現在アクティブになっている XEvent トレースに関する情報を提供します。  
  
 **適用対象:** 表形式モデル、多次元モデル  
  
## <a name="rowset-columns"></a>行セットの列  
 `DISCOVER_XEVENT_TRACE_DEFINITION`行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|説明|  
|-----------------|--------------------|------------|-----------------|  
|`Data`|`DBTYPE_WSTR`||XEvent トレースの XML 定義。|  
  
 このスキーマ行セットは並べ替えられません。  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>ADOMD.NET を使用した行セットのリターン  
 ADOMD.NET とスキーマ行セットを使用してメタデータを取得する場合、GetSchemaDataSet メソッドで GUID または文字列を使用してスキーマ行セット オブジェクトを参照できます。 詳細については、「 [Working with Schema Rowsets in ADOMD.NET](../multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md)」を参照してください。  
  
 次の表に、この行セットを識別する GUID と文字列の値を示します。  
  
|引数|値|  
|--------------|-----------|  
|GUID|a07ccd1c-8148-11d0-87bb-00c04fc33942|  
|String|DISCOVER_XEVENT_TRACE_DEFINITION|  
  
## <a name="see-also"></a>参照  
 [XML for Analysis スキーマ行セット](../schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)   
 [SQL Server 拡張イベントを使用して、 &#40;Xevent&#41;サービス モニターは分析するには](../instances/monitor-analysis-services-with-sql-server-extended-events.md)   
 [動的管理ビューを使用して&#40;Dmv&#41;サービス モニターは分析するには](../instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)  
  
  

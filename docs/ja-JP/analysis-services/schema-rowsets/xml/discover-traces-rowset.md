---
title: DISCOVER_TRACES 行セット |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 1be6a035-ffc9-489e-9d4d-7391b3e384e2
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: b32ae25f17cded9f395b7d48e6ae0f9db4dde7b6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="discovertraces-rowset"></a>DISCOVER_TRACES 行セット
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  サーバー上で現在アクティブになっているトレースに関する情報を提供します。  
  
 **適用されます:** 表形式モデル、多次元モデル  
  
## <a name="rowset-columns"></a>行セットの列  
 **DISCOVER_TRACES**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|Description|  
|-----------------|--------------------|-----------------|  
|**TraceID**|**DBTYPE_WSTR**|トレース ID です。|  
|**TraceName**|**DBTYPE_WSTR**|トレース名です。|  
|**LogFileName**|**DBTYPE_WSTR**|トレース ログ ファイルの名前です。|  
|**LogFileSize**|**DBTYPE_I4**|トレース ログ ファイルのサイズです。|  
|**LogFileRollover**|**DBTYPE_BOOL**|true の場合、ログ ファイルをロールオーバーする必要があることを示します。それ以外の場合は false です。|  
|**AutoRestart**|**DBTYPE_BOOL**|true の場合、自動再起動オプションが有効になっていることを示します。それ以外の場合は false です。|  
|**CreationTime**|**DBTYPE_TIME 型**|トレースが作成された日付と時刻です。|  
|**StopTime**|**DBTYPE_TIME 型**|トレースの停止時刻です。|  
|**型**|**PF_DBTYPE_WSTR**|トレースの種類です。|  
  
 このスキーマ行セットは並べ替えられません。  
  
## <a name="restriction-columns"></a>制限の列  
 **DISCOVER_TRACES**行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|**TraceId**|**DBTYPE_I4**|省略可。|  
|**型**|WSTR|省略可。|  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>ADOMD.NET を使用した行セットのリターン  
 ADOMD.NET とスキーマ行セットを使用してメタデータを取得する場合、GetSchemaDataSet メソッドで GUID または文字列を使用してスキーマ行セット オブジェクトを参照できます。 詳細については、「 [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md)」を参照してください。  
  
 次の表に、この行セットを識別する GUID と文字列の値を示します。  
  
|引数|値|  
|--------------|-----------|  
|GUID|a07ccd1a-8148-11d0-87bb-00c04fc33942|  
|文字列|DISCOVER_TRACES|  
  
## <a name="see-also"></a>参照  
 [XML for Analysis スキーマ行セット](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  

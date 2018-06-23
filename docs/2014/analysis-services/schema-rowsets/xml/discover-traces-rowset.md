---
title: DISCOVER_TRACES 行セット |Microsoft ドキュメント
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
ms.assetid: 1be6a035-ffc9-489e-9d4d-7391b3e384e2
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 7b3c8428b34a72f16986044db1652b9907384b07
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36165334"
---
# <a name="discovertraces-rowset"></a>DISCOVER_TRACES 行セット
  サーバー上で現在アクティブになっているトレースに関する情報を提供します。  
  
 **適用されます:** 表形式モデル、多次元モデル  
  
## <a name="rowset-columns"></a>行セットの列  
 `DISCOVER_TRACES`行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|説明|  
|-----------------|--------------------|-----------------|  
|`TraceID`|`DBTYPE_WSTR`|トレース ID です。|  
|`TraceName`|`DBTYPE_WSTR`|トレース名です。|  
|`LogFileName`|`DBTYPE_WSTR`|トレース ログ ファイルの名前です。|  
|`LogFileSize`|`DBTYPE_I4`|トレース ログ ファイルのサイズです。|  
|`LogFileRollover`|`DBTYPE_BOOL`|true の場合、ログ ファイルをロールオーバーする必要があることを示します。それ以外の場合は false です。|  
|`AutoRestart`|`DBTYPE_BOOL`|true の場合、自動再起動オプションが有効になっていることを示します。それ以外の場合は false です。|  
|`CreationTime`|`DBTYPE_TIME`|トレースが作成された日付と時刻です。|  
|`StopTime`|`DBTYPE_TIME`|トレースの停止時刻です。|  
|`Type`|`PF_DBTYPE_WSTR`|トレースの種類です。|  
  
 このスキーマ行セットは並べ替えられません。  
  
## <a name="restriction-columns"></a>制限の列  
 `DISCOVER_TRACES`行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|**TraceId**|`DBTYPE_I4`|任意。|  
|`Type`|WSTR|任意。|  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>ADOMD.NET を使用した行セットのリターン  
 ADOMD.NET とスキーマ行セットを使用してメタデータを取得する場合、GetSchemaDataSet メソッドで GUID または文字列を使用してスキーマ行セット オブジェクトを参照できます。 詳細については、「 [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md)」を参照してください。  
  
 次の表に、この行セットを識別する GUID と文字列の値を示します。  
  
|引数|値|  
|--------------|-----------|  
|GUID|a07ccd1a-8148-11d0-87bb-00c04fc33942|  
|String|DISCOVER_TRACES|  
  
## <a name="see-also"></a>参照  
 [XML for Analysis Schema 行セット](xml-for-analysis-schema-rowsets.md)  
  
  
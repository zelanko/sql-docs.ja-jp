---
title: DISCOVER_TRACE_EVENT_CATEGORIES 行セット |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 1ad74fd2-4740-469d-85b5-abf0171737fd
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4d5771be15bf30b7cd5d478281ff9d859c354f4d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48140162"
---
# <a name="discovertraceeventcategories-rowset"></a>DISCOVER_TRACE_EVENT_CATEGORIES 行セット
  トレース プロバイダーによってサポートされているイベント カテゴリの一覧を表示します。  
  
 **適用対象:** 表形式モデル、多次元モデル  
  
## <a name="rowset-columns"></a>行セットの列  
 `DISCOVER_TRACE_EVENT_CATEGORIES`行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|説明|  
|-----------------|--------------------|------------|-----------------|  
|`Data`|`DBTYPE_WSTR`||カテゴリの名前、型、説明などのトレース プロバイダーに関するイベント カテゴリ情報を説明するエンコードされた XML 文字列を格納します。 型は、イベント カテゴリの型を示す文字列です。 列挙値は次のとおりです。<br /><br /> -0 = 標準<br />-1 = 有効<br />-2 = エラー|  
  
 このスキーマ行セットは並べ替えられません。  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>ADOMD.NET を使用した行セットのリターン  
 ADOMD.NET とスキーマ行セットを使用してメタデータを取得する場合、GetSchemaDataSet メソッドで GUID または文字列を使用してスキーマ行セット オブジェクトを参照できます。 詳細については、「 [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md)」を参照してください。  
  
 次の表に、この行セットを識別する GUID と文字列の値を示します。  
  
|引数|値|  
|--------------|-----------|  
|GUID|a07ccd19-8148-11d0-87bb-00c04fc33942|  
|String|DISCOVER_TRACE_EVENT_CATEGORIES|  
  
## <a name="see-also"></a>参照  
 [XML for Analysis Schema 行セット](xml-for-analysis-schema-rowsets.md)  
  
  

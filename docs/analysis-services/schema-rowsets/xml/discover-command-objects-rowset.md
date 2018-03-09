---
title: "DISCOVER_COMMAND_OBJECTS 行セット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords: DISCOVER_COMMAND_OBJECTS rowset
ms.assetid: 325114ee-3a50-4504-9782-dbf7c1a44778
caps.latest.revision: "21"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 7f97592e50485bdd26c55eb62fb9b4649acb545b
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="discovercommandobjects-rowset"></a>DISCOVER_COMMAND_OBJECTS 行セット
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]参照先のコマンドによって使用中のオブジェクトに関するリソース使用状況とアクティビティ情報を提供します。  
  
 **適用されます:**表形式モデル、多次元モデル  
  
## <a name="rowset-columns"></a>行セットの列  
 **DISCOVER_COMMAND_OBJECTS**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|制限|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|**SESSION_SPID**|**DBTYPE_I4**|可|セッション ID。|  
|**SESSION_ID**|**DBTYPE_WSTR**|可|GUID としてのセッションの一意識別子。|  
|**SESSION_COMMAND_COUNT**|**DBTYPE_I4**||コマンドのシーケンス番号。|  
|**OBJECT_PARENT_PATH**|**DBTYPE_WSTR**|可|現在のオブジェクトの親へのパス。|  
|**OBJECT_ID**|**DBTYPE_WSTR**|可|作成したときに定義されたオブジェクトの ID。|  
|**OBJECT_VERSION**|**DBTYPE_I4**||オブジェクトのメタデータ バージョン番号。この番号は、オブジェクトが変更されるたびに変わります。|  
|**OBJECT_DATA_VERSION**|**DBTYPE_I4**||オブジェクト内のデータの系列番号。 この番号は、オブジェクトが処理されるたびに増加します。|  
|**OBJECT_CPU_TIME_MS**|**DBTYPE_I8**||コマンドの開始以降にオブジェクトによって使用された CPU 時間 (ミリ秒単位)。|  
|**OBJECT_READ_KB**|**DBTYPE_I8**||コマンドの開始以降にオブジェクトによって読み取られたデータの累積値 (KB 単位)。|  
|**OBJECT_READS**|**DBTYPE_I8**||コマンドの開始以降にオブジェクトによって行われた読み取り操作の累積数。|  
|**OBJECT_WRITE_KB**|**DBTYPE_I8**||コマンドの開始以降にオブジェクトによって書き込まれたデータの累積値 (KB 単位)。|  
|**OBJECT_WRITES**|**DBTYPE_I8**||コマンドの開始以降にオブジェクトによって行われた書き込み操作の累積数。|  
|**OBJECT_ROWS_RETURNED**|**DBTYPE_I8**||コマンドの開始以降にオブジェクトによって呼び出し元に返された行数。|  
|**OBJECT_ROWS_SCANNED**|**DBTYPE_I8**||コマンドの開始以降にオブジェクトによってスキャンされた行数。|  
  
 このスキーマ行セットは並べ替えられません。  
  
> [!IMPORTANT]  
>  DISCOVER_COMMAND_OBJECTS スキーマ行セットは DMV クエリでは利用状況を報告しません。  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>ADOMD.NET を使用した行セットのリターン  
 ADOMD.NET とスキーマ行セットを使用してメタデータを取得する場合、GetSchemaDataSet メソッドで GUID または文字列を使用してスキーマ行セット オブジェクトを参照できます。 詳細については、「 [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md)」を参照してください。  
  
 次の表に、この行セットを識別する GUID と文字列の値を示します。  
  
|引数|値|  
|--------------|-----------|  
|GUID|a07ccd35-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|CommandObjects|  
  
## <a name="see-also"></a>参照  
 [XML for Analysis Schema 行セット](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  

---
title: DISCOVER_MEMORYUSAGE 行セット |Microsoft ドキュメント
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
ms.assetid: e416ea61-9615-468c-a96f-bbf731f803b1
caps.latest.revision: 7
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 832017b2efa7d1d788a74a20332160cffea63764
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="discovermemoryusage-rowset"></a>DISCOVER_MEMORYUSAGE 行セット
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  サーバーによって割り当てられているさまざまなオブジェクトの DISCOVER_MEMORYUSAGE 統計を返します。  
  
> [!WARNING]  
>  この行セットでは、非常に大きな結果セットが生成されることがあります。 SQL Server Management Studio によって許可されている量よりも多くの表示メモリを必要とするために結果を表示できない場合、次の既定の場所にある一時ファイルに結果が書き込まれます。  
>   
>  '\<ドライブ >: \Users\\< ユーザー名\>\AppData\Local\Temp\\< fileID\>.xml' です。  
  
 **適用されます:** 表形式モデル、多次元モデル  
  
## <a name="rowset-columns"></a>行セットの列  
 **DISCOVER_MEMORYUSAGE**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|制限|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|**MemoryID**|**DBTYPE_UI8**||メモリを識別する番号。|  
|**MemoryName**|**DBTYPE_WSTR**||メモリを所有しているオブジェクトの名前。|  
|**SPID**|**DBTYPE_UI4**|はい|メモリを割り当てたセッション。 ゼロは、メモリが特定のセッションに関連付けられていないことを意味します。|  
|**CreationTime**|**DBTYPE_DBTIMESTAMP**||"オブジェクトが作成された時刻" または "メモリが割り当てられた時刻"。|  
|**BaseObjectType**|**DBTYPE_UI4**|はい|オブジェクトの型を記述する番号です。 BaseObjectType が同じオブジェクトは同じ型になります。|  
|**MemoryUsed**|**DBTYPE_UI8**|はい|オブジェクトの現在のサイズです。オブジェクトが使用するために割り当てられているメモリよりも小さい場合があります。|  
|**MemoryAllocated**|**DBTYPE_UI8**||オブジェクトが使用するために割り当てられているメモリの量。オブジェクトが実際に使用するメモリの量よりも大きい場合があります。|  
|**MemoryAllocBase**|**DBTYPE_UI8**||オブジェクト自体に最初に割り当てられたバイト数 (オブジェクトのコンテンツに対する追加の割り当てを除く)。|  
|**MemoryAllocFromAlloc**|**DBTYPE_UI8**||このオブジェクトのコンテンツに割り当てられたメモリ。|  
|**ElementCount**|**DBTYPE_UI4**||コンテナー オブジェクトの場合、これはそのオブジェクトに含まれるオブジェクトの数です。|  
|**圧縮可能**|**DBTYPE_BOOL**|はい|メモリが圧縮可能かどうかを示すブール値 (メモリ不足により解放することができます)。 true の場合メモリは圧縮可能であり、false の場合メモリは圧縮不能です。|  
|**ObjectParentPath**|**DBTYPE_WSTR**||このオブジェクトの完全なパスを識別する文字列。|  
|**Exchange Spill**|**DBTYPE_WSTR**||オブジェクトを識別する文字列。 このオブジェクトの完全なパスが、文字列で表される: (ObjectParentPath + '.' + ObjectId)。|  
  
 このスキーマ行セットは並べ替えられません。  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>ADOMD.NET を使用した行セットのリターン  
 ADOMD.NET とスキーマ行セットを使用してメタデータを取得する場合、GetSchemaDataSet メソッドで GUID または文字列を使用してスキーマ行セット オブジェクトを参照できます。 詳細については、「 [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md)」を参照してください。  
  
 次の表に、この行セットを識別する GUID と文字列の値を示します。  
  
|引数|値|  
|--------------|-----------|  
|GUID|A07CCD21-8148-11D0-87BB-00C04FC33942|  
|ADOMDNAME|MemoryUsage|  
  
## <a name="see-also"></a>参照  
 [XML for Analysis スキーマ行セット](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  

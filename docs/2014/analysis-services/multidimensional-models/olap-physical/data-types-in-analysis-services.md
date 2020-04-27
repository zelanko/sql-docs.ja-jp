---
title: Analysis Services のデータ型 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 910be4f4-3010-41cd-9fdc-f0a79a0ce823
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4ecdc64918e582f25f0e017d263c66e78c0d1bee
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "62725386"
---
# <a name="data-types-in-analysis-services"></a>Analysis Services で使用するデータ型
  すべて<xref:Microsoft.AnalysisServices.DataItem>のオブジェクトに[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]ついて、は次`System.Data.OleDb.OleDbType`ののサブセットをサポートします。 データ型を設定または読み取るには、 [DataItem データ型 &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/data-type/dataitem-data-type-assl)を使用します。  
  
## <a name="supported-data-types"></a>サポートされるデータ型  
  
|||  
|-|-|  
|BigInt|64 ビットの符号付き整数です。 *BigInt*値型は、負の9223372036854775808から正の9223372036854775807までの範囲の値を持つ整数を表します。|  
|Binary|**バイト**型のバイナリデータのストリーム。 **Byte**は、0 ~ 255 の範囲の符号なし整数を表す値型です。|  
|ブール型|この型のインスタンスの値は、`true` または `false` のいずれかになります。|  
|通貨|-922337203685477.5808 から + 922337203685477.5807 までの範囲で、精度が通貨単位の10,000 分の 1 (小数点以下4桁) の*通貨*値。|  
|日付|日付と時刻データで、double として格納されます。 整数部分は 1899 年 12 月 30 日から起算した日数、小数部分は日の一部分 (時刻) を表します。|  
|Double|-1.79769313486232E +308 から 1.79769313486232E +308 までの範囲の浮動小数点数です。 Double 値は、最大有効桁数が 15 の 10 進数の数値情報を格納します。|  
|Integer|負の 2,147,483,648 から正の 2,147,483,647 までの符号付き整数値を表す、32 ビットの符号付き整数です。|  
|Single|-3.4028235E +38 から 3.4028235E +38 までの範囲の浮動小数点数です。 Single 値は、最大有効桁数が 7 の 10 進数の数値情報を格納します。|  
|Smallint|16 ビットの符号付き整数です。 *Smallint*値型は、負の32768から正の32767までの範囲の値を持つ符号付き整数を表します。|  
|Tinyint|8 ビットの符号付き整数です。 Tinyint 値型は、負の 128 から正の 127 までの整数値を表します。|  
|UnsignedBigInt|64 ビットの符号なし整数です。 *Unsignedbigint*値型は、0から18446744073709551615までの値を持つ符号なし整数を表します。|  
|UnsignedInt|32 ビットの符号なし整数です。 *Unsignedint*値型は、0 ~ 4294967295 の範囲の値を持つ符号なし整数を表します。|  
|UnsignedSmallInt|16 ビットの符号なし整数です。 *Unsignedsmallint*値型は、0 ~ 65535 の範囲の値を持つ符号なし整数を表します。|  
|UnsignedTinyInt|8 ビットの符号なし整数です。 *Unsignedtinyint*値型は、0 ~ 255 の範囲の符号なし整数を表します。|  
|WChar|Unicode 文字の NULL 終了ストリームです。 *WChar*は、テキストを表すために使用される Unicode 文字のシーケンシャルコレクションです。|  
  
## <a name="amo-validations-on-data-types"></a>データ型に対する AMO の検証  
 次の表は、特定のバインドに対して分析管理オブジェクト (AMO) が行う追加の検証を示しています。  
  
|オブジェクト|バインド|許可されるデータ型|  
|------------|-------------|------------------------|  
|DimensionAttribute|[KeyColumns]|Binary 以外のすべて|  
||NameColumn|WChar のみ|  
||SkippedLevelsColumn|BigInt、Integer、SmallInt、TinyInt、UnsignedBigInt、UnsignedInt、UnsignedSmallInt、UnsignedTinyInt の整数型のみ|  
||CustomRollupColumn|WChar のみ|  
||CustomRollupPropertiesColumn|WChar のみ|  
||UnaryOperatorColumn|WChar のみ|  
||ValueColumn|All|  
|AttributeTranslation|CaptionColumn|WChar のみ|  
|ScalarMiningStructureColumn|[KeyColumns]|Binary 以外のすべて|  
||NameColumn|WChar のみ|  
|TableMiningStructureColumn|ForeignKeyColumns|Binary 以外のすべて|  
|MeasureGroupAttribute|[KeyColumns]|Binary 以外のすべて|  
|個別のカウント メジャー|ソース|BigInt、Currency、Double、Integer、Single、SmallInt、TinyInt、UnsignedBigInt、UnsignedInt、UnsignedSmallInt、UnsignedTinyInt|  
  
  

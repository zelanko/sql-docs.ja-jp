---
title: Analysis Services でのデータ タイプ |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3b7ac934afdc086a50020e9ba22ca2d236ee091b
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34026269"
---
# <a name="data-types-in-analysis-services"></a>Analysis Services で使用するデータ型
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  すべての<xref:Microsoft.AnalysisServices.DataItem>オブジェクト、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]次のサブセットをサポートしている**System.Data.OleDb.OleDbType**です。 使用して設定またはデータ型を読み取る、 [DataItem データ型&#40;ASSL&#41;](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)です。  
  
## <a name="supported-data-types"></a>サポートされるデータ型  
  
|||  
|-|-|  
|BigInt|64 ビットの符号付き整数です。 *BigInt*値の型は整数を正 9,223,372,036,854,775,807 負 9,223,372,036,854,775,808 から範囲の値を表します。|  
|Binary|バイナリ データのストリーム**バイト**型です。 **バイト**は範囲 0 ~ 255 の値の符号なし整数を表す値の型。|  
|ブール値|この型のインスタンスは、いずれかの値を持つ**true**または**false**です。|  
|通貨|A*通貨*(小数点以下 4 桁) 通貨単位の 10,000 の精度で +922,337,203,685,477.5807-922,337,203,685,477.5808 から範囲の値。|  
|日付|日付と時刻データで、double として格納されます。 整数部分は 1899 年 12 月 30 日から起算した日数、小数部分は日の一部分 (時刻) を表します。|  
|Double|-1.79769313486232E +308 から 1.79769313486232E +308 までの範囲の浮動小数点数です。 Double 値は、最大有効桁数が 15 の 10 進数の数値情報を格納します。|  
|Integer|負の 2,147,483,648 から正の 2,147,483,647 までの符号付き整数値を表す、32 ビットの符号付き整数です。|  
|単一|-3.4028235E +38 から 3.4028235E +38 までの範囲の浮動小数点数です。 Single 値は、最大有効桁数が 7 の 10 進数の数値情報を格納します。|  
|Smallint|16 ビットの符号付き整数です。 *Smallint*値型は、負の 32768 から正の 32767 までの値を符号付き整数を表します。|  
|Tinyint|8 ビットの符号付き整数です。 Tinyint 値型は、負の 128 から正の 127 までの整数値を表します。|  
|UnsignedBigInt|64 ビットの符号なし整数です。 *UnsignedBigInt*値型は、0 から 18,446,744,073,709,551,615 までの値を符号なし整数を表します。|  
|UnsignedInt|32 ビットの符号なし整数です。 *UnsignedInt*値型は、0 から 4,294,967,295 までの値を符号なし整数を表します。|  
|UnsignedSmallInt|16 ビットの符号なし整数です。 *UnsignedSmallInt*値型は、0 から 65535 までの値を符号なし整数を表します。|  
|UnsignedTinyInt|8 ビットの符号なし整数です。 *UnsignedTinyInt*値型は、範囲 0 ~ 255 の値の符号なし整数を表します。|  
|WChar|Unicode 文字の NULL 終了ストリームです。 A *WChar*テキストを表現するために使用される Unicode 文字のシーケンシャル コレクションです。|  
  
## <a name="amo-validations-on-data-types"></a>データ型に対する AMO の検証  
 次の表は、特定のバインドに対して分析管理オブジェクト (AMO) が行う追加の検証を示しています。  
  
|オブジェクト|Binding|許可されるデータ型|  
|------------|-------------|------------------------|  
|DimensionAttribute|[KeyColumns]|Binary 以外のすべて|  
||NameColumn|WChar のみ|  
||SkippedLevelsColumn|BigInt、Integer、SmallInt、TinyInt、UnsignedBigInt、UnsignedInt、UnsignedSmallInt、UnsignedTinyInt の整数型のみ|  
||CustomRollupColumn|WChar のみ|  
||CustomRollupPropertiesColumn|WChar のみ|  
||UnaryOperatorColumn|WChar のみ|  
||ValueColumn|すべて|  
|AttributeTranslation|CaptionColumn|WChar のみ|  
|ScalarMiningStructureColumn|[KeyColumns]|Binary 以外のすべて|  
||NameColumn|WChar のみ|  
|TableMiningStructureColumn|ForeignKeyColumns|Binary 以外のすべて|  
|MeasureGroupAttribute|[KeyColumns]|Binary 以外のすべて|  
|個別のカウント メジャー|ソース|BigInt、Currency、Double、Integer、Single、SmallInt、TinyInt、UnsignedBigInt、UnsignedInt、UnsignedSmallInt、UnsignedTinyInt|  
  
  

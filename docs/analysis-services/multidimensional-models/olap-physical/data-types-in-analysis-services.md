---
title: Analysis Services でのデータ型 |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ea192588186f69adbc04ab6a56123206e1fb7817
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68208607"
---
# <a name="data-types-in-analysis-services"></a>Analysis Services で使用するデータ型
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  すべての<xref:Microsoft.AnalysisServices.DataItem>オブジェクト、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]のサブセットをサポート**System.Data.OleDb.OleDbType**します。 を設定またはデータ型を読み取るには、使用[DataItem データ型&#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/data-type/dataitem-data-type-assl)します。  
  
## <a name="supported-data-types"></a>サポートされるデータ型  
  
|||  
|-|-|  
|BigInt|64 ビット符号付き整数。 *BigInt*値の型は整数を正 9,223,372,036,854,775,807 負 9,223,372,036,854,775,808 から範囲の値を表します。|  
|Binary|バイナリ データ ストリーム**バイト**型。 **バイト**は 0 から 255 までの値の符号なし整数を表す値型です。|  
|ブール値|この型のインスタンスは、いずれかの値を持つ**true**または**false**します。|  
|通貨|A*通貨*通貨 (小数点以下 4 桁) 単位の 10,000 の精度で +922,337,203,685,477.5807 ~-922,337,203,685,477.5808 から範囲の値。|  
|date|日付と時刻データで、double として格納されます。 整数部分は 1899 年 12 月 30 日から起算した日数、小数部分は日の一部分 (時刻) を表します。|  
|Double|-1.79769313486232E +308 から 1.79769313486232E +308 までの範囲の浮動小数点数です。 Double 値は、最大有効桁数が 15 の 10 進数の数値情報を格納します。|  
|整数型|負の 2,147,483,648 から正の 2,147,483,647 までの符号付き整数値を表す、32 ビットの符号付き整数です。|  
|単一|-3.4028235E +38 から 3.4028235E +38 までの範囲の浮動小数点数です。 Single 値は、最大有効桁数が 7 の 10 進数の数値情報を格納します。|  
|Smallint|16 ビット符号付き整数。 *Smallint*値型は、負の 32768 から正の 32767 までの値を符号付き整数を表します。|  
|Tinyint|8 ビットの符号付き整数です。 Tinyint 値型は、負の 128 から正の 127 までの整数値を表します。|  
|UnsignedBigInt|64 ビット符号なし整数。 *UnsignedBigInt* 18,446,744,073,709,551,615 ~ 0 の範囲値を持つ値の型が符号なし整数を表します。|  
|UnsignedInt|32 ビット符号なし整数 *UnsignedInt* 4,294,967,295 ~ 0 の範囲値を持つ値の型が符号なし整数を表します。|  
|UnsignedSmallInt|16 ビット符号なし整数。 *UnsignedSmallInt*値型は、0 から 65535 までの値を符号なし整数を表します。|  
|UnsignedTinyInt|8 ビットの符号なし整数です。 *UnsignedTinyInt*値型は、0 から 255 までの値の符号なし整数を表します。|  
|WChar|Unicode 文字の NULL 終了ストリームです。 A *WChar*はテキストを表すために使用される Unicode 文字のシーケンシャル コレクション。|  
  
## <a name="amo-validations-on-data-types"></a>データ型に対する AMO の検証  
 次の表は、特定のバインドに対して分析管理オブジェクト (AMO) が行う追加の検証を示しています。  
  
|オブジェクト|Binding|許可されるデータ型|  
|------------|-------------|------------------------|  
|DimensionAttribute|[KeyColumns]|Binary 以外のすべて|  
||NameColumn|WChar のみ|  
||SkippedLevelsColumn|整数型のみ:BigInt、Integer、SmallInt、TinyInt、UnsignedBigInt、UnsignedInt、UnsignedSmallInt、UnsignedTinyInt|  
||CustomRollupColumn|WChar のみ|  
||CustomRollupPropertiesColumn|WChar のみ|  
||UnaryOperatorColumn|WChar のみ|  
||ValueColumn|All|  
|AttributeTranslation|CaptionColumn|WChar のみ|  
|ScalarMiningStructureColumn|[KeyColumns]|Binary 以外のすべて|  
||NameColumn|WChar のみ|  
|TableMiningStructureColumn|ForeignKeyColumns|Binary 以外のすべて|  
|MeasureGroupAttribute|[KeyColumns]|Binary 以外のすべて|  
|個別のカウント メジャー|Source|BigInt、Currency、Double、Integer、Single、SmallInt、TinyInt、UnsignedBigInt、UnsignedInt、UnsignedSmallInt、UnsignedTinyInt|  
  
  

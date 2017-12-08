---
title: "Analysis Services 表形式モデルでサポートされるデータ型 |Microsoft ドキュメント"
ms.custom: 
ms.date: 10/16/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 92993f7b-7243-4aec-906d-0b0379798242
caps.latest.revision: "16"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 79512ded963b6568346c261b69c100b77e03bc74
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="data-types-supported-in-tabular-models"></a>表形式モデルでサポートされるデータ型

[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  このトピックでは、テーブル モデルで使用できるデータ型について説明し、データが計算される場合または Data Analysis Expressions (DAX) の数式で使用される場合の暗黙的な変換についても解説します。  

  
##  <a name="bkmk_data_types"></a>テーブル モデルで使用されるデータ型  
データをインポートする場合や数式で値を使用する場合は、元のデータ ソースに別のデータ型が含まれていても、そのデータは次のデータ型のいずれかに変換されます。 数式で得られる結果の値にも、これらのデータ型が使用されます。  
  
 通常、これらのデータ型は、計算列で正確な計算を実行するために実装されます。一貫性を確保するために、同じ制限がモデルのその他のデータにも適用されます。  
  
 数値、通貨、日付と時刻に使用される形式は、モデル データの操作に使用されるクライアントで指定されているロケールの形式に従う必要があります。 モデルの書式設定オプションを使用して、値の表示方法を制御できます。  
  
||||  
|-|-|-|  
|**モデルでのデータ型**|**DAX のデータ型**|**Description**|  
|整数|64 ビット (8 バイト) の整数値*<br /><br /> 注:<br />         DAX の数式は、説明に示されている最小値を保持するには小さすぎるデータ型をサポートしません。|小数点以下を含まない数値。 整数は正の数値または負の数値のどちらも有効ですが、-9,223,372,036,854,775,808 (-2^63) ～ 9,223,372,036,854,775,807 (2^63-1) の範囲の整数でなければなりません。|  
|10 進数|64 ビット (8 バイト) の実数*<br /><br /> 注:<br />         DAX の数式は、説明に示されている最小値を保持するには小さすぎるデータ型をサポートしません。|小数点以下を含む数値。 実数では次のような幅広い値が有効です。<br /><br /> 負の値 (-1.79E +308 ～ -2.23E -308 の範囲)<br /><br /> Zero<br /><br /> 正の値 (2.23E -308 ～ 1.79E + 308 の範囲)<br /><br /> ただし、有効桁数は小数点以下が 17 桁に制限されます。|  
|ブール値|ブール値|True または False の値。|  
|テキスト|文字列|Unicode 文字データ文字列。 文字列、数値、またはテキスト形式で表現される日付を指定できます。|  
|日付|日付/時刻|許容された日付時刻表現による日付および時刻。<br /><br /> 1900 年 3 月 1 日より後のすべての日付が有効です。|  
|Currency|Currency|通貨データ型では、-922,337,203,685,477.5808 ～ 922,337,203,685,477.5807 の範囲の値 (小数点以下が 4 桁で有効桁数が固定長) が有効です。|  
|なし|空白|空白は、DAX では SQL の NULL に相当するデータ型です。 空白を作成するには BLANK 関数を使用し、空白かどうかをテストするには論理関数の ISBLANK を使用します。|  
  
 \*数値が大きいデータをインポートしようとすると、インポートが次のエラーで失敗する可能性があります。  
  
 メモリ内のデータベース エラー: '\<列名 >' の列、'\<テーブル名 >' テーブルには、値が含まれています。' 1.7976931348623157 e + 308' はサポートされていません。 操作が取り消されました。  
  
 このエラーは、モデル デザイナーがこの値を使用して NULL を表すために発生します。 次の一覧の値は、上で説明した NULL 値のシノニムです。  
  
||  
|-|  
|値|  
|9223372036854775807|  
|-9223372036854775808|  
|1.7976931348623158e+308|  
|2.2250738585072014e-308|  
  
 データから値を削除して、再度インポートします。  
  
> [!NOTE]  
>  131,072 文字を超える文字列を含む **varchar(max)** 列からインポートすることはできません。  
  
### <a name="table-data-type"></a>table データ型  
 また、DAX では *table* データ型を使用します。 このデータ型は、集計やタイム インテリジェンス計算など、DAX の多くの関数で使用されます。 一部の関数は、テーブルへの参照を受け取ります。また、他の関数の入力として使用できるテーブルを返す関数もあります。 入力としてテーブルを受け取る一部の関数では、テーブルに評価される式を指定できます。また、ベース テーブルへの参照を受け取る関数もあります。 特定の関数の要件については、「 [DAX 関数リファレンス](http://msdn.microsoft.com/en-us/4dbb28a1-dd1a-4fca-bcd5-e90f74864a7b)」を参照してください。  
  
##  <a name="bkmk_implicit"></a>DAX の数式で暗黙的および明示的なデータ型の変換
  
 各 DAX 関数には、入力および出力として使用するデータ型について固有の要件があります。 たとえば、一部の関数は、特定の引数に整数や日付の指定が必要です。テキストやテーブルの指定が必要な関数もあります。  
  
 引数として指定した列のデータは、関数に必要なデータ型と互換性がありません、DAX では、多くの場合は、エラーを返します。 ただし、任意の場所可能な DAX しようとデータに必要なデータ型に暗黙的に変換します。 例:  
  
-   数値 (たとえば "123") は、文字列として入力できます。 DAX では、文字列を解析し、数値データ型として指定しようとしています。  
  
-   TRUE + 1 では 2 が返されます。これは、TRUE が数値の 1 に暗黙的に変換され、1 + 1 という演算が実行されるためです。  
  
-   2 つの列内の値を加算する場合に、1 つの値がテキスト ("12") で表現され、他の値が数値 (12) で表現されているとき、DAX では文字列を数値に暗黙的に変換してから加算が実行され、数値の結果が得られます。 次の式では、44: = "22" + 22 が返されます。  
  
-   2 つの数値を連結しようとする場合は文字列として表示し、連結しています。 次の式では、"1234": = 12 &34;が返されます。  
  
 次の表に、数式で実行される暗黙的なデータ型変換をまとめました。 通常、セマンティック モデル デザイナーの動作は Microsoft Excel と似ていますが、指定された演算に必要な場合は可能な限り暗黙的な変換を実行します。  
  
### <a name="table-of-implicit-data-conversions"></a>テーブルなデータの暗黙的な変換  
 実行される変換のタイプは演算子によって決定され、要求された演算を実行する前に必要な値がキャストされます。 これらの表には演算子とデータ型が記載されていますが、列と行が交差するセルには、各データ型を組み合わせた場合に実行される変換が示されています。  
  
> [!NOTE]  
>  テキスト データ型はこれらの表には含まれていません。 場合によってでのテキスト形式で数値が表現されているときに、モデル デザイナーは、数値の種類を決定し、数値として表現を試みます。  
  
#### <a name="addition-"></a>加算 (+)  
  
||||||  
|-|-|-|-|-|  
|演算子 (+)|INTEGER|Currency|REAL|日付/時刻|  
|INTEGER|INTEGER|Currency|REAL|日付/時刻|  
|Currency|Currency|Currency|REAL|日付/時刻|  
|REAL|REAL|REAL|REAL|日付/時刻|  
|日付/時刻|日付/時刻|日付/時刻|日付/時刻|日付/時刻|  
  
 たとえば、加算演算で実数を通貨データと組み合わせて使用する場合、両方の値が実数に変換され、結果が実数として返されます。  
  
#### <a name="subtraction--"></a>減算 (-)  
 次の表に、行見出しは被減数 (左側) と列見出しは減数 (右側)。  
  
||||||  
|-|-|-|-|-|  
|演算子 (-)|INTEGER|Currency|REAL|日付/時刻|  
|INTEGER|INTEGER|Currency|REAL|REAL|  
|Currency|Currency|Currency|REAL|REAL|  
|REAL|REAL|REAL|REAL|REAL|  
|日付/時刻|日付/時刻|日付/時刻|日付/時刻|日付/時刻|  
  
 たとえば、減算演算で日付を他のデータ型と共に使用する場合、両方の値が日付に変換され、戻り値も日付になります。  
  
> [!NOTE]  
>  テーブル モデルでは、単項演算子の - (負号) もサポートされますが、この演算子はオペランドのデータ型を変更しません。  
  
#### <a name="multiplication-"></a>乗算 (*)  
  
||||||  
|-|-|-|-|-|  
|演算子 (*)|INTEGER|Currency|REAL|日付/時刻|  
|INTEGER|INTEGER|Currency|REAL|INTEGER|  
|Currency|Currency|REAL|Currency|Currency|  
|REAL|REAL|Currency|REAL|REAL|  
  
 たとえば、乗算演算で整数を実数と組み合わせて使用する場合、両方の数値が実数に変換され、戻り値も実数になります。  
  
#### <a name="division-"></a>除算 (/)  
 次の表では、行ヘッダーが分子で、列ヘッダーが分母です。  
  
||||||  
|-|-|-|-|-|  
|演算子 (/)<br /><br /> 行/列|INTEGER|Currency|REAL|日付/時刻|  
|INTEGER|REAL|Currency|REAL|REAL|  
|Currency|Currency|REAL|Currency|REAL|  
|REAL|REAL|REAL|REAL|REAL|  
|日付/時刻|REAL|REAL|REAL|REAL|  
  
 たとえば、除算演算で整数を通貨値と組み合わせて使用する場合、両方の値が実数に変換され、結果も実数になります。  
  
#### <a name="comparison-operators"></a>比較演算子  
比較操作の混合のデータ型の組み合わせの限定されたセットのみがサポートされています。 詳細については、「 [DAX 演算子リファレンス](https://msdn.microsoft.com/library/ee634237.aspx)」を参照してください。  
  
## <a name="bkmk_hand_blanks"></a>空白、空の文字列、およびゼロ値の処理  
 次の表には、空白が処理されるように DAX と Microsoft Excel での違いをまとめたものです。  
  
||||  
|-|-|-|  
|式|DAX|Excel|  
|BLANK + BLANK|空白|0 (ゼロ)|  
|BLANK + 5|5|5|  
|BLANK * 5|空白|0 (ゼロ)|  
|5/BLANK|無限大|[エラー]|  
|0 / BLANK|NaN|[エラー]|  
|BLANK / BLANK|空白|[エラー]|  
|FALSE OR BLANK|FALSE|FALSE|  
|FALSE AND BLANK|FALSE|FALSE|  
|TRUE OR BLANK|TRUE|TRUE|  
|TRUE AND BLANK|FALSE|TRUE|  
|BLANK OR BLANK|空白|[エラー]|  
|BLANK AND BLANK|空白|[エラー]|  
  
 特定の関数または演算子で空白を処理する方法の詳細については、「 [DAX 関数リファレンス](http://msdn.microsoft.com/en-us/4dbb28a1-dd1a-4fca-bcd5-e90f74864a7b)」セクションの各 DAX 関数のトピックを参照してください。  
  

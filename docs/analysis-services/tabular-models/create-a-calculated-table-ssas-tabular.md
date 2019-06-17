---
title: Analysis Services 表形式モデルでの計算テーブルの作成 |Microsoft Docs
ms.date: 12/19/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 199096efcdf9212e19e1055f1276079eddfb1a75
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62469374"
---
# <a name="create-a-calculated-table"></a>計算テーブルを作成します。 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  *計算テーブル* は、DAX クエリまたは式に基づいて計算されたオブジェクトで、同じモデル内の他のテーブルの全部または一部から派生しています。  
  
 計算テーブルで解決できる一般的な設計上の問題では、クライアント アプリケーションでクエリ構造として公開できるように、特定のコンテキストで多様ディメンションが表示されています。  多様ディメンションは、複数のコンテキストで表示される単なる 1 つのテーブルです。従来の例としては、外部キー関係に応じて OrderDate、ShipDate、または DueDate としてマニフェストされる Date テーブルなどがあります。 明示的に ShipDate 用の計算テーブルを作成すると、他のテーブルのように完全に操作可能なクエリに使用できるスタンドアロン テーブルが作成されます。 別の用途には、フィルター選択された行セット、サブセット、またはその他の既存のテーブルの列のスーパー セットの構成が含まれます。 これにより、元のテーブルを変更せずに保持しながら、特定のシナリオをサポートするテーブルのバリエーションを作成できます。  
  
 計算テーブルを最大限に活用するには、少なくとも DAX についてある程度理解している必要があります。 テーブルの式を操作するときは、計算テーブルに、式は、DAX 式を DAXSource の 1 つのパーティションが含まれているかを把握する役立つ可能性があります。  
式によって返される列ごとに 1 つの CalculatedTableColumn があります。SourceColumn は返される列の名前です (非計算テーブルの DataColumns に似ています)。 

少なくとも 1 つのテーブルには、計算テーブルを作成する前に存在する必要があります。 スタンドアロン計算テーブルのオブジェクトとして計算テーブルを作成する場合は、(csv、xls、xml) ファイルのデータ ソースからインポートすることでテーブルを作成することができます。 1 つの列と 1 つの値をファイルからインポートすることができます。 そのテーブルをし、非表示にすることができます。 
  
## <a name="how-to-create-a-calculated-table"></a>計算テーブルを作成する方法  
  
1.  最初に、表形式モデルが互換性レベル 1200 以上のことを確認します。 SSDT のモデルで **[互換性レベル]** プロパティを確認できます。  
  
2.  データ ビューに切り替えます。 ダイアグラム ビューでは計算テーブルを作成できません。  
  
3.  **[テーブル]**  >  **[新しい計算テーブル]** の順に選択します。  
  
4.  DAX 式を入力するか貼り付けます (以下を参考にしてください)。  
  
5.  テーブルの名前を設定します。  
  
6.  モデルの他のテーブルへのリレーションシップを作成します。 参照してください[2 テーブル間のリレーションシップを作成](../../analysis-services/tabular-models/create-a-relationship-between-two-tables-ssas-tabular.md)この手順で必要な場合。  
  
7.  モデル内の計算や式でテーブルを参照するか、またはアドホック データ探索用に **[Excel で分析]** で使用します。  
  
### <a name="replicate-a-role-playing-dimension"></a>多様ディメンションをレプリケートする  
 [数式] バーで、別のテーブルのコピーを取得する DAX 式を入力します。 計算テーブルを読み込んだ後、わかりやすい名前を付け、ロールに固有の外部キーを使用するリレーションシップを設定します。 たとえば、Adventure Works データベースでは、Due Date の計算テーブルを作成し、ファクト テーブルとのリレーションシップのベースとして DueDateKey を使用できます。  
  
```  
=DimDate  
```  
  
### <a name="summarized-or-filtered-dataset"></a>集計されたデータセットまたはフィルター選択されたデータセット  
 [数式] バーで、データセットにフィルター処理、要約、またはそれ以外の操作を行って必要な行を取得する DAX 式を入力します。 次の例では、売上、色、通貨でグループ化しています。  
  
```  
=SUMMARIZECOLUMNS(DimProduct[Color]  
, DimCurrency[CurrencyName]   
, "Sales" , SUM(FactInternetSales[SalesAmount])  
)  
```  
  
### <a name="superset-using-columns-from-multiple-tables"></a>複数のテーブルの列を使用するスーパーセット  
 [数式] バーで、複数のテーブルの列を結合する DAX 式を入力します。 この例では、クエリの出力は通貨ごとに製品カテゴリを一覧表示します。  
  
```  
=CROSSJOIN(DimProductCategory, DimCurrency)  
```  
  
## <a name="see-also"></a>関連項目  
 [互換性レベル](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)   
 [Analysis Services の Data Analysis Expressions (DAX)](http://msdn.microsoft.com/library/abb336c9-3346-4cab-b91b-90f93f4575e5)   
 [表形式モデルで DAX を理解します。](../../analysis-services/tabular-models/understanding-dax-in-tabular-models-ssas-tabular.md)  
  
  

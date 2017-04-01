---
title: "カスタム メンバー式の定義 | Microsoft Docs"
ms.custom: ""
ms.date: "03/06/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "メンバー [Analysis Services], カスタム"
  - "カスタム ロールアップ式 [Analysis Services]"
  - "MDX [Analysis Services], カスタム ロールアップ式"
  - "カスタム メンバー式 [Analysis Services]"
ms.assetid: 258304e2-d900-4013-97e3-871f51dfdce2
caps.latest.revision: 32
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# カスタム メンバー式の定義
  カスタム メンバー式と呼ばれる多次元式 (MDX) を定義すると、指定した属性のメンバーに値を指定できます。 データ ソース ビューからのテーブルの列は、属性のメンバーごとに、そのメンバーの値の指定に使用される式を提供します。  
  
 カスタム メンバー式により、メンバーに関連付けられたセル値が判別され、メジャーの集計関数が上書きされます。 カスタム メンバー式は、MDX で記述します。 各カスタム メンバー式は、1 つのメンバーに適用されます。 カスタム メンバー式は、ディメンション テーブルまたはディメンション テーブルとの外部キー リレーションシップを持つ別のテーブルに格納されます。  
  
 属性の **CustomRollupColumn** プロパティは、属性のメンバーのカスタム メンバー式が含まれている列を指定します。 列の行が空の場合は、メンバーのセル値は通常どおり返されます。 列の式が有効でない場合は、メンバーを使用するセル値が取得されるたびに実行時エラーが発生します。  
  
 属性のカスタム メンバー式を指定する前に、属性が含まれているディメンション テーブル、つまり直接関連するテーブルに、カスタム メンバー式を保存するための文字列型の列があることを確認してください。 この場合、属性に **CustomRollupColumn** プロパティを手動で設定するか、またはビジネス インテリジェンス ウィザードのカスタム メンバー式の設定拡張機能を使用して、属性にカスタム メンバー式を有効にします。 この拡張機能の使用方法については、「[ディメンションの属性に対するカスタム メンバー式の設定](../../analysis-services/multidimensional-models/set-custom-member-formulas-for-attributes-in-a-dimension.md)」を参照してください。  
  
## カスタム メンバー式の評価  
 カスタム メンバー式は、計算されるメンバーとは異なります。 カスタム メンバー式は、ディメンション テーブルに存在しているメンバーに適用され、メンバーの値のみを提供します。 これに対して、計算されるメンバーはディメンション テーブルに格納されず、ディメンションまたは階層に含まれている他のメンバーのデータとメタデータの両方を定義します。  
  
 カスタム メンバー式は、メジャーに関連付けられている集計関数より優先されます。 たとえば、カスタム メンバー式を指定する前に、時間ディメンションの以下のメンバーについて、**Sum** 集計関数を使用するメジャーが次の値であるとします。  
  
-   2003: 2100  
  
    -   Quarter 1: 700  
  
    -   Quarter 2: 500  
  
    -   Quarter 3: 100  
  
    -   Quarter 4: 800  
  
-   2004: 1500  
  
    -   Quarter 1: 600  
  
    -   Quarter 2: 200  
  
    -   Quarter 3: 300  
  
    -   Quarter 4: 400  
  
 カスタム メンバー式を使用すると、メンバーの値は代わりにカスタム ロールアップ式によって指定されます。 たとえば、次のカスタム メンバー式を使用すると、時間ディメンションの 2004 メンバーの Quarter 4 子メンバーの値を 450 に指定できます。  
  
```  
Time.[Quarter 3] * 1.5  
```  
  
 カスタム メンバー式は、ディメンション テーブルの列に格納されます。 属性の **CustomRollupColumn** プロパティを設定して、カスタム ロールアップ式を有効にします。  
  
 1 つの MDX 式を属性のすべてのメンバーに適用するには、MDX 式をリテラル文字列として返すディメンション テーブルで名前付き計算を作成します。 次に、名前付き計算を、構成する属性の **CustomRollupColumn** プロパティ設定で指定します。 名前付き計算は、SQL 式によって定義される行の値を返す、データ ソース ビュー テーブルの列です。 名前付き計算の構築方法については、「[データ ソース ビューでの名前付き計算の定義 (Analysis Services)](../../analysis-services/multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)」を参照してください。  
  
> [!NOTE]  
>  特定の属性に基づいているすべてのレベルのメンバーではなく、特定のレベルのメンバーに MDX 式を適用するには、レベルの MDX スクリプトとして式を定義できます。 詳細については、「[MDX スクリプティングの基礎 (Analysis Services)](../../analysis-services/multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md)」を参照してください。  
  
 計算されるメンバーと属性のメンバーのカスタム ロールアップ式の両方を使用する場合は、評価の順序に注意してください。 計算されるメンバーは、カスタム ロールアップ式が解決される前に解決されます。  
  
## 参照  
 [属性と属性階層](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [ディメンションの属性に対するカスタム メンバー式の設定](../../analysis-services/multidimensional-models/set-custom-member-formulas-for-attributes-in-a-dimension.md)  
  
  
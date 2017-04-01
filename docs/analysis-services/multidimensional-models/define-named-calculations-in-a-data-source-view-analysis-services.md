---
title: "データ ソース ビューでの名前付き計算の定義 (Analysis Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
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
  - "名前付き計算の変更"
  - "データ ソース ビュー [Analysis Services], 名前付き計算"
  - "名前付き計算 [Analysis Services]"
ms.assetid: 729e7b12-6185-4b73-8bcb-cfe459b15355
caps.latest.revision: 34
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 34
---
# データ ソース ビューでの名前付き計算の定義 (Analysis Services)
  名前付き計算は、計算される列として表現されている SQL 式です。 この式は、テーブル内の列として表示され動作します。 名前付き計算を使用すると、基になるデータ ソースのテーブルやビューを変更しなくても、データ ソース ビュー内の既存のテーブルまたはビューのリレーショナル スキーマを拡張できます。 次の例を考えてみます。  
  
-   ファクト テーブルの複数の列から派生した 1 つの名前付き計算を作成します (たとえば、税率に販売価格を乗算して Tax Amount を作成します)。  
  
-   ディメンション メンバーにわかりやすい名前を付けます。  
  
-   クエリ パフォーマンスの強化として、キューブに計算済みのメンバーを作成するのではなく、DSV に名前付き計算を作成します。 名前付き計算は処理中に計算されますが、計算されるメンバーはクエリ時に計算されます。  
  
## 名前付き計算の作成  
  
> [!NOTE]  
>  名前付き計算を名前付きクエリに追加したり、名前付き計算を含んでいるテーブルに基づいて名前付きクエリを作成したりすることはできません。  
  
 名前付き計算を作成するには、名前と SQL 式を指定し、必要に応じて計算の説明も指定します。 SQL 式は、データ ソース ビュー内の他のテーブルを参照できます。 名前付き計算を定義すると、名前付き計算の式がデータ ソースのプロバイダーに送信され、次の SQL ステートメントとして検証されます。ここで、`<Expression>` には、名前付き計算を定義する式が含まれます。  
  
```  
SELECT   
   <Table Name in Data Source>.*,   
   <Expression> AS <Column Name>   
FROM   
   <Table Name in Data Source> AS <Table Name in Data Source View>  
```  
  
 列のデータ型は、式によって返されたスカラー値のデータ型によって決まります。 プロバイダーによって式でエラーが検出されなければ、列がテーブルに追加されます。  
  
 式で参照される列は、修飾する必要がないか、テーブル名によってのみ修飾する必要があります。 たとえば、テーブルの SaleAmount 列を参照するには、`SaleAmount` または `Sales.SaleAmount` は有効ですが、`dbo.Sales.SaleAmount` ではエラーが発生します。  
  
 式は、自動的にはかっこで囲まれません。 このため、SELECT ステートメントなどの式で、かっこが必要な場合は、**[式]** ボックスでかっこを入力する必要があります。 たとえば、次の式は、かっこを入力した場合にのみ有効です。  
  
```  
(SELECT Description FROM Categories WHERE Categories.CategoryID = CategoryID)  
```  
  
## 名前付き計算の追加または編集  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] でプロジェクトを開くか、名前付き計算を定義するデータ ソース ビューが含まれているデータベースに接続します。  
  
2.  ソリューション エクスプローラーで、**[データ ソース ビュー]** フォルダーを展開し、データ ソース ビューをダブルクリックします。  
  
3.  **[テーブル]** ペインまたは **[ダイアグラム]** ペインで、名前付き計算を定義するテーブルを右クリックし、**[新しい名前付き計算]** をクリックします。 必ず、属性ではなくテーブル名を右クリックします。 メニューは以下のようになります。  
  
     ![ダイアグラム ワークスペース (右クリック メニュー) のスクリーンショット](../../analysis-services/multidimensional-models/media/ssas-olapdsv-diagram.gif "ダイアグラム ワークスペース (右クリック メニュー) のスクリーンショット")  
  
    > [!NOTE]  
    >  テーブルまたはビューを検索する場合は、**[データ ソース ビュー]** メニューをクリックするか、**[テーブル]** ペインまたは **[ダイアグラム]** ペインの空いている領域を右クリックすることで、**[テーブルの検索]** オプションを使用できます。  
  
4.  **[名前付き計算の作成]** ダイアログ ボックスで、次の操作を行います。  
  
    -   **[列名]** テキスト ボックスに新しい列の名前を入力します。  
  
    -   **[説明]** テキスト ボックスに新しい列の説明を入力します。  
  
    -   **[式]** テキスト ボックスに、データ プロバイダーに適した SQL 言語仕様で新しい列の内容をもたらす式を入力します。  
  
5.  **[OK]**をクリックします。  
  
     名前付き計算の列がデータ ソース ビュー テーブルの最後の列に表示されます。 名前付き計算を含む列は、計算機の記号で示されます。  
  
## 名前付き計算の削除  
 名前付き計算を削除しようとすると、削除するかどうかを確認するメッセージが、削除によって無効になるプロジェクトまたはデータベースに定義されているオブジェクトのリストと共に表示されます。 計算を削除する前に、リストを慎重に確認します。  
  
## 参照  
 [データ ソース ビューでの名前付きクエリの定義 (Analysis Services)](../../analysis-services/multidimensional-models/define-named-queries-in-a-data-source-view-analysis-services.md)  
  
  
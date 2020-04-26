---
title: テーブルモデルのクエリ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: b01d45d9-4598-4ded-9a9e-e3419cc3df8e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 61b6f366843b326a8983c27c3d5ee945604756f0
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/25/2020
ms.locfileid: "62757743"
---
# <a name="querying-a-tabular-model"></a>テーブル モデルのクエリ
  テーブル モデルのクエリを実行することは、テーブル データベースからデータを取得することを意味します。この目的を達成する方法は 2 つあります。DAX 内の表形式クエリを使用する方法と、MDX を使用して、キューブから取得するような形でデータを取得する方法です。 ただし、テーブル モデルの基になるモードによっては、DAX 表形式クエリしか使用できない場合があります。DirectQuery モードでは、DAX 表形式クエリを使用する必要があります。  
  
## <a name="querying-with-adomdnet"></a>ADOMD.NET を使用したクエリ  
 ADOMD.Net を使用してテーブル モデルをクエリする方法は単純で柔軟性に優れています。DAX から MDX ステートメントまたは表形式クエリ式をサーバーに送信して、結果を受信します。  
  
 次のコードでは、クエリ ステートメントをテーブル モデルに渡し、その結果を受信する方法を示します。  
  
```csharp  
//Function: tabularQueryExecute(string qry, ADOMD.AdomdConnection cnx)  
//   - arg: qry, the tabular query or MDX expression to be evaluated  
//   - arg: cnx, an active and opened ADOMD connection to the database where 'qry' is to be evaluated  
//  
// This function takes a query or mdx expression -qry-, a connection -cnx-  
// and runs the query it against a Tabular Model using ADOMD.net  
//  
// Important note:  
//    If the MDX query contains more than 2 axes (ON COLUMNS, ON ROWS), each axis will come as a new column  
//    If the (All) value of the members in any axis have not been defined, a blank cell is returned. This might be misleading  
//    if the model also has missing values... which are also represented with blank cells.  
private DataTable tabularQueryExecute(string qry, ADOMD.AdomdConnection cnx)  
{  
    ADOMD.AdomdDataAdapter currentDataAdapter = new ADOMD.AdomdDataAdapter(qry, cnx);  
    DataTable tabularResults = new DataTable();  
    currentDataAdapter.Fill(tabularResults);  
    return tabularResults;  
}  
  
```  
  
### <a name="example"></a>例  
 ここでは、上記のコードを次の MDX 式と組み合わせて使用します。  
  
```  
SELECT { [Measures].[Internet Total Sales], [Measures].[Reseller Total Sales], [Measures].[Total Sales] } ON COLUMNS  
     , NON EMPTY [Product Category].[Product Category Name].MEMBERS ON ROWS "  
     , NON EMPTY [Date].[Calendar Year].members ON 2 \n"  
FROM [Model]  
  
```  
  
 サンプル モデル 'Adventure Works DW Tabular Denali CTP3' に対して使用した場合、次の値を含む結果のテーブルが表示されます。  
  
|Calendar Year|Product Category Name|Internet Total Sales|Reseller Total Sales|Total Sales|  
|-------------------|---------------------------|--------------------------|--------------------------|-----------------|  
|||$29358677.22|$80450596.98|$109809274.20|  
||Accessories|$700759.96|$571297.93|$1272057.89|  
||Bikes|$28318144.65|$66302381.56|$94620526.21|  
||Clothing|$339772.61|$1777840.84|$2117613.45|  
||Components||$11799076.66|$11799076.66|  
|2001||$3266373.66|$8065435.31|$11331808.96|  
|2001|Accessories||$20235.36|$20235.36|  
|2001|Bikes|$3266373.66|$7395348.63|$10661722.28|  
|2001|Clothing||$34376.34|$34376.34|  
|2001|Components||$615474.98|$615474.98|  
|2002||$6530343.53|$24144429.65|$30674773.18|  
|2002|Accessories||$92735.35|$92735.35|  
|2002|Bikes|$6530343.53|$19956014.67|$26486358.20|  
|2002|Clothing||$485587.15|$485587.15|  
|2002|Components||$3610092.47|$3610092.47|  
|2003||$9791060.30|$32202669.43|$41993729.72|  
|2003|Accessories|$293709.71|$296532.88|$590242.59|  
|2003|Bikes|$9359102.62|$25551775.07|$34910877.69|  
|2003|Clothing|$138247.97|$871864.19|$1010112.16|  
|2003|Components||$5482497.29|$5482497.29|  
|2004||$9770899.74|$16038062.60|$25808962.34|  
|2004|Accessories|$407050.25|$161794.33|$568844.58|  
|2004|Bikes|$9162324.85|$13399243.18|$22561568.03|  
|2004|Clothing|$201524.64|$386013.16|$587537.80|  
|2004|Components||$2091011.92|$2091011.92|  
  
 MDX 式を次の DAX 表形式クエリ式に置き換えます。  
  
```  
DEFINE  
   MEASURE 'Product Category'[Internet Sales] = SUM( 'Internet Sales'[Sales Amount])  
   MEASURE 'Product Category'[Reseller Sales] = SUM('Reseller Sales'[Sales Amount]) \n"  
   EVALUATE ADDCOLUMNS('Product Category', \"Internet Sales - All Years\", 'Product Category'[Internet Sales], \"Reseller Sales - All Years\", 'Product Category'[Reseller Sales])  
  
```  
  
 これを上記のサンプル コードを使用してサーバーに送信します。サンプル モデル 'Adventure Works DW Tabular Denali CTP3' に対して使用した場合、次の値を含む結果のテーブルが表示されます。  
  
|Product Category Id|Product Category Alternate Id|Product Category Name|Internet Sales|Reseller Sales|  
|-------------------------|-----------------------------------|---------------------------|--------------------|--------------------|  
|4|4|Accessories|$700759.96|$571297.93|  
|1|1|Bikes|$28318144.65|$66302381.56|  
|3|3|Clothing|$339772.61|$1777840.84|  
|2|2|Components||$11799076.66|  
  
  

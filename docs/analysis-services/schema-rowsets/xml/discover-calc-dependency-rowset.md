---
title: "DISCOVER_CALC_DEPENDENCY 行セット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords: DISCOVER_CALC_DEPENDENCIES rowset
ms.assetid: f39dde72-fa5c-4c82-8b4e-88358aa2e422
caps.latest.revision: "22"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 9eca892f8ddf9e85e05d33b81023a3602c861734
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="discovercalcdependency-rowset"></a>DISCOVER_CALC_DEPENDENCY 行セット
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]これらの計算で参照されるオブジェクトおよび計算間の依存関係をレポートします。 クライアント アプリケーションでは、複雑な式に伴う問題についてレポートする場合や、関連するオブジェクトが削除または変更されたときに警告を生成する場合に、この情報を使用できます。 また、この行セットを使用して、メジャーまたは計算列で使用される DAX 式を抽出することもできます。  
  
 **適用対象:** テーブル モデル  
  
## <a name="rowset-columns"></a>行セットの列  
 **DISCOVER_CALC_DEPENDENCY** 行セットには、次の列が含まれています。 表には、データ型、列を制限することで返される行を制限できるかどうか、および各列の説明も示しています。  
  
|列名|型を表すインジケーター|制限|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|**DATABASE_NAME**|**DBTYPE_WSTR**|可|依存関係分析を要求する際の対象となるオブジェクトを含んだデータベースの名前を指定します。 省略した場合は、現在のデータベースが使用されます。<br /><br /> **DISCOVER_DEPENDENCY_CALC** 行セットはこの列を使用して制限できます。|  
|**OBJECT_TYPE**|**DBTYPE_WSTR**|可|依存関係分析の要求対象となるオブジェクトの種類を示します。 オブジェクトの種類は次のいずれかに該当する必要があります。<br /><br /> **ACTIVE_RELATIONSHIP**: アクティブなリレーションシップ<br /><br /> **CALC_COLUMN**: 計算列<br /><br /> **HIERARCHY**: 階層<br /><br /> **MEASURE**: メジャー<br /><br /> **RELATIONSHIP**: リレーションシップ<br /><br /> **KPI**: KPI (主要業績評価指標)<br /><br /> <br /><br /> なお、 **DISCOVER_DEPENDENCY_CALC**この列を使用して行セットを制限することができます。|  
|**クエリ**|**DBTYPE_WSTR**|可|[!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] で作成されたテーブル モデルの場合は、DAX クエリまたは式を含めて、そのクエリまたは式の依存グラフを表示できます。 クライアント アプリケーションでは、QUERY 制限を使用して、DAX クエリで使用されているオブジェクトを確認できます。<br /><br /> **QUERY** 制限は、XMLA または DMV クエリの WHERE 句で指定できます。 詳細については、「例」を参照してください。|  
|**TABLE**|**DBTYPE_WSTR**||依存関係情報の生成対象となるオブジェクトを含んだテーブルの名前です。|  
|**オブジェクト**|**DBTYPE_WSTR**||依存関係情報の生成対象となるオブジェクトの名前です。 オブジェクトがメジャーまたは計算列である場合は、メジャーの名前を使用します。 オブジェクトがリレーションシップである場合は、リレーションシップに参加している列を含んだテーブル (またはキューブ ディメンション) の名前になります。|  
|**式**|**DBTYPE_WSTR**||依存関係の検出対象となるオブジェクトを含んでいる式です。|  
|**REFERENCED_OBJECT_TYPE**|**DBTYPE_WSTR**||参照先オブジェクトに依存しているオブジェクトの種類を返します。 返されるオブジェクトの種類は、次のいずれかです。<br /><br /> **CALC_COLUMN**:  計算列<br /><br /> **COLUMN**: データ列<br /><br /> **MEASURE**: メジャー<br /><br /> **RELATIONSHIP**: リレーションシップ<br /><br /> **KPI**: KPI (主要業績評価指標)|  
|**REFERENCED_TABLE**|**DBTYPE _ WSTR**||依存オブジェクトを含んだテーブルの名前です。|  
|**REFERENCED_OBJECT**|**DBTYPE _ WSTR**||参照先オブジェクトに依存しているオブジェクトの名前です。 メジャーおよび計算列の場合は、メジャーまたは列の名前になります。 リレーションシップの場合は、依存オブジェクトを含んだテーブル (またはキューブ ディメンション) の完全修飾名になります。|  
|**REFERENCED_EXPRESSION**|**DBTYPE_WSTR**||計算列またはメジャーにおいて、参照先オブジェクトに依存する式です。|  
  
## <a name="example"></a>例  
 **基本構文**  
  
 次のクエリは、現在の接続の既定のデータベースを使用して、この行セットのすべての列の値を返す、簡単な DMV クエリです。 このクエリを MDX クエリ ウィンドウで実行し、結果を [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] で表示できます。 説明する手法を行うことができる[Excel から Power Pivot Dmv のクエリ](http://go.microsoft.com/fwlink/?LinkID=235146)を Excel で DMV クエリの結果を表示します。  
  
```  
SELECT * FROM $System.DISCOVER_CALC_DEPENDENCY  
```  
  
## <a name="example"></a>例  
 **結果を並べ替え**  
  
 テーブルまたは別の列を基準にして行セットを並べ替えるには、ORDER BY を追加します。  
  
```  
SELECT * FROM $System.DISCOVER_CALC_DEPENDENCY ORDER BY [TABLE] ASC  
```  
  
## <a name="example"></a>例  
 **WHERE 句を使用してフィルター処理します。**  
  
 次のクエリでは、WHERE 句を使用して制限を追加する方法を示します。 WHERE 句では、 **Database_Name**、 **Object_Type**、および **Query**の各列をクエリ フィルターとして使用できます。  
  
```  
SELECT * From $SYSTEM.DISCOVER_CALC_DEPENDENCY WHERE OBJECT_TYPE = 'RELATIONSHIP' OR OBJECT_TYPE = 'ACTIVE_RELATIONSHIP'  
```  
  
## <a name="example"></a>例  
 **メジャーと基になる DAX 式を表示する計算列でフィルター処理します。**  
  
 このクエリでは、メジャー列または計算列のみを選択し、計算に使用されている DAX 式を表示できます。 EXPRESSION 列には DAX 式が含まれています。 DISCOVER_CALC_DEPENDENCY を使用して、モデルで使用される DAX 式を抽出する目的に対しては、このクエリで十分です。 モデルで使用されているすべての式が昇順で並べ替えられて返されます。  
  
```  
SELECT * From $SYSTEM.DISCOVER_CALC_DEPENDENCY WHERE OBJECT_TYPE = 'MEASURE' OR OBJECT_TYPE = 'CALC_COLUMN' ORDER BY [EXPRESSION] ASC  
```  
  
## <a name="example"></a>例  
 **クエリを使用してフィルター処理します。**  
  
 DAX クエリで QUERY 制限を使用すると、そのクエリで使用されているすべてのオブジェクトを表示できます。 "Evaluate Customer" (顧客の評価) という単純なクエリがあるとします。 このクエリは、文字どおり、行の構成が Customer テーブルの列に基づく顧客データの行を返します。 "Evaluate Customer" の QUERY 制限を使用して、DISCOVER_CALC_DEPENDENCY を実行すると、そのクエリで使用されている列 (つまり、オブジェクト) が返されます。 この場合は、Customer テーブルの列の一覧が返されます。  
  
 次のクエリでは、QUERY 制限の構文を示しています。 これらのクエリを [AdventureWorks Tabular Model SQL Server 2012](http://msftdbprodsamples.codeplex.com/releases/view/55330) に対して実行して、結果セットを表示できます。  
  
 最初のクエリでは、スペースを含むオブジェクト名の QUERY 制限を指定する方法を示しています。 「 [OLE DB および ADOMD.NET を使用した DAX クエリの実行](http://go.microsoft.com/fwlink/?LinkId=254329)」から借用した 2 番目のクエリは、複数のテーブルのオブジェクトを含む複雑なクエリです。  
  
> [!NOTE]  
>  クエリに二重引用符が使用されているように見えますが、実際には、単一引用符のみが使用されています。 1 組の単一引用符で囲みます ' 評価\<Tablename >'、テーブル名を囲む単一引用符がそれら 2 つ入力してエスケープする必要があります。 テーブル名を囲む単一引用符は、テーブル名にスペースが含まれている場合のみ必要になります。  
  
```  
SELECT * From $SYSTEM.DISCOVER_CALC_DEPENDENCY WHERE QUERY = 'EVALUATE ''Reseller Sales'''  
```  
  
```  
SELECT * from $system.DISCOVER_CALC_DEPENDENCY WHERE QUERY = 'EVALUATE CALCULATETABLE(VALUES(''Product Subcategory''[Product Subcategory Name]), ''Product Category''[Product Category Name] = "Bikes")'  
```  
  
## <a name="example"></a>例  
 **XMLA クエリ制限の例**  
  
 XMLA Discover コマンドを使用して、テーブル内のクエリ オブジェクトを返すことができます。 XMLA の結果は未加工の XML として返されます。 ADOMD.NET を使用すると、結果を判読できる形式で解析できます。  
  
```  
<Discover xmlns="urn:schemas-microsoft-com:xml-analysis">  
   <RequestType>DISCOVER_CALC_DEPENDENCY</RequestType>  
     <Restrictions>  
        <RestrictionList>  
            <QUERY>Evaluate 'Reseller Sales'</QUERY>  
        </RestrictionList>  
    </Restrictions>  
    <Properties />  
</Discover>  
```  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>ADOMD.NET を使用した行セットのリターン  
 ADOMD.NET とスキーマ行セットを使用してメタデータを取得する場合、GetSchemaDataSet メソッドで GUID または文字列を使用してスキーマ行セット オブジェクトを参照できます。 詳細については、「 [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md)」を参照してください。  
  
 次の表に、この行セットを識別する GUID と文字列の値を示します。  
  
|引数|値|  
|--------------|-----------|  
|GUID|a07ccd46-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|DependencyGraph|  
  
## <a name="see-also"></a>参照  
 [Analysis Services のスキーマ行セット](../../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)   
 [使用して動的管理ビュー (&) #40 です。 Dmv &#41;Analysis Services を監視するには](../../../analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)  
  
  

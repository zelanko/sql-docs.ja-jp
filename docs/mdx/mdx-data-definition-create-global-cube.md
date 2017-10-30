---
title: "CREATE GLOBAL CUBE ステートメント (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- GLOBAL CUBE
- CUBE
- GLOBAL
- CREATE
- CREATE GLOBAL
- CREATE GLOBAL CUBE
dev_langs:
- kbMDX
helpviewer_keywords:
- statements [MDX], CREATE GLOBAL CUBE
- CREATE GLOBAL CUBE
ms.assetid: b46f3c98-a4f1-4ebb-915f-a3333f4054dc
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: b9a80a053d9666ca2e8c63eb6037dddf3cf4a7a5
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="mdx-data-definition---create-global-cube"></a>MDX データ定義のグローバル キューブを作成します。
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  サーバーのキューブのサブキューブを基にして、ローカルに保存されるキューブを作成します。 ローカルに保存されるキューブに接続する場合、サーバーに接続する必要はありません。 ローカル キューブの詳細については、次を参照してください。[ローカル キューブと #40 です。Analysis Services - 多次元データ &#41;](../analysis-services/multidimensional-models/olap-physical/local-cubes-analysis-services-multidimensional-data.md).  
  
## <a name="syntax"></a>構文  
  
```  
  
CREATE GLOBAL CUBE local_cube_name STORAGE 'Cube_Location'   
FROM source_cube_name (<param list>)  
  
<param list>::= <param> ,<param list> | <param>  
  
<param>::= <dims list> | <measures list>  
  
<measures list>::= <measure>[, <measures list>]   
  
<dims list>::= <dim def> [, <dims list>]  
  
<measure>::= MEASURE source_cube_name.measure_name [<visibility qualifier>] [AS measure_name]   
  
<dim def>::= <source dim def> | <derived dim def>  
  
<source dim def>::= DIMENSION source_cube_name.dimension_name [<dim flags>] [<visibility qualifier>] [AS dimension_name>] [FROM <dim from clause> ] [<dim content def>]  
  
<dim flags>::= NOT_RELATED_TO_FACTS   
  
<dim from clause>::= < dim DM from clause> | <reg dim from clause>   
  
<dim DM from clause>::= dm_model_name> COLUMN column_name   
  
<dim reg from clause>::= dimension_name  
  
<dim content def>::= ( <level list> [,<grouping list>] [,<member slice list>] [,<default member>] )  
  
<level list>::= <level def> [, <level list>]  
  
<level def>::= LEVEL level_name [<level type> ] [AS level_name] [<level content def>]  
  
<level content def>::= ( <property list> ) | NO_PROPERTIES  
  
<level type>::= GROUPING  
  
<property list>::= <property def> [, <property list>]  
  
<property def>::= PROPERTY property_name   
  
<grouping list>::= <grouping entity> [,<grouping list>]  
  
<grouping entity>::= GROUP group_level_name.group_name (<mixed list>)  
  
<grp mixed list>::= <grp mixed element> [,<grp mixed list>]  
  
<grp mixed element>::= <grouping entity> | <member def>  
  
<member slice list>::= <member list>  
  
<member list>::= <member def> [, <member list>]  
  
<member def>::= MEMBER member_name  
  
<default member>::= DEFAULT_MEMBER AS MDX_expression  
  
<visibility qualifier>::= HIDDEN   
```  
  
## <a name="syntax-elements"></a>構文要素  
 local_cube_name  
 ローカル キューブの名前です。  
  
 'Cube_Location'  
 ローカルに保持されるキューブの名前とパスです。  
  
 source_cube_name  
 作成するローカル キューブの基になるキューブの名前です。  
  
 source_cube_name.measure_name  
 ローカル キューブに含まれる、基になるメジャーの完全修飾名です。 Measures ディメンションの計算されるメンバーは指定できません。  
  
 measure_name  
 ローカル キューブのメジャーの名前です。  
  
 source_cube_name.dimension_name  
 ローカル キューブに含まれる、基になるディメンションの完全修飾名です。  
  
 dimension_name  
 ローカル キューブのディメンションの名前です。  
  
 \<句から dim >  
 派生ディメンションの定義でのみ指定できます。  
  
 NOT_RELATED_TO_FACTS  
 派生ディメンションの定義でのみ指定できます。  
  
 \<レベルの種類 >  
 派生ディメンションの定義でのみ指定できます。  
  
## <a name="remarks"></a>解説  
 ローカル キューブは、メジャーとその定義で定義された条件です。 ディメンションには次の 2 種類があります。  
  
-   ソース ディメンション - いずれかのソース キューブを構成していたディメンションです。  
  
-   派生ディメンション - 新しい分析要素となるディメンションです。 派生ディメンションには、ソース ディメンションを垂直または水平にスライスすることによって定義した標準ディメンションと、独自にグループ化した複数のディメンション メンバーを含むディメンションがあります。 また、派生ディメンションは、データ マイニング モデルに基づくデータ マイニング ディメンションである場合もあります。  
  
> [!NOTE]  
>  Dimension キーワードは、ディメンションまたは階層を指します。  
  
 ローカル キューブでは次のタスクを実行できます。  
  
-   ソース キューブに存在するディメンションを削除する  
  
-   ディメンションに階層を追加する、ディメンションから階層を削除する  
  
-   メジャー グループまたは特定のメジャーを削除する  
  
 CREATE GLOBAL CUBE ステートメントは、以下の規則に従います。  
  
-   CREATE GLOBAL CUBE ステートメントは、計算されるメジャーやアクションなどのすべてのコマンドを自動的にローカル キューブにコピーします。 親キューブを明示的に参照する多次元式 (MDX) 式がコマンドに含まれる場合、ローカル キューブではそのコマンドを実行できません。 この問題を防ぐためを使用して、 **CURRENTCUBE**キーワード コマンドの MDX 式を定義するときにします。 **CURRENTCUBE**キーワードは、MDX 式内のキューブを参照するときに現在のキューブ コンテキストを使用します。  
  
-   ローカル キューブ ファイル内にある既存のグローバル キューブから作成したグローバル キューブは、同じローカル キューブ ファイルに保存できません。 たとえば、SalesLocal1 という名前のグローバル キューブを作成し、このキューブを C:\SalesLocal.cub ファイルに保存するとします。 その後、C:\SalesLocal.cub ファイルに接続して SalesLocal2 という名前の新しいグローバル キューブを作成します。 ここで、SalesLocal2 グローバル キューブを C:\SalesLocal.cub ファイルに保存しようとすると、エラーが返されます。 しかし、別のローカル キューブ ファイルには、SalesLocal2 グローバル キューブを保存できます。  
  
-   グローバル キューブでは、個別のカウント メジャーがサポートされません。 個別のカウント メジャーを含むキューブは非加法であるため、CREATE GLOBAL CUBE ステートメントでは、個別のカウント メジャーの作成や使用はできません。  
  
-   ローカル キューブにメジャーを追加する場合は、追加するメジャーに関連するディメンションも最低 1 つ追加する必要があります。  
  
-   ローカル キューブに親子階層を追加すると、親子階層のレベルやフィルターは無視されて、親子階層全体が追加されます。  
  
-   ローカル キューブではメンバー プロパティはサポートされません。  
  
-   ローカル キューブは、パースペクティブからは作成できません。  
  
-   ローカル キューブに準加法メジャーを含める場合、次の規則が適用されます。  
  
    -   追加するメジャーの AggregateFunction プロパティが ByAccount の場合、Account ディメンションを含める必要があります。  
  
    -   追加するメジャーの AggregateFunction プロパティが FirstChild、LastChild、FirstNonEmpty、LastNonEmpty、または AverageOfChildren の場合、Time ディメンション全体を含める必要があります。  
  
-   データ マイニング ディメンションはローカル キューブに追加できません。  
  
-   参照ディメンションは、標準ディメンションとして具体化され、追加されます。  
  
-   多対多ディメンションを含める場合は、次の規則が適用されます。  
  
    -   多対多ディメンション全体を追加する必要があります。  
  
    -   中間メジャー グループを追加する必要があります。  
  
    -   多対多リレーションシップに関係する 2 つのメジャー グループに共通するすべてのディメンションの全体を追加する必要があります。  
  
 次の例では、Adventure Works キューブを基にして、Reseller Sales Amount メジャー、Reseller ディメンション、および Date ディメンションだけを含む、保存されるローカル キューブを作成します。  
  
```  
CREATE GLOBAL CUBE [LocalReseller]  
   Storage 'C:\LocalAWReseller1.cub'  
   FROM [Adventure Works]  
   (  
      MEASURE  [Adventure Works].[Reseller Sales Amount],  
      DIMENSION [Adventure Works].[Reseller],  
      DIMENSION [Adventure Works].[Date]  
   )  
```  
  
 次の例では、ローカル キューブを作成する際にスライスを行います。 作成されるグローバル キューブは、Adventure Works キューブを基にして、Fiscal Year レベルの 2005 メンバーで縦方向に、Fiscal Year レベルおよび Month レベルで横方向にスライスしたキューブになります。  
  
```  
CREATE GLOBAL CUBE [LocalReseller]  
   Storage 'C:\LocalAWReseller2.cub'  
   FROM [Adventure Works]  
   (  
      MEASURE  [Adventure Works].[Reseller Sales Amount],  
      DIMENSION [Adventure Works].[Reseller],  
      DIMENSION [Adventure Works].[Date]  
      (  
LEVEL [Fiscal Year],  
LEVEL [Month],  
MEMBER [Date].[Fiscal].[Fiscal Year].&[2005]  
      )  
   )  
```  
  
## <a name="see-also"></a>参照  
 [MDX データ定義ステートメント & #40 です。MDX と #41 です。](../mdx/mdx-data-definition-statements-mdx.md)   
 [SESSION CUBE ステートメント &#40; を作成します。MDX と #41 です。](../mdx/mdx-data-definition-create-session-cube.md)  
  
  


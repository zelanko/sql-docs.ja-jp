---
title: CREATE GLOBAL CUBE ステートメント (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6fb1bc0055748c711762d89ad2757a12d1161254
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63181443"
---
# <a name="mdx-data-definition---create-global-cube"></a>MDX データ操作 - CREATE GLOBAL CUBE


  作成し、サーバー上のキューブのサブキューブに基づく、ローカルに保存されるキューブを設定します。 サーバーへの接続は、ローカルに保存されるキューブに接続する必要はありません。 ローカル キューブの詳細については、次を参照してください。[ローカル キューブ&#40;Analysis Services - 多次元データ&#41;](../analysis-services/multidimensional-models/olap-physical/local-cubes-analysis-services-multidimensional-data.md)します。  
  
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
 ローカル キューブの基になるキューブの名前。  
  
 source_cube_name.measure_name  
 ローカル キューブに含まれる、基になるメジャーの完全修飾名。 メジャー ディメンションの計算されるメンバーは許可されていません。  
  
 measure_name  
 ローカル キューブのメジャーの名前。  
  
 source_cube_name.dimension_name  
 ローカル キューブに含まれるソース ディメンションの完全修飾名。  
  
 dimension_name  
 ローカル キューブのディメンションの名前です。  
  
 FROM \<dim from clause>  
 派生ディメンションの定義のみ有効な仕様。  
  
 NOT_RELATED_TO_FACTS  
 派生ディメンションの定義のみ有効な仕様。  
  
 \<レベルの種類 >  
 派生ディメンションの定義のみ有効な仕様。  
  
## <a name="remarks"></a>コメント  
 ローカル キューブは、メジャーとその定義で定義された条件です。 ディメンションの 2 種類があります。  
  
-   ソース ディメンション - これらは、1 つ以上のソース キューブの一部であったディメンション  
  
-   派生ディメンション - これらは、新しい分析機能を提供するディメンションです。 派生ディメンションは、通常のディメンションが定義されている基になる、ソース ディメンションを垂直方向または水平方向にスライスか、またはディメンション メンバーのカスタム グループを格納します。 また、派生ディメンションは、データ マイニング モデルに基づくデータ マイニング ディメンションである場合もあります。  
  
> [!NOTE]  
>  Dimension キーワードは、ディメンションまたは階層を参照できます。  
  
 ローカル キューブでは次のタスクを実行できます。  
  
-   ソース キューブ内に存在するディメンションを削除します。  
  
-   ディメンションに階層を追加する、ディメンションから階層を削除する  
  
-   メジャー グループまたは特定のメジャーを削除します。  
  
 CREATE GLOBAL CUBE ステートメントは、以下の規則に従います。  
  
-   CREATE GLOBAL CUBE ステートメントは、計算されるメジャーやアクションなどのすべてのコマンドを自動的にローカル キューブにコピーします。 コマンドには、親キューブを明示的に参照する多次元式 (MDX) 式が含まれる、ローカル キューブはそのコマンドを実行できません。 この問題を回避するには、使用、 **CURRENTCUBE**コマンドの MDX 式を定義するときに、キーワード。 **CURRENTCUBE**キーワードは、MDX 式内のキューブを参照するときに現在のキューブ コンテキストを使用します。  
  
-   ローカル キューブ ファイル内の既存のグローバル キューブから作成されるグローバル キューブは、同じローカル キューブ ファイルに保存できません。 たとえば、SalesLocal1 という名前のグローバル キューブを作成し、このキューブを C:\SalesLocal.cub ファイルに保存します。 C:\SalesLocal.cub ファイルに接続し、SalesLocal2 という名前の 2 つ目のグローバル キューブを作成します。 これで、SalesLocal2 グローバル キューブを C:\SalesLocal.cub ファイルに保存すると、エラーを受け取ります。 ただし、別のローカル キューブ ファイルには、SalesLocal2 グローバル キューブを保存できます。  
  
-   グローバル キューブでは、個別のカウント メジャーがサポートされません。 個別のカウント メジャーを含むキューブは非加法であるため、CREATE GLOBAL CUBE ステートメントでは、個別のカウント メジャーの作成や使用はできません。  
  
-   ローカル キューブにメジャーを追加する場合は、追加するメジャーに関連するディメンションも最低 1 つ追加する必要があります。  
  
-   ローカル キューブに親子階層を追加するときにレベルと、親子階層に基づくフィルターは無視され、全体の親子階層が含まれています。  
  
-   ローカル キューブではメンバー プロパティはサポートされません。  
  
-   ローカル キューブは、パースペクティブからは作成できません。  
  
-   ローカル キューブに準加法メジャーが含まれる場合は、次の規則が適用されます。  
  
    -   追加するメジャーの AggregateFunction プロパティが ByAccount の場合、Account ディメンションを含める必要があります。  
  
    -   追加するメジャーの AggregateFunction プロパティが FirstChild、LastChild、FirstNonEmpty、LastNonEmpty、または AverageOfChildren の場合、Time ディメンション全体を含める必要があります。  
  
-   データ マイニング ディメンションは、ローカル キューブに追加できません。  
  
-   参照ディメンションを具体化し、標準ディメンションとして追加します。  
  
-   多対多ディメンションを含める場合は、次の規則が適用されます。  
  
    -   多対多ディメンション全体を追加する必要があります。  
  
    -   中間メジャー グループを追加する必要があります。  
  
    -   多であるリレーションシップに関係する 2 つのメジャー グループには、一般的なすべてのディメンションの全体を追加する必要があります。  
  
 次の例では、Reseller Sales Amount メジャーのみ、Reseller ディメンション、および Date ディメンションを含む、Adventure Works キューブのローカルで永続化されたバージョンの作成を示します。  
  
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
  
 次の例では、ローカル キューブを作成するときにスライスを示します。 作成されるグローバル キューブは、Fiscal Year レベルの 2005年メンバーによってと会計年と月レベルで水平方向に垂直方向にスライス、Adventure Works キューブに基づきます。  
  
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
 [MDX データ定義ステートメント&#40;MDX&#41;](../mdx/mdx-data-definition-statements-mdx.md)   
 [CREATE SESSION CUBE ステートメント&#40;MDX&#41;](../mdx/mdx-data-definition-create-session-cube.md)  
  
  

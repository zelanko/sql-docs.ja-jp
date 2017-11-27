---
title: "CREATE SESSION CUBE ステートメント (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE_SESSION_CUBE
- SESSION
- CUBE
- SESSION CUBE
- CREATE SESSION CUBE
- CREATE SESSION
- CREATE
dev_langs:
- kbMDX
helpviewer_keywords:
- CREATE SESSION CUBE
- statements [MDX], CREATE SESSION CUBE
ms.assetid: 06b90f44-d943-4a52-b0d8-4bcbc57ed6ec
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 14556669f6c39977fa1f82d8fbe6a2edff927837
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="mdx-data-definition---create-session-cube"></a>MDX データ定義、セッション キューブの作成
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  既存のサーバー キューブから、セッション キューブを作成および設定します。 セッション キューブは現在のセッション内でのみ表示できます。他のセッションから参照したり、クエリを実行することはできません。 セッション キューブは、セッションが閉じられたときに暗黙的に削除されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
CREATE SESSION CUBE session_cube_name FROM <cube list> (<param list>)  
  
<cube list>::= source_cube_name [,<cube list>]  
  
<param list>::= <param> ,<param list> | <param>  
  
<param>::= <dims list> | <measures list>  
  
<measures list>::= <measure>[, <measures list>]   
  
<dims list>::= <dim def> [, <dims list>]  
  
<measure>::= MEASURE source_cube_name.measure_name [<visibility qualifier>] [AS measure_name]   
  
<dim def>::= <source dim def> | <derived dim def>  
  
<source dim def>::= DIMENSION source_cube_name.dimension_name [<dim flags>] [<visibility qualifier>] [AS dimension_name>] [FROM <dim from clause> ] [<dim content def>]  
  
<dim flags>::= NOT_RELATED_TO_FACTS   
  
<dim from clause>::= <reg dim from clause>   
  
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
 session_cube_name  
 セッション キューブの名前です。  
  
 source_cube_name  
 作成するセッション キューブの基になるキューブの名前です。  
  
 source_cube_name.measure_name  
 セッション キューブに含まれる、基になるメジャーの完全修飾名です。 Measures ディメンションの計算されるメンバーは指定できません。  
  
 measure_name  
 セッション キューブのメジャーの名前です。  
  
 source_cube_name.dimension_name  
 セッション キューブに含まれる、基になるディメンションの完全修飾名です。  
  
 dimension_name  
 セッション キューブのディメンションの名前です。  
  
 \<句から dim >  
 派生ディメンションの定義でのみ指定できます。  
  
 NOT_RELATED_TO_FACTS  
 派生ディメンションの定義でのみ指定できます。  
  
 \<レベルの種類 >  
 派生ディメンションの定義でのみ指定できます。  
  
## <a name="remarks"></a>解説  
 サーバー キューブやローカル キューブと異なり、セッション キューブは、それを作成したセッションの期間を超えて保持されません。 セッション キューブは、それを定義するメジャーおよび定義を使用して定義されます。 ディメンションには次の 2 種類があります。  
  
-   ソース ディメンション - 1 つ以上のソース キューブの一部であったディメンションです。  
  
-   派生ディメンション - 新しい分析要素となるディメンションです。 派生ディメンションには、ソース ディメンションを垂直または水平にスライスすることによって定義した標準ディメンションと、独自にグループ化した複数のディメンション メンバーを含むディメンションがあります。 また、派生ディメンションは、データ マイニング モデルに基づくデータ マイニング ディメンションである場合もあります。  
  
> [!NOTE]  
>  Dimension キーワードは、ディメンションまたは階層を指します。  
  
 セッション キューブは、主に Microsoft Excel などのクライアント アプリケーションで属性メンバーをカスタム メンバー グループに動的にグループ化するために使用されます。 セッション キューブでは、次のタスクを実行できます。  
  
-   ソース キューブに存在するディメンションを削除する。  
  
-   ディメンションに階層を追加する、ディメンションから階層を削除する。  
  
-   メジャー グループまたは特定のメジャーを削除する。  
  
-   属性バインドに基づく新しい属性を追加して、既存の属性にグループを作成する。  
  
> [!IMPORTANT]  
>  セッション キューブ オブジェクトのセキュリティは、基になるソース オブジェクトのセキュリティを継承します。 セッション キューブは、アクションや計算スクリプトなど、その他のオブジェクトも継承します。  
  
 CREATE SESSION CUBE ステートメントは、以下の規則に従います。  
  
-   親子階層ではグループ化を実行できません。  
  
-   ROLAP ディメンションではグループ化を実行できません。  
  
-   リンク ディメンションではグループ化を実行できません。  
  
-   カスタム ロールアップを持つレベルではグループ化を実行できません。  
  
-   分離された属性階層ではグループ化を実行できません。  
  
-   不自然階層ではグループ化を実行できません。不自然階層とは、たとえば年齢と性別のようにレベル間での多対多のリレーションシップがある階層です。  
  
-   MDX スクリプト内でキューブ名を明示的に参照しても、セッション キューブでは名前が異なるためグループ化によって参照が無効になります。 代わりに CURRENTCUBE キーワードを使用してください。  
  
-   明示的な既定メンバーを持つディメンションではグループ化を実行できません。  
  
-   グループ化を実行すると、元のサーバー キューブのセッション スコープの計算されるメンバーは削除されます。  
  
-   サーバー キューブのキューブ ディメンションでグループ化を実行する場合、同じディメンションに基づくすべてのキューブ ディメンションに影響します。  
  
## <a name="example"></a>例  
 次の例では、Adventure Works キューブを基にして、Reseller Sales Amount メジャー、Reseller ディメンション、Product ディメンション、Geography ディメンション、および Date ディメンションを含むセッション スコープのキューブを作成します。 このセッション キューブ内では 2 つのグループが作成されます。1 つはヨーロッパ諸国を含み、もう 1 つは北米の国々を含みます。 このサンプルは、ユーザーがメンバーのカスタム グループを作成するときに Microsoft Excel が発行する CREATE SESSION CUBE ステートメントを簡略化したものです。  
  
```  
CREATE SESSION CUBE [Adventure Works_XL_GROUPING1]   
   FROM [Adventure Works]   
   ( MEASURE [Adventure Works].[Internet Sales Amount]  
   ,MEASURE [Adventure Works].[Reseller Sales Amount]  
   ,DIMENSION [Adventure Works].[Date].[Calendar]  
   ,DIMENSION [Adventure Works].[Date].[Calendar Year]  
   ,DIMENSION [Adventure Works].[Date].[Calendar Semester]  
   ,DIMENSION [Adventure Works].[Date].[Calendar Quarter]  
   ,DIMENSION [Adventure Works].[Date].[Month Name]  
   ,DIMENSION [Adventure Works].[Date].[Date]  
   ,DIMENSION [Adventure Works].[Geography].[Country]   
      HIDDEN AS _XL_GROUPING81  
   ,DIMENSION [Adventure Works].[Geography].[State-Province]  
   ,DIMENSION [Adventure Works].[Geography].[City]  
   ,DIMENSION [Adventure Works].[Geography].[Postal Code]  
   ,DIMENSION [Adventure Works].[Geography].[Geography]  
   ,DIMENSION [Adventure Works].[Product].[Product Categories]  
   ,DIMENSION [Adventure Works].[Product].[Category]  
   ,DIMENSION [Adventure Works].[Product].[Subcategory]  
   ,DIMENSION [Adventure Works].[Product].[Product]  
   ,DIMENSION [Adventure Works].[Product].[Product Key]  
   ,DIMENSION [Adventure Works].[Reseller].[Reseller]  
   ,DIMENSION [Adventure Works].[Reseller].[Geography Key]  
   ,DIMENSION [Geography].[Country]   
      NOT_RELATED_TO_FACTS FROM _XL_GROUPING81   
          ( LEVEL [(All)]  
         ,LEVEL [Country1] GROUPING  
         ,LEVEL [Country]  
            ,GROUP [Country1].[CountryXl_Grp_1]   
                ( MEMBER [Geography].[Country].&[Canada]  
                  ,MEMBER [Geography].[Country].&[United States] )  
            ,GROUP [Country1].[CountryXl_Grp_2]   
                ( MEMBER [Geography].[Country].&[France]  
                  ,MEMBER [Geography].[Country].&[Germany]  
                  ,MEMBER [Geography].[Country].&[United Kingdom] )   
            )   
   )  
```  
  
## <a name="see-also"></a>参照  
 [MDX データ定義ステートメント & #40 です。MDX と #41 です。](../mdx/mdx-data-definition-statements-mdx.md)   
 [GLOBAL CUBE ステートメント &#40; を作成します。MDX と #41 です。](../mdx/mdx-data-definition-create-global-cube.md)  
  
  


---
title: "ALTER CUBE ステートメント (MDX) |Microsoft ドキュメント"
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
- Cube
- ALTER_CUBE
- ALTER CUBE
- ALTER
dev_langs:
- kbMDX
helpviewer_keywords:
- ALTER CUBE statement
- cubes [Analysis Services], modifying
- modifying cubes
ms.assetid: 2f0af61b-f509-4e1a-990f-20a215d22994
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: e20832dac862a4a4973c4350c64efdd23a35b461
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="mdx-data-definition---alter-cube"></a>MDX データ定義に ALTER CUBE
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定されたキューブの構造を変更します。通常、ディメンションの書き戻しをサポートするために使用されます。 アプリケーションでの書き戻しの使用の詳細については、このブログの投稿を参照してください: [Analysis Services (ブログ) での書き戻しアプリケーションの構築](http://go.microsoft.com/fwlink/?LinkId=394977)  
  
 ディメンションの書き戻しを同時に実行すると、デッドロックが発生する可能性があります。この場合、最初の書き戻しがブロックされコミットできなくなります。これは、共有ロックが 2 番目の書き戻しによって保持されているためです。 このような状況では、エラーは生成されません。また、どのような操作も実行されません。 最終的には、タイムアウトと変更がロールバックされます。  
  
## <a name="syntax"></a>構文  
  
```  
  
ALTER CUBE  
      Cube_Name | CURRENTCUBE  
      <alter clause>   
            [ < alter clause> ...n]  
  
< alter clause> ::=   
   <create dimension member clause>   
  | <remove dimension member clause>  
  | <move dimension member clause>   
    | <update clause>   
    | <create cell calculation clause>  
  
<create dimension member clause> ::=  
CREATE DIMENSION MEMBER [ParentName.]MemberName  
    , [[KEY = Key_Value]   
    | [Property_Name = Property_Value[, ...n]]  
  
<dropping clause>::=  
DROP   
      DIMENSION MEMBER Member_Name   
            Member_Name ...n ]   
      [WITH DESCENDANTS]  
      | [ SESSION ] [ CALCULATED ] MEMBER Member_Name   
                  [ ,Member_Name,...n ]   
    | SET Set_Name  
                  [ ,Set_Name,...n ]   
    | [ SESSION ] CELL CALCULATION CellCalc_Name  
                  [ ,CellCalc_Name,...n ]   
    | ACTION Action_Name  
  
<move dimension member clause> ::=  
MOVE DIMENSION MEMBER MemberName  
        [, SKIPPED_LEVELS = Unsigned_Integer]   
      [WITH DESCENDANTS]  
    UNDER ParentName      
  
<update clause> ::=  
UPDATE   
    CUSTOM ROLLUP FOR MEMBER MemberName  
      [,MemberName, ...n] AS MDX_Expression  
   | DIMENSION Dimension_Name | Hierarchy_Name  
      , DEFAULT_MEMBER = MDX_Expression  
   | DIMENSION MEMBER MemberName AS  
   [MDX_Expression]  
   [Property_Name = Property_Value[, ...n]]  
  
<create cell calculation clause>::=  
CELL CALCULATION Calculation_Name   
   FOR Set_Expression AS MDX_Expression   
            [ [ CONDITION = 'Logical_Expression' ]   
    | [ DISABLED = { TRUE | FALSE } ]   
    | [ DESCRIPTION =String ]   
    | [ CALCULATION_PASS_NUMBER = Integer]   
    | [ CALCULATION_PASS_DEPTH = Integer]   
    | [ SOLVE_ORDER = Integer]   
    | [ Calculation_Name= Scalar_Expression ], ...n]  
```  
  
## <a name="creating-a-dimension-member"></a>ディメンション メンバーの作成  
 基になるディメンション テーブルに新しい行が追加されます。  
  
### <a name="arguments"></a>引数  
 *ParentName*  
 新しいディメンション メンバーの親の名前を指定する有効な文字列式です。ディメンション メンバーをルート以外の場所に作成する場合に指定します。  
  
 *メンバー名*  
 メンバー名を指定する有効な文字列式です。  
  
 *Key_Value*  
 新しいディメンション メンバーのキー値を定義する有効なスカラー式です。  
  
 *Property_Name*  
 メンバー プロパティを表す有効な多次元式 (MDX) 識別子です。  
  
 *Property_Value*  
 計算されるメンバー プロパティの値を定義する有効な多次元式 (MDX) スカラー式です。  
  
## <a name="dropping-a-dimension-member"></a>ディメンション メンバーを削除します。  
 書き込み可能なディメンションからディメンション メンバーを削除すると、基になるディメンション テーブルからそのメンバーおよび対応する行が削除されます。  
  
### <a name="arguments"></a>引数  
 *Cube_Name*  
 キューブの名前を指定する有効な文字列式です。  
  
 *Member_Name*  
 メンバー名またはメンバー キーを提供する有効な文字列式です。  
  
### <a name="remarks"></a>解説  
 WITH DESCENDANTS 句を使用しなかった場合、削除したメンバーの子は、削除したメンバーの親の子になります。 WITH DESCENDANTS 句を使用した場合、ディメンション テーブル内にあるすべての子孫および対応する行が削除されます。  
  
> [!NOTE]  
>  計算されるメンバー、名前付きセット、アクション、およびセル計算の削除については、次を参照してください。 [MEMBER ステートメントの削除 & #40 です。MDX と #41 です。](../mdx/mdx-data-definition-drop-member.md)、 [DROP SET ステートメント & #40 です。MDX と #41 です。](../mdx/mdx-data-definition-drop-set.md)、 [DROP ACTION ステートメント & #40 です。MDX と #41 です。](../mdx/mdx-data-definition-drop-action.md)、および[DROP CELL CALCULATION ステートメント & #40 です。MDX と #41 です。](../mdx/mdx-data-definition-drop-cell-calculation.md).  
  
## <a name="updating-the-default-dimension-member"></a>既定のディメンション メンバーの更新  
 この句では、キューブの既定のメンバーを更新します。この句は、MDX 計算スクリプトで既定のメンバーを定義するために使用されます。 データベース ディメンション、キューブ ディメンション、またはユーザー ログインの既定のメンバーを指定できます。 既定のメンバーは、セッション中に変更することもできます。  
  
### <a name="arguments"></a>引数  
 *Dimension_Name*  
 ディメンションの名前を指定する有効な文字列です。  
  
 *MDX_Expression*  
 メンバーを 1 つ返す有効な MDX 式です。  
  
### <a name="remarks"></a>解説  
 指定する MDX 式は、静的であっても動的であってもかまいません。  
  
## <a name="moving-a-dimension-member"></a>ディメンション メンバーの移動  
 基になるディメンション テーブルの行が変更されます。  
  
### <a name="arguments"></a>引数  
 *ParentName*  
 移動するディメンション メンバーの新しい親の名前を指定する有効な文字列式です。  
  
 *メンバー名*  
 メンバー名を指定する有効な文字列式です。  
  
 Unsigned _*整数*  
 スキップするレベル数を指定する有効な数値です。  
  
 WITH DESCENDANTS を指定した場合は、ツリー全体が移動されます。 WITH DESCENDANTS を指定しなかった場合、移動した親の子は、移動したメンバーの親の子になります。 移動を行うことによる影響は、簡単にいえば、基になるディメンション テーブルの親キー列の値を更新することです。  
  
## <a name="updating-a-dimension-member"></a>ディメンション メンバーの更新  
 UPDATE DIMENSION MEMBER 句を使用すると、メンバーのプロパティだけでなく、メンバーに関連付けられているカスタム メンバー式も変更できます。  
  
### <a name="arguments"></a>引数  
 *メンバー名*  
 メンバー名を指定する有効な文字列式です。  
  
 *MDX_Expression*  
 メンバーを 1 つ返す有効な MDX 式です。  
  
 *Property_Value*  
 計算されるメンバー プロパティの値を定義する有効な MDX スカラー式です。  
  
## <a name="creating-a-cell-calculation"></a>セル計算の作成  
 ALTER CUBE ステートメントを使用してセル計算の作成の詳細については、次を参照してください。 [CELL CALCULATION ステートメントの削除 & #40 です。MDX と #41 です。](../mdx/mdx-data-definition-drop-cell-calculation.md).  
  
## <a name="see-also"></a>参照  
 [MDX データ定義ステートメント & #40 です。MDX と #41 です。](../mdx/mdx-data-definition-statements-mdx.md)  
  
  


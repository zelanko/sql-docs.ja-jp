---
title: CREATE SET ステートメント (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4d1e58d016649c3c21a056a82315bd0d0fb3564f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63248387"
---
# <a name="mdx-data-definition---create-set"></a>MDX データ操作 - CREATE SET


  現在のキューブのセッションのスコープを持つ名前付きセットを作成します。  
  
## <a name="syntax"></a>構文  
  
```  
  
CREATE [SESSION] [ STATIC | DYNAMIC ] [HIDDEN] SET   
   CURRENTCUBE | Cube_Name  
      .Set_Name AS 'Set_Expression'  
      [,Property_Name = Property_Value, ...n]  
```  
  
## <a name="arguments"></a>引数  
 *Cube_Name*  
 キューブの名前を指定する有効な文字列式を指定します。  
  
 *Set_Name*  
 作成する名前付きセットの名前を指定する有効な文字列式です。  
  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *Property_Name*  
 セットのプロパティの名前を指定する有効な文字列です。  
  
 *Property_Value*  
 セットのプロパティの値を定義する有効なスカラー式です。  
  
## <a name="remarks"></a>コメント  
 名前付きセットは、ディメンション メンバー (またはセットを定義する式) のセットをもう一度使用するために作成します。 たとえば、売上高上位 10 ストアのセットで構成されるディメンション メンバーのセットを名前付きセットとして定義するとします。 静的にまたはなどの関数によって、このセットを定義できます[TopCount](../mdx/topcount-mdx.md)します。 この名前付きセットはし、上位 10 ストアのセットが必要な場合に使用できます。  
  
 CREATE SET ステートメントは、セッション全体で使用可能なに残っている名前付きセットを作成し、そのため、セッションで複数のクエリで使用することができます。 詳細については、次を参照してください。[セッション スコープの計算されるメンバー &#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/mdx-calculated-members-session-scoped-calculated-members.md)します。  
  
 1 つのクエリだけで使用する名前付きセットを定義することも可能です。 そのようなセットを定義する場合は、SELECT ステートメントで WITH 句を使用します。 WITH 句の詳細については、次を参照してください。[名前付きセットのクエリ&#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/mdx-named-sets-creating-query-scoped-named-sets.md)します。  
  
 *Set_Expression*句は MDX 構文をサポートする任意の関数を含めることができます。 SESSION 句を指定しない CREATE SET ステートメントで作成したセットは、セッションのスコープを設定します。 クエリ スコープによるセットを作成するには、WITH 句を使用してください。  
  
 現在接続されているキューブ以外に、キューブを指定するエラーが発生します。 そのため、現在のキューブを表すためにキューブ名の代わりに CURRENTCUBE を使用する必要があります。  
  
## <a name="scope"></a>スコープ  
 ユーザー定義のセットは、次の表の範囲のいずれかで発生します。  
  
 クエリ スコープ  
 セットの表示設定と有効期間は、クエリに限定されます。 セットは、個々 のクエリで定義されます。 クエリ スコープには、セッション スコープよりも優先されます。 詳細については、次を参照してください。[名前付きセットのクエリ&#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/mdx-named-sets-creating-query-scoped-named-sets.md)します。  
  
 セッション スコープ  
 可視性と、一連の有効期間を作成するセッションに限定されます。 (有効期間はセッションよりも小さい、セットに対して DROP SET ステートメントが実行された場合) です。CREATE SET ステートメントでは、セッション スコープのセットを作成します。 クエリ スコープによるセットを作成するには、WITH 句を使用してください。  
  
### <a name="example"></a>例  
 次の例では、Core Products というセットを作成します。 次に SELECT クエリによって、新しく作成されたセットの呼び出しを示しています。 SELECT クエリを実行できる、同じバッチ内でを実行できません - 前に、CREATE SET ステートメントを実行する必要があります。  
  
```  
CREATE SET [Adventure Works].[Core Products] AS '{[Product].[Category].[Bikes]}'  
  
SELECT [Core Products] ON 0  
  FROM [Adventure Works]  
```  
  
## <a name="set-evaluation"></a>評価を設定します。  
 異なる; が発生するセットの評価を定義することができます。セットの作成時を 1 回だけ定義できますか、セットが使用されるたびに発生することを定義できます。  
  
 STATIC  
 CREATE SET ステートメントが評価されるときに、セットを一度だけ評価することを示します。  
  
 DYNAMIC  
 クエリでセットが使用されるたびに、セットを評価することを示します。  
  
## <a name="set-visibility"></a>可視性の設定  
 セットには、キューブのクエリの表示またはにない他のユーザーを指定できます。  
  
 HIDDEN  
 セットが、キューブをクエリするユーザーに表示されないことを指定します。  
  
## <a name="standard-properties"></a>標準的なプロパティ  
 セットには、それぞれ既定のプロパティのセットがあります。 クライアント アプリケーションが接続したとき[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]管理者の選択に従って既定のプロパティはサポートされている、または、サポートされる使用可能ないずれか。  
  
|プロパティの識別子|説明|  
|-------------------------|-------------|  
|キャプション|セットのキャプションとしてクライアント アプリケーションが使用する文字列。|  
|DISPLAY_FOLDER|セットを表示するためにクライアント アプリケーションが使用する、表示フォルダーのパスを識別する文字列です。 フォルダー レベルの区切り記号は、クライアント アプリケーションによって定義されます。 ツールおよびクライアントによって提供される[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]、円記号 (\\) レベルの区切り記号です。 定義されたセットで複数の表示フォルダーを指定するには、セミコロン (;) を使用してフォルダーを区切ります。|  
  
## <a name="see-also"></a>参照  
 [DROP SET ステートメント&#40;MDX&#41;](../mdx/mdx-data-definition-drop-set.md)   
 [MDX データ定義ステートメント&#40;MDX&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  

---
title: CREATE MEMBER ステートメント (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 432438fe9a6e1b39c849188050b67f816d895187
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63250208"
---
# <a name="mdx-data-definition---create-member"></a>MDX データ操作 - CREATE MEMBER


  計算されるメンバーを作成します。  
  
## <a name="syntax"></a>構文  
  
```  
  
CREATE [ SESSION ] [HIDDDEN] [ CALCULATED ] MEMBER CURRENTCUBE | Cube_Name.Member_Name   
   AS MDX_Expression  
      [,Property_Name = Property_Value, ...n]  
......[,SCOPE_ISOLATION = CUBE]  
```  
  
## <a name="arguments"></a>引数  
 *Cube_Name*  
 メンバーを作成するキューブの名前を指定する有効な文字列式を指定します。  
  
 *Member_Name*  
 メンバー名を指定する有効な文字列式です。 ディメンション、メジャー ディメンション以外のディメンション内のメンバーを作成する完全修飾名を指定します。 完全に修飾されたメンバーの名前を指定しない場合は、メジャー ディメンション メンバーが作成されます。  
  
 *MDX_Expression*  
 有効な多次元式 (MDX) 式です。  
  
 *Property_Name*  
 計算されるメンバー プロパティの名前を指定する有効な文字列。  
  
 *Property_Value*  
 計算されるメンバー プロパティの値を定義する有効なスカラー式。  
  
## <a name="remarks"></a>コメント  
 CREATE MEMBER ステートメントは、セッション中に、複数のクエリでは、セッション全体で使用し、そのため、使用できる計算されるメンバーを定義します。 詳細については、次を参照してください。[セッション スコープの計算されるメンバー &#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/mdx-calculated-members-session-scoped-calculated-members.md)します。  
  
 1 つのクエリだけで使用する計算されるメンバーを定義することも可能です。 1 つのクエリに限定される計算されるメンバーを定義するには、SELECT ステートメントで WITH 句を使用します。 詳細については、次を参照してください。[クエリの計算されるメンバー &#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/mdx-calculated-members-query-scoped-calculated-members.md)します。  
  
 *Property_Name*標準またはオプションの計算されるメンバー プロパティのどちらかを参照できます。 標準のメンバー プロパティは、このトピックの一覧です。 計算されるメンバーをしない CREATE MEMBER で作成された、**セッション**値は、セッションのスコープを持ちます。 さらに、計算されるメンバーの定義に含まれる文字列は二重引用符で区切られます。 これは、OLE DB、単一引用符で文字列を区切る必要がありますを指定します。 これによって定義されたメソッドと異なります。  
  
 現在接続されているキューブ以外に、キューブを指定するエラーが発生します。 そのため、現在のキューブを表すためにキューブ名の代わりに CURRENTCUBE を使用する必要があります。  
  
 OLE DB によって定義されるメンバー プロパティの詳細については、OLE DB のドキュメントを参照してください。  
  
## <a name="scope"></a>スコープ  
 計算されるメンバーは、次の表の範囲のいずれかで発生します。  
  
 クエリ スコープ  
 計算されるメンバーの表示設定と有効期間は、クエリに限定されます。 そのような計算されるメンバーは、個々のクエリの中で定義します。 クエリ スコープには、セッション スコープよりも優先されます。 詳細については、次を参照してください。[クエリの計算されるメンバー &#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/mdx-calculated-members-query-scoped-calculated-members.md)します。  
  
 セッション スコープ  
 可視性と、計算されるメンバーの有効期間を作成するセッションに限定されます。 (有効期間はセッションよりも小さい、計算されるメンバーに対して DROP MEMBER ステートメントが実行された場合) です。CREATE MEMBER ステートメントでは、セッション スコープの計算されるメンバーを作成します。  
  
### <a name="scope-isolation"></a>スコープの分離  
 キューブの多次元式 (MDX) スクリプトには、計算されるメンバーが含まれている、既定では、計算されるメンバーが解決されないことも、セッション スコープの計算が解決される前に、クエリ定義されている計算の解決前に。  
  
> [!NOTE]  
>  特定のシナリオで、 [Aggregate (MDX)](../mdx/aggregate-mdx.md)関数と[VisualTotals (MDX)](../mdx/visualtotals-mdx.md)関数にはこの問題は発生しません。  
  
 この動作によって、汎用的なクライアント アプリケーションでは計算の実装方法を気にせずに複雑な計算を含むキューブを処理できます。 ただし、特定のシナリオで可能性がありますを実行するセッションまたは特定の計算前にクエリ スコープの計算されるメンバーであり、キューブのどちらも、**集計**関数も**VisualTotals**関数が適用されます。 これを実現するには、SCOPE_ISOLATION 計算プロパティを使用します。  
  
#### <a name="example"></a>例  
 次のスクリプトでは、SCOPE_ISOLATION 計算プロパティが正しい結果を生成するために必要なシナリオの例を示します。  
  
 **キューブの MDX スクリプト:**  
  
```  
CREATE MEMBER CURRENTCUBE.Measures.ProfitRatio AS 'Measures.[Store Sales]/Measures.[Store Cost]', SOLVE_ORDER = 10  
```  
  
 **MDX クエリ:**  
  
```  
WITH MEMBER [Customer].[Customers].[USA]. USAWithoutWA AS  
[Customer].[Customers].[Country].&[USA] - [Customer].[Customers].[State Province.&[WA], SOLVE_ORDER=5  
SELECT {USAWithoutWA} ON 0 FROM SALES  
WHERE ProfitRatio  
```  
  
 上のクエリでは、WA を除く USA の、出店コストに対する売上の比率を求めようとしています。 上のクエリでは目的の結果が返されず、USA の比率から WA の比率を引くという無意味な結果が返されます。 目的の結果を実現するために SCOPE_ISOLATION 計算プロパティを使用することができます。  
  
 **SCOPE_ISOLATION 計算プロパティを使用して MDX クエリ:**  
  
```  
WITH MEMBER [Customer].[Customers].[USA]. USAWithoutWA AS  
[Customer].[Customers].[Country].&[USA] - [Customer].[Customers].[State Province.&[WA], SOLVE_ORDER=5  
,SCOPE_ISOLATION=CUBE  
SELECT {USAWithoutWA} ON 0 FROM SALES  
WHERE ProfitRatio  
```  
  
## <a name="standard-properties"></a>標準的なプロパティ  
 計算されるメンバーには、それぞれ既定のプロパティのセットがあります。 クライアント アプリケーションが接続したとき[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]管理者の選択に従って既定のプロパティはサポートされている、または、サポートされる使用可能ないずれか。  
  
 使用可能なキューブの定義に応じて追加のメンバー プロパティがあります。 以下のプロパティは、キューブ内のディメンション レベルに関係する情報を表します。  
  
|プロパティの識別子|説明|  
|-------------------------|-------------|  
|SOLVE_ORDER|計算されるメンバーがもう 1 つの他の計算されるメンバーを参照する場合 (つまり、計算されるメンバーが互いに交差する場合) に、計算されるメンバーが解決される順序です。|  
|FORMAT_STRING|セルの値を表示するときに、クライアント アプリケーションが使用できる Office のスタイル書式指定文字列。|  
|表示されます。|計算されるメンバーがスキーマ行セットに表示されるかどうかを示す値。 表示では、メンバーのセットに追加できますされる計算される、 [AddCalculatedMembers](../mdx/addcalculatedmembers-mdx.md)関数。 0 以外の値は、計算されるメンバーが表示されていることを示します。 このプロパティの既定値は*Visible*します。<br /><br /> 表示されません (この値はゼロに設定) の計算されるメンバーより複雑な計算されるメンバーの途中のステップとして一般的に使用されます。 これらの計算されるメンバーは、メンバー、メジャーなどの他の種類によってにも参照できます。|  
|NON_EMPTY_BEHAVIOR|メジャーまたはセットを空のセルを解決するときに、計算されるメンバーの動作を決定するために使用します。<br /><br /> **\*\* 警告\* \*** このプロパティが非推奨とされます。 これを設定しないでください。 詳細については、「 [SQL Server 2016 に含まれている非推奨の Analysis Services 機能](../analysis-services/deprecated-analysis-services-features-in-sql-server-2016.md) 」を参照してください。|  
|キャプション|メンバーのキャプションとしてクライアント アプリケーションが使用する文字列です。|  
|DISPLAY_FOLDER|クライアント アプリケーションを使用して、メンバーを表示する表示フォルダーのパスを識別する文字列。 フォルダー レベルの区切り記号は、クライアント アプリケーションによって定義されます。 ツールおよびクライアントによって提供される[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]、円記号 (\\) レベルの区切り記号です。 定義されたメンバーで複数の表示フォルダーを指定するには、セミコロン (;) を使用してフォルダーを区切ります。|  
|ASSOCIATED_MEASURE_GROUP|このメンバーが関連付けられているメジャー グループの名前です。|  
  
## <a name="see-also"></a>関連項目  
 [DROP MEMBER ステートメント&#40;MDX&#41;](../mdx/mdx-data-definition-drop-member.md)   
 [UPDATE MEMBER ステートメント&#40;MDX&#41;](../mdx/mdx-data-definition-update-member.md)   
 [MDX データ定義ステートメント&#40;MDX&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  

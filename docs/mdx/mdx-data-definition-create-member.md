---
title: "CREATE MEMBER ステートメント (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE_MEMBER
- CREATE MEMBER
- Member
- CREATE
dev_langs: kbMDX
helpviewer_keywords:
- CREATE MEMBER statement
- calculated members [MDX]
ms.assetid: 49379217-be2c-4139-a206-1168078b9b76
caps.latest.revision: "55"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: 8a5c596238e605bf34b3c3c6cbaac5ebde803066
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="mdx-data-definition---create-member"></a>MDX データ定義のメンバーを作成します。
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
 メンバーを作成するキューブの名前を指定する有効な文字列式です。  
  
 *Member_Name*  
 メンバー名を指定する有効な文字列式です。 メジャー ディメンション以外のディメンション内にメンバーを作成するには、完全修飾名を指定します。 完全修飾メンバー名を指定しなかった場合、メンバーはメジャー ディメンション内に作成されます。  
  
 *MDX_Expression*  
 有効な多次元式 (MDX) 式です。  
  
 *Property_Name*  
 計算されるメンバー プロパティの名前を指定する有効な文字列。  
  
 *Property_Value*  
 計算されるメンバー プロパティの値を定義する有効なスカラー式です。  
  
## <a name="remarks"></a>解説  
 CREATE MEMBER ステートメントは、セッション全体で使用できる計算されるメンバーを定義します。作成した計算されるメンバーは、セッション内の複数のクエリで使用できます。 詳細については、次を参照してください。 [creating session-scoped 計算されるメンバーと #40 です。MDX と #41 です。](../analysis-services/multidimensional-models/mdx/mdx-calculated-members-session-scoped-calculated-members.md).  
  
 1 つのクエリだけで使用する計算されるメンバーを定義することも可能です。 1 つのクエリに限定される計算されるメンバーを定義するには、SELECT ステートメントで WITH 句を使用します。 詳細については、次を参照してください。 [Creating Query-Scoped 計算されるメンバーと #40 です。MDX と #41 です。](../analysis-services/multidimensional-models/mdx/mdx-calculated-members-query-scoped-calculated-members.md).  
  
 *Property_Name*標準またはオプションの計算されるメンバー プロパティのどちらかを参照できます。 標準のメンバー プロパティの一覧は、このトピックの後半にあります。 計算されるメンバーをしない CREATE MEMBER で作成された、**セッション**値はセッションのスコープを設定します。 また、計算されるメンバーの定義に含まれる文字列は、二重引用符で区切ります。 この点は、OLE DB によって定義される方法と異なっています。OLE DB では、文字列を単一引用符で区切るように指定されています。  
  
 現在接続しているキューブ以外のキューブを指定すると、エラーになります。 したがって、キューブ名の代わりに CURRENTCUBE を使用して、現在のキューブを確実に指定してください。  
  
 OLE DB によって定義されるメンバー プロパティの詳細については、OLE DB のドキュメントを参照してください。  
  
## <a name="scope"></a>スコープ  
 計算されるメンバーには、以下のいずれかのスコープを設定できます。  
  
 クエリ スコープ  
 計算されるメンバーの表示設定と有効期間は、クエリに限定されます。 そのような計算されるメンバーは、個々のクエリの中で定義します。 クエリ スコープは、セッション スコープよりも優先されます。 詳細については、次を参照してください。 [Creating Query-Scoped 計算されるメンバーと #40 です。MDX と #41 です。](../analysis-services/multidimensional-models/mdx/mdx-calculated-members-query-scoped-calculated-members.md).  
  
 セッション スコープ  
 計算されるメンバーの表示設定と有効期間は、メンバーが作成されたセッションに限定されます。 計算されるメンバーに対して DROP MEMBER ステートメントが実行された場合、有効期間はセッションよりも短くなります。CREATE MEMBER ステートメントで作成する計算されるメンバーは、セッション スコープです。  
  
### <a name="scope-isolation"></a>スコープの分離  
 キューブの多次元式 (MDX) スクリプトに計算されるメンバーが含まれる場合、既定では計算されるメンバーが解決されてから、セッション スコープの計算とクエリ定義の計算が解決されます。  
  
> [!NOTE]  
>  特定のシナリオで、 [Aggregate (MDX)](../mdx/aggregate-mdx.md)関数および[VisualTotals (MDX)](../mdx/visualtotals-mdx.md)関数にはこの問題は発生しません。  
  
 この動作によって、汎用的なクライアント アプリケーションでは計算の実装方法を気にせずに複雑な計算を含むキューブを処理できます。 ただし、特定のシナリオで可能性があります実行するセッションまたは特定の計算前にクエリ スコープの計算されるメンバーであり、キューブのどちらも、**集計**関数も**VisualTotals**関数も適用されます。 これを実現するには、SCOPE_ISOLATION 計算プロパティを使用します。  
  
#### <a name="example"></a>例  
 次のスクリプトは、正しい結果を得るために SCOPE_ISOLATION 計算プロパティが必要とされるシナリオの例です。  
  
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
  
 上のクエリでは、WA を除く USA の、出店コストに対する売上の比率を求めようとしています。 上のクエリでは目的の結果が返されず、USA の比率から WA の比率を引くという無意味な結果が返されます。 ここで目的の結果を得るには、SCOPE_ISOLATION 計算プロパティを使用できます。  
  
 **SCOPE_ISOLATION 計算プロパティを使用して MDX クエリ:**  
  
```  
WITH MEMBER [Customer].[Customers].[USA]. USAWithoutWA AS  
[Customer].[Customers].[Country].&[USA] - [Customer].[Customers].[State Province.&[WA], SOLVE_ORDER=5  
,SCOPE_ISOLATION=CUBE  
SELECT {USAWithoutWA} ON 0 FROM SALES  
WHERE ProfitRatio  
```  
  
## <a name="standard-properties"></a>標準のプロパティ  
 計算されるメンバーには、それぞれ既定のプロパティのセットがあります。 クライアント アプリケーションが接続されているときに[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]既定のプロパティは、サポートされている、または、サポートされるために使用できるように、管理者の選択します。  
  
 キューブの定義に応じて、追加のメンバー プロパティを使用できる場合があります。 以下のプロパティは、キューブ内のディメンション レベルに関係する情報を表します。  
  
|プロパティの識別子|意味|  
|-------------------------|-------------|  
|SOLVE_ORDER|計算されるメンバーがもう 1 つの他の計算されるメンバーを参照する場合 (つまり、計算されるメンバーが互いに交差する場合) に、計算されるメンバーが解決される順序です。|  
|FORMAT_STRING|A [!INCLUDE[msCoName](../includes/msconame-md.md)] Office スタイルの形式の文字列には、セルの値を表示するときにクライアント アプリケーションで使用できます。|  
|VISIBLE|計算されるメンバーがスキーマ行セットに表示されるかどうかを示す値です。 表示は、メンバーのセットに追加できますされる計算される、 [AddCalculatedMembers](../mdx/addcalculatedmembers-mdx.md)関数。 0 以外の値は、計算されるメンバーが表示されることを示します。 このプロパティの既定値は*Visible*です。<br /><br /> 表示されない (この値が 0 に設定されている) 計算されるメンバーは、一般には中間段階として、より複雑な計算されるメンバー内で使用されます。 これらの計算されるメンバーは、メジャーなど、他の種類のメンバーによって参照することもできます。|  
|NON_EMPTY_BEHAVIOR|空のセルを解決する場合の計算されるメンバーの動作を決定するために使用するメジャーまたはセットです。<br /><br /> **\*\*警告\* \*** このプロパティは推奨されなくなりました。 これを設定しないでください。 詳細については、「[SQL Server 2016 に含まれている非推奨の Analysis Services 機能](../analysis-services/deprecated-analysis-services-features-in-sql-server-2016.md)」を参照してください。|  
|CAPTION|メンバーのキャプションとしてクライアント アプリケーションが使用する文字列です。|  
|DISPLAY_FOLDER|メンバーを表示するためにクライアント アプリケーションが使用する、表示フォルダーのパスを識別する文字列です。 フォルダー レベルの区切り記号は、クライアント アプリケーションによって定義されます。 ツールおよびクライアントによって提供される[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]、円記号 (\\) は、レベルの区切り記号。 定義されたメンバーで複数の表示フォルダーを指定するには、セミコロン (;) を使用してフォルダーを区切ります。|  
|ASSOCIATED_MEASURE_GROUP|このメンバーが関連付けられているメジャー グループの名前です。|  
  
## <a name="see-also"></a>参照  
 [DROP MEMBER ステートメント &#40;です。MDX と #41 です。](../mdx/mdx-data-definition-drop-member.md)   
 [UPDATE MEMBER ステートメント &#40;です。MDX と #41 です。](../mdx/mdx-data-definition-update-member.md)   
 [MDX データ定義ステートメント &#40;です。MDX と #41 です。](../mdx/mdx-data-definition-statements-mdx.md)  
  
  

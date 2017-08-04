---
title: "CREATE SET ステートメント (MDX) |Microsoft ドキュメント"
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
- SET
- CREATE SET
- CREATE_SET
- CREATE
dev_langs:
- kbMDX
helpviewer_keywords:
- named sets [MDX]
- CREATE SET statement
ms.assetid: eff51eeb-5e7e-4706-b861-c57b6f3f89f0
caps.latest.revision: 42
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 12462e2b5a81c34e53332fa9749d698fecca36a8
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="mdx-data-definition---create-set"></a>MDX データ定義の設定の作成
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在のキューブのセッション スコープを使用して、名前付きセットを作成します。  
  
## <a name="syntax"></a>構文  
  
```  
  
CREATE [SESSION] [ STATIC | DYNAMIC ] [HIDDEN] SET   
   CURRENTCUBE | Cube_Name  
      .Set_Name AS 'Set_Expression'  
      [,Property_Name = Property_Value, ...n]  
```  
  
## <a name="arguments"></a>引数  
 *Cube_Name*  
 キューブの名前を指定する有効な文字列式です。  
  
 *Set_Name*  
 作成する名前付きセットの名前を指定する有効な文字列式です。  
  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *Property_Name*  
 セットのプロパティの名前を指定する有効な文字列です。  
  
 *Property_Value*  
 セットのプロパティの値を定義する有効なスカラー式です。  
  
## <a name="remarks"></a>解説  
 名前付きセットとは、再利用のために作成するディメンション メンバーのセット (またはセットを定義する式) です。 たとえば、売上高上位 10 ストアのセットで構成されるディメンション メンバーのセットを名前付きセットとして定義するとします。 静的には、やなどの関数によって、このセットを定義できます[TopCount](../mdx/topcount-mdx.md)です。 そのようにして作成した名前付きセットは、上位 10 ストアのセットが必要な場所で再利用できます。  
  
 CREATE SET ステートメントで作成する名前付きセットは、セッションが終了するまで使用できます。つまり、そのセッションの複数のクエリで再利用できるということです。 詳細については、次を参照してください。 [creating session-scoped 計算されるメンバーと #40 です。MDX と #41 です。](../analysis-services/multidimensional-models/mdx/mdx-calculated-members-session-scoped-calculated-members.md).  
  
 1 つのクエリだけで使用する名前付きセットを定義することも可能です。 そのようなセットを定義する場合は、SELECT ステートメントで WITH 句を使用します。 詳細については、WITH 句は、次を参照してください。 [Creating Query-Scoped 名前付きセット & #40 です。MDX と #41 です。](../analysis-services/multidimensional-models/mdx/mdx-named-sets-creating-query-scoped-named-sets.md).  
  
 *Set_Expression*句は MDX 構文をサポートするすべての関数を含めることができます。 SESSION 句を指定しない CREATE SET ステートメントで作成したセットは、セッション スコープになります。 クエリ スコープによるセットを作成するには、WITH 句を使用してください。  
  
 現在接続しているキューブ以外のキューブを指定すると、エラーになります。 したがって、キューブ名の代わりに CURRENTCUBE を使用して、現在のキューブを確実に指定してください。  
  
## <a name="scope"></a>スコープ  
 ユーザー定義セットには、以下のいずれかのスコープを設定できます。  
  
 クエリ スコープ  
 セットの表示設定と有効期間は、クエリに限定されます。 そのようなセットは、個々のクエリの中で定義します。 クエリ スコープは、セッション スコープよりも優先されます。 詳細については、次を参照してください。 [Creating Query-Scoped 名前付きセット & #40 です。MDX と #41 です。](../analysis-services/multidimensional-models/mdx/mdx-named-sets-creating-query-scoped-named-sets.md).  
  
 セッション スコープ  
 セットの表示設定と有効期間は、セットが作成されたセッションに限定されます (セットに対して DROP SET ステートメントが実行された場合、有効期間はセッションよりも短くなります)。CREATE SET ステートメントで作成するセットは、セッション スコープです。 クエリ スコープによるセットを作成するには、WITH 句を使用してください。  
  
### <a name="example"></a>例  
 次の例では、Core Products というセットが作成されます。 次に SELECT クエリによって、新しく作成されたセットの呼び出しを示しています。 CREATE SET ステートメントは、SELECT クエリを実行する前に実行する必要があります。この 2 つのステートメントは同じバッチ内では実行できません。  
  
```  
CREATE SET [Adventure Works].[Core Products] AS '{[Product].[Category].[Bikes]}'  
  
SELECT [Core Products] ON 0  
  FROM [Adventure Works]  
```  
  
## <a name="set-evaluation"></a>セットの評価  
 セットの評価は異なる方法で行うことができ、セットの作成時に一度だけ行うか、セットの使用時に毎回行うかを定義できます。  
  
 STATIC  
 CREATE SET ステートメントが評価されるときに、セットを一度だけ評価することを示します。  
  
 DYNAMIC  
 クエリでセットが使用されるたびに、セットを評価することを示します。  
  
## <a name="set-visibility"></a>セットの表示  
 キューブにクエリを実行する他のユーザーに対して、セットを表示するかどうかを指定できます。  
  
 HIDDEN  
 キューブにクエリを実行するユーザーに対して、セットを非表示にすることを指定します。  
  
## <a name="standard-properties"></a>標準のプロパティ  
 セットには、それぞれ既定のプロパティのセットがあります。 クライアント アプリケーションが接続されているときに[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]既定のプロパティは、サポートされている、または、サポートされるために使用できるように、管理者の選択します。  
  
|プロパティの識別子|意味|  
|-------------------------|-------------|  
|CAPTION|セットのキャプションとしてクライアント アプリケーションが使用する文字列。|  
|DISPLAY_FOLDER|セットを表示するためにクライアント アプリケーションが使用する、表示フォルダーのパスを識別する文字列です。 フォルダー レベルの区切り記号は、クライアント アプリケーションによって定義されます。 ツールおよびクライアントによって提供される[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]、円記号 (\\) は、レベルの区切り記号。 定義されたセットで複数の表示フォルダーを指定するには、セミコロン (;) を使用してフォルダーを区切ります。|  
  
## <a name="see-also"></a>参照  
 [DROP SET ステートメント & #40 です。MDX と #41 です。](../mdx/mdx-data-definition-drop-set.md)   
 [MDX データ定義ステートメント & #40 です。MDX と #41 です。](../mdx/mdx-data-definition-statements-mdx.md)  
  
  


---
title: "UPDATE MEMBER ステートメント (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- UPDATE_MEMBER
- UPDATE MEMBER
- MEMBER
- UPDATE
helpviewer_keywords:
- calculated members [MDX]
- UPDATE MEMBER statement
ms.assetid: 07ab708d-d165-4fb1-a9f9-fb8197ff0dab
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: e126f34be1f1cecd1a793b71ff4b64069c1802c3
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="mdx-data-definition---update-member"></a>MDX データ定義の更新プログラムのメンバー
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  既存の計算されるメンバーを更新します。  
  
## <a name="syntax"></a>構文  
  
```  
  
UPDATE MEMBER Cube_Name.Member_Name   
   AS MDX_Expression  
      [,Property_Name = Property_Value, ...n]  
......[,SCOPE_ISOLATION = CUBE]  
```  
  
## <a name="arguments"></a>引数  
 *Cube_Name*  
 メンバーを含むキューブの名前を指定する有効な文字列です。  
  
 *Member_Name*  
 既存のメンバーの名前を指定する有効な文字列です。  
  
 *MDX_Expression*  
 メンバーを更新する有効な多次元式 (MDX) 式です。  
  
 *Property_Name*  
 計算されるメンバーのプロパティの名前を指定する有効な文字列です。  
  
 *Property_Value*  
 計算されるメンバーのプロパティの値を指定する有効なスカラー式です。  
  
## <a name="remarks"></a>Remarks  
 UPDATE MEMBER ステートメントは、他の計算に対してこのメンバーの相対的な優先順位を維持しながら、既存の計算されるメンバーを更新します。 したがって、SOLVEORDER を変更するために UPDATE MEMBER ステートメントを使用することはできません。  
  
 キューブの MDX スクリプトでは、UPDATE MEMBER ステートメントを指定できません。  
  
 現在接続しているキューブ以外のキューブを指定すると、エラーになります。 したがって、キューブ名の代わりに CURRENTCUBE を使用して、現在のキューブを確実に指定してください。  
  
 OLE DB によって定義されるメンバー プロパティの詳細については、OLE DB のドキュメントを参照してください。  
  
## <a name="standard-properties"></a>標準のプロパティ  
 メンバーには、それぞれ既定のプロパティのセットがあります。 次の表は、これらの既定のプロパティを示しています。  
  
|プロパティの識別子|意味|  
|-------------------------|-------------|  
|FORMAT_STRING|A [!INCLUDE[msCoName](../includes/msconame-md.md)] Office スタイルの形式の文字列には、クライアント アプリケーションでセル値の表示に使用できます。|  
|VISIBLE|計算されるメンバーがスキーマ行セットに表示されるかどうかを示す値です。 表示は、メンバーのセットに追加できますされる計算される、 [AddCalculatedMembers](../mdx/addcalculatedmembers-mdx.md)関数。 0 以外の値は、計算されるメンバーが表示されることを示します。 このプロパティの既定値は*Visible*です。<br /><br /> 表示されない計算されるメンバーは、一般的には中間段階として、より複雑な計算されるメンバー内で使用されます。 これらの計算されるメンバーは、メジャーなど、他の種類のメンバーによって参照することもできます。|  
|NON_EMPTY_BEHAVIOR|空のセルを解決する場合の計算されるメンバーの動作を決定するために MDX が使用するメジャーまたはセットです。|  
|CAPTION|メンバーを表示するためにクライアント アプリケーションが使用するキャプションを指定する文字列値です。|  
|DISPLAY_FOLDER|クライアント アプリケーションによってメンバーが表示される、表示フォルダーのパスを指定する文字列値です。 フォルダー レベルの区切り記号は、クライアント アプリケーションによって定義されます。 ツールおよびクライアントによって提供される[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]、円記号 (\\) レベルの区切り記号として。 定義されたメンバーで複数の表示フォルダーを指定するには、セミコロン (;) を使用してフォルダーを区切ります。|  
|ASSOCIATED_MEASURE_GROUP|このメンバーが関連付けられているメジャー グループの名前です。|  
  
## <a name="see-also"></a>参照  
 [DROP MEMBER ステートメント &#40;です。MDX と #41 です。](../mdx/mdx-data-definition-drop-member.md)   
 [MEMBER ステートメント &#40; を作成します。MDX と #41 です。](../mdx/mdx-data-definition-create-member.md)   
 [MDX データ定義ステートメント &#40;です。MDX と #41 です。](../mdx/mdx-data-definition-statements-mdx.md)  
  
  

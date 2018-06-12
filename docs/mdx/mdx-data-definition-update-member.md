---
title: UPDATE MEMBER ステートメント (MDX) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 829aabfa7028814e20bcecd47a53495f6dc6bc6a
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34742711"
---
# <a name="mdx-data-definition---update-member"></a>MDX データ定義の更新プログラムのメンバー


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
  
## <a name="remarks"></a>コメント  
 UPDATE MEMBER ステートメントは、他の計算に対してこのメンバーの相対的な優先順位を維持しながら、既存の計算されるメンバーを更新します。 したがって、SOLVEORDER を変更するために UPDATE MEMBER ステートメントを使用することはできません。  
  
 キューブの MDX スクリプトでは、UPDATE MEMBER ステートメントを指定できません。  
  
 現在接続しているキューブ以外のキューブを指定すると、エラーになります。 したがって、キューブ名の代わりに CURRENTCUBE を使用して、現在のキューブを確実に指定してください。  
  
 OLE DB によって定義されるメンバー プロパティの詳細については、OLE DB のドキュメントを参照してください。  
  
## <a name="standard-properties"></a>標準のプロパティ  
 メンバーには、それぞれ既定のプロパティのセットがあります。 次の表は、これらの既定のプロパティを示しています。  
  
|プロパティの識別子|説明|  
|-------------------------|-------------|  
|FORMAT_STRING|セルの値を表示するクライアント アプリケーションが使用できる Office のスタイル書式指定文字列。|  
|VISIBLE|計算されるメンバーがスキーマ行セットに表示されるかどうかを示す値です。 表示は、メンバーのセットに追加できますされる計算される、 [AddCalculatedMembers](../mdx/addcalculatedmembers-mdx.md)関数。 0 以外の値は、計算されるメンバーが表示されることを示します。 このプロパティの既定値は*Visible*です。<br /><br /> 表示されない計算されるメンバーは、一般的には中間段階として、より複雑な計算されるメンバー内で使用されます。 これらの計算されるメンバーは、メジャーなど、他の種類のメンバーによって参照することもできます。|  
|NON_EMPTY_BEHAVIOR|空のセルを解決する場合の計算されるメンバーの動作を決定するために MDX が使用するメジャーまたはセットです。|  
|CAPTION|メンバーを表示するためにクライアント アプリケーションが使用するキャプションを指定する文字列値です。|  
|DISPLAY_FOLDER|クライアント アプリケーションによってメンバーが表示される、表示フォルダーのパスを指定する文字列値です。 フォルダー レベルの区切り記号は、クライアント アプリケーションによって定義されます。 ツールおよびクライアントによって提供される[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]、円記号 (\\) レベルの区切り記号として。 定義されたメンバーで複数の表示フォルダーを指定するには、セミコロン (;) を使用してフォルダーを区切ります。|  
|ASSOCIATED_MEASURE_GROUP|このメンバーが関連付けられているメジャー グループの名前です。|  
  
## <a name="see-also"></a>参照  
 [DROP MEMBER ステートメント&#40;MDX&#41;](../mdx/mdx-data-definition-drop-member.md)   
 [CREATE MEMBER ステートメント&#40;MDX&#41;](../mdx/mdx-data-definition-create-member.md)   
 [MDX データ定義ステートメント&#40;MDX&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  

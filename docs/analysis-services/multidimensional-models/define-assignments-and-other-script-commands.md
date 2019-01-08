---
title: 割り当てとその他のスクリプト コマンドの定義 |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4a96f96319c76c9c4d5a9b22a6e613ed8bf90cee
ms.sourcegitcommit: 38076f423663bdbb42f325e3d0624264e05beda1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/06/2018
ms.locfileid: "52983973"
---
# <a name="define-assignments-and-other-script-commands"></a>割り当てとその他のスクリプト コマンドの定義
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  キューブ デザイナーの **[計算]** タブで、ツール バーの **[新しいスクリプト コマンド]** アイコンをクリックして、空のスクリプトを作成します。 新しいスクリプトを作成すると、最初に [計算] タブの **[スクリプト オーガナイザー]** ペインに空のタイトルと共に表示されます。計算式ペインで入力する文字は、 **[スクリプト オーガナイザー]** でアイテムの名前として表示されます。 このため、最初の行にコメント付きの名前を入力すると、 **[スクリプト オーガナイザー]** ペインでスクリプトが識別しやすくなります。 詳細については、「 [Microsoft SQL Server 2005 の MDX スクリプトの紹介](http://go.microsoft.com/fwlink/?LinkId=81892)」を参照してください。  
  
> [!IMPORTANT]  
>  最初に、キューブ デザイナーの **[計算]** タブに切り替えると、 **[スクリプト オーガナイザー]** ペインには、CALCULATE コマンドを持つスクリプトが 1 つ含まれています。 CALCULATE コマンドは、キューブ内のセルの集計を制御し、キューブの集計方法を手動で指定する場合にのみ編集する必要があります。  
  
 計算式ペインを使用して、多次元式 (MDX) 構文で式を作成できます。 式の作成中は、キューブ コンポーネント、関数、およびテンプレートを **[計算ツール]** ペインから計算式ペインにドラッグまたはコピーできます。 これにより、アイテムのスクリプトが、それをドロップまたは貼り付ける場所で計算式ペインに追加されます。 引数とその区切り記号 (&#xAB; と &#xBB;) を適切な値に置換してください。  
  
> [!IMPORTANT]  
>  計算式ペインを使用して、複数のステートメントが含まれている式を書き込む場合は、MDX スクリプトの最後の行を除くすべての行がセミコロン (;) で終了していることを確認してください。 計算は、1 つの MDX スクリプトに連結され、各スクリプトにはセミコロンが追加されて、MDX スクリプトが正しくコンパイルされることが確認されます。 計算式ペインでスクリプトの最後の行にセミコロンを追加した場合、キューブは正しく作成および配置されますが、それに対してクエリを実行することはできません。  
  
## <a name="see-also"></a>参照  
 [多次元モデルの計算](../../analysis-services/multidimensional-models/calculations-in-multidimensional-models.md)  
  
  

---
title: ディメンションの属性に対するカスタム メンバー式の設定 |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: multidimensional-models
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 275d3db686926c779fca7b5b8ca7a291615ee1d6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="bi-wizard---custom-member-formulas-for-attributes-in-a-dimension"></a>BI ウィザード - ディメンションの属性に対するカスタム メンバー式
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  キューブまたはディメンションにカスタム メンバー式の拡張機能を追加して、多次元式 (MDX) の式の結果を持つディメンション メンバーに関連付けられている既定の集計を置換します  (この拡張機能により、ディメンションの指定した属性で **CustomRollupColumn** プロパティが設定されます)。  
  
> [!NOTE]  
>  カスタム メンバー式は、既存のデータ ソースを基にしたディメンションのみに使用できます。 データ ソースを使用せずに作成されたディメンションに対しては、スキーマ生成ウィザードを実行し、データ ソース ビューを作成してからカスタム メンバー式を追加する必要があります。  
  
 カスタム メンバー式を追加するには、ビジネス インテリジェンス ウィザードを使用して、 **[拡張機能の選択]** ページで **[カスタム メンバー式の作成]** オプションを選択します。 このウィザードでは、カスタム メンバー式の適用先となるディメンションを選択し、カスタム メンバー式を有効にする手順が示されます。  
  
## <a name="selecting-a-dimension"></a>ディメンションの選択  
 ウィザードの最初の **[カスタム メンバー式の作成]** ページで、カスタム メンバー式の適用先となるディメンションを指定します。 この選択したディメンションに追加されるカスタム メンバー式の拡張機能が、ディメンションへの変更内容になります。 これらの変更は、選択したディメンションを含むすべてのキューブによって継承されます。  
  
## <a name="enabling-a-custom-member-formula"></a>カスタム メンバー式の有効化  
 **[カスタム メンバー式の作成]** の 2 ページ目で、カスタム メンバー式が含まれている基になる列を、ディメンションの 1 つまたは複数の属性に関連付けます。 **[属性]** 列で、カスタム メンバー式の列に関連付ける属性の横のチェック ボックスをオンにします。 各属性を選択すると、ウィザードに **[列の選択]** ダイアログ ボックスが表示されます。 このダイアログ ボックスで、式が含まれているディメンション テーブルの列をクリックします。 **[列の選択]** ダイアログ ボックスを閉じた後で選択を変更する場合は、変更する **[基になる列]** セルをクリックし、省略記号 (**[...]**) をクリックして **[列の選択]** ダイアログ ボックスを再び開きます。  
  
## <a name="see-also"></a>参照  
 [ビジネス インテリジェンス ウィザードを使用したディメンションの拡張](http://msdn.microsoft.com/library/12d995d1-75ca-4890-bf4b-a2656910b8d0)  
  
  

---
title: 予測クエリを手動で編集 |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: aba181ab73ab730869eaa7930591cf21a947d20c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62679418"
---
# <a name="manually-edit-a-prediction-query"></a>手動での予測クエリの編集
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  予測クエリ ビルダーでクエリのデザインを終えたら、データ マイニング デザイナーの **[マイニング モデル予測]** タブにあるクエリ テキスト ビューに切り替えて、クエリを変更できます。 画面の下部に、クエリ ビルダーによって作成されたクエリを含んでいるテキスト エディターが表示されます。  
  
 クエリ テキスト ビューに切り替えると、クエリへの追加を行う場合に便利です。 たとえば、WHERE 句や ORDER BY 句を追加できます。  
  
 予測クエリ ビルダーのグリッドを使用してオブジェクトおよび列の名前を挿入し、個々の予測関数の構文を設定してから、手動編集モードに切り替えて、パラメーター値を変更します。  
  
> [!NOTE]  
>  **クエリ テキスト** ビューから **デザイン** ビューに戻ると、 **クエリ テキスト** ビューで行った変更は失われます。  
  
### <a name="modify-a-query"></a>クエリの変更  
  
1.  **のデータ マイニング デザイナーにある** [マイニング モデル予測] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]タブで、 **[SQL]** をクリックします。  
  
     画面の下部にあるグリッドが、クエリを含んでいるテキスト エディターに置き換わります。 このエディターでクエリの変更を入力できます。  
  
2.  クエリを実行するには、 **[マイニング モデル]** メニューの **[結果]** をクリックするか、クエリ結果に切り替えるボタンをクリックします。  
  
    > [!NOTE]  
    >  作成したクエリが無効であれば、[結果] ウィンドウにはエラーも結果も表示されません。 **[デザイン]** ボタンをクリックするか、 **[マイニング モデル]** メニューの **[デザイン]** または **[クエリ]** をクリックして問題を修正し、再度クエリを実行してください。  
  
## <a name="see-also"></a>参照  
 [データ マイニング クエリ](../../analysis-services/data-mining/data-mining-queries.md)   
 [予測クエリ ビルダー &#40;データ マイニング&#41;](http://msdn.microsoft.com/library/12900d49-db88-48bb-a5f4-0a9a172bc126)   
 [レッスン 6:予測の作成と操作&#40;基本的なデータ マイニング チュートリアル&#41;](http://msdn.microsoft.com/library/b213cb58-2c40-4c89-b08b-d3c36a4afad3)  
  
  

---
title: "マイニング構造に列を追加 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/13/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mining structures [Analysis Services], columns
- columns [data mining], mining structure columns
- adding columns
ms.assetid: 3f879344-9f66-4178-851a-e8c5ccccf4cb
caps.latest.revision: "30"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 5dfeade08192456bae474b633af9bd401dfa0fde
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="add-columns-to-a-mining-structure"></a>マイニング構造への列の追加
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]データ マイニング デザイナーを使用して[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]データ マイニング ウィザードで定義した後、マイニング構造に列を追加します。 マイニング構造の定義に使用したデータ ソース ビューに存在する列はどれでも追加できます。  
  
> [!NOTE]  
>  マイニング構造に列のコピーを複数追加することもできます。ただし、同じモデル内で 1 つの列のインスタンスが複数にならないようにし、ソースと派生列の間に誤った相関関係ができるのを防ぐ必要があります。  
  
### <a name="to-add-a-column-to-a-mining-structure"></a>マイニング構造に列を追加するには  
  
1.  データ マイニング デザイナーで **[マイニング構造]** タブを選択します。  
  
2.  マイニング構造を右クリックして **[列の追加]**を選択します。  
  
     **[列の選択]** ダイアログ ボックスが開きます。  
  
3.  **[基になるテーブル]**で、列が格納されているデータ ソース ビュー内のテーブルを選択します。  
  
4.  **[基になる列]**で、マイニング構造に追加する列を選択します。  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
> [!NOTE]  
>  既に存在する列を追加すると、構造にコピーが追加され、その名前に "1" が付加されます。 コピーされた列の名前をわかりやすい名前に変更するには、マイニング構造列の **[名前]** プロパティに新しい名前を入力します。  
  
## <a name="see-also"></a>参照  
 [マイニング構造のタスクと操作方法](../../analysis-services/data-mining/mining-structure-tasks-and-how-tos.md)  
  
  

---
title: 推定ディメンション メンバー (緩やかに変化するディメンション ウィザード) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.loaddimwizard.inferrdim.f1
ms.assetid: 809e395f-2e10-48ff-8860-56403f130628
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: aac7bf7d5ece29122f095f15bde5fa11255baa6c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36083462"
---
# <a name="inferred-dimension-members-slowly-changing-dimension-wizard"></a>[推定ディメンション メンバー] (緩やかに変化するディメンション ウィザード)
  **[推定ディメンション メンバー]** ダイアログ ボックスを使用すると、推定メンバーを使用するためのオプションを指定できます。 推定メンバーは、まだ読み込まれていないディメンション メンバーをファクト テーブルで参照するときに使用されます。 推定メンバーのデータが読み込まれると、新しいレコードを作成する代わりに、既存のレコードを更新できます。  
  
 このウィザードの詳細については、「 [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md)」を参照してください。  
  
## <a name="options"></a>および  
 **[推定メンバー サポートを有効にする]**  
 推定メンバーを有効にすることを選択した場合は、次のどちらかのオプションを選択する必要があります。  
  
 **[変化する型を持つすべての列を NULL とする]**  
 新しい推定メンバー レコード内で、変化する型を持つすべての列に NULL 値を入力するかどうかを指定します。  
  
 **[現在のレコードが推定メンバーであるかどうかの識別にブール型の列を使用する]**  
 現在のレコードが推定メンバーであるかどうかを示すために、既存のブール型の列を使用するかどうかを指定します。  
  
 **[推定メンバー インジケーター]**  
 上記の、推定メンバーであるかどうかの識別にブール型の列を使用することを選択した場合は、一覧から列を選択します。  
  
## <a name="see-also"></a>参照  
 [緩やかに変化するディメンション ウィザードを使用して出力を構成する](configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
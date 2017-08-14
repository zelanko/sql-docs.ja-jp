---
title: "[緩やかに変化するディメンション列]\\ (緩やかに変化するディメンション ウィザード) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.loaddimwizard.scdsupport.f1
ms.assetid: 36de99d5-5368-48e0-b876-17e9c6862c6c
caps.latest.revision: 23
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 0531f6420e00e284752be07dd44862ea117f1ffd
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="slowly-changing-dimension-columns-slowly-changing-dimension-wizard"></a>[緩やかに変化するディメンションの列]\ (緩やかに変化するディメンション ウィザード)
  **[緩やかに変化するディメンションの列]** ダイアログ ボックスを使用すると、緩やかに変化するディメンションの各列に対して変更の種類を選択できます。  
  
 このウィザードの詳細については、「 [Slowly Changing Dimension Transformation](../../../integration-services/data-flow/transformations/slowly-changing-dimension-transformation.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **[ディメンション列]**  
 ディメンション列を一覧から選択します。  
  
 **[変更の種類]**  
 **[固定属性]**を選択するか、変化する属性の 2 つのうちのいずれかを選択します。 列の値を変更しない場合は **[固定属性]** を使用します。 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] は、変更をエラーとして扱います。 **[変化する属性]** を使用して、既存の値を変更後の値で上書きします。 **[履歴属性]** を使用して、変更後の値を新しいレコードに保存し、前のレコードを期限切れにすることができます。  
  
 **[削除]**  
 ディメンション列を選択し、 **[削除]**をクリックして、マップされた列の一覧から削除します。  
  
## <a name="see-also"></a>参照  
 [出力を緩やかに変化するディメンション ウィザードを使用して構成します。](../../../integration-services/data-flow/transformations/configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  

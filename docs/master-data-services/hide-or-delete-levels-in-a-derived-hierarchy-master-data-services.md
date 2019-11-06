---
title: 派生階層のレベルを非表示にするか削除する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- derived hierarchies, hiding levels
- derived hierarchies, deleting levels
ms.assetid: e00582b9-9415-4b66-b4a7-9f590d83875f
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 0b6ce19214332e2a4f2ec85735657e7e55906c44
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67945244"
---
# <a name="hide-or-delete-levels-in-a-derived-hierarchy-master-data-services"></a>派生階層のレベルを非表示にするか削除する (マスター データ サービス)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で、レベルを使用してグループ化する必要があるが、レベルを表示する必要はない場合は、派生階層のレベルを非表示にします。 グループ化にレベルを使用しない場合はレベルを削除します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 この手順を実行するには  
  
-   **[システム管理]** 機能領域にアクセスする権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「 [管理者 &#40;マスター データ サービス&#41;](../master-data-services/administrators-master-data-services.md)にアクセスすることなくグループに対してユーザーの追加または削除を行うことができます。  
  
### <a name="to-hide-or-delete-levels-in-a-derived-hierarchy"></a>派生階層のレベルを非表示にするか削除するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。  
  
2.  メニュー バーの **[管理]** をポイントして **[派生階層]** をクリックします。  
  
3.  **[派生階層のメンテナンス]** ページの **[モデル]** の一覧からモデルを選択します。  
  
4.  編集する派生階層の列を選択します。  
  
5.  **[編集]** をクリックします。  
  
6.  **[現在のレベル]** ペインで、次のいずれかを実行します。  
  
    -   レベルを非表示にするには、最上位または最下位以外のレベルをクリックします。 **[表示]** ボックスの一覧で **[いいえ]** を選択します。 **[選択した階層アイテムの保存]** をクリックします。  
  
    -   最上位レベルを削除するには、 **[選択した階層アイテムの削除]** をクリックします。 確認のダイアログ ボックスで **[OK]** をクリックします。 削除できるのは最上位レベルだけです。  
  
## <a name="see-also"></a>関連項目  
    
 [派生階層 (マスター データ サービス)](../master-data-services/derived-hierarchies-master-data-services.md)  
  
  

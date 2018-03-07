---
title: "派生階層のレベルを非表示にするか削除する (マスター データ サービス) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: non-specific
ms.reviewer: 
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- derived hierarchies, hiding levels
- derived hierarchies, deleting levels
ms.assetid: e00582b9-9415-4b66-b4a7-9f590d83875f
caps.latest.revision: 
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f6bfe02b83b677275385f6c712b26438e9a17cea
ms.sourcegitcommit: 6ac1956307d8255dc544e1063922493b30907b80
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2018
---
# <a name="hide-or-delete-levels-in-a-derived-hierarchy-master-data-services"></a>派生階層のレベルを非表示にするか削除する (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で、レベルを使用してグループ化する必要があるが、レベルを表示する必要はない場合は、派生階層のレベルを非表示にします。 グループ化にレベルを使用しない場合はレベルを削除します。  
  
## <a name="prerequisites"></a>Prerequisites  
 この手順を実行するには  
  
-   **[システム管理]** 機能領域にアクセスする権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「 [管理者 (マスター データ サービス)](../master-data-services/administrators-master-data-services.md)にアクセスすることなくグループに対してユーザーの追加または削除を行うことができます。  
  
### <a name="to-hide-or-delete-levels-in-a-derived-hierarchy"></a>派生階層のレベルを非表示にするか削除するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]**をクリックします。  
  
2.  メニュー バーの **[管理]** をポイントして **[派生階層]**をクリックします。  
  
3.  **[派生階層のメンテナンス]** ページの **[モデル]** の一覧からモデルを選択します。  
  
4.  編集する派生階層の列を選択します。  
  
5.  **[編集]**をクリックします。  
  
6.  **[現在のレベル]** ペインで、次のいずれかを実行します。  
  
    -   レベルを非表示にするには、最上位または最下位以外のレベルをクリックします。 **[表示]** ボックスの一覧で **[いいえ]**を選択します。 **[選択した階層アイテムの保存]**をクリックします。  
  
    -   最上位レベルを削除するには、 **[選択した階層アイテムの削除]**をクリックします。 確認のダイアログ ボックスで **[OK]**をクリックします。 削除できるのは最上位レベルだけです。  
  
## <a name="see-also"></a>参照  
    
 [派生階層 (マスター データ サービス)](../master-data-services/derived-hierarchies-master-data-services.md)  
  
  

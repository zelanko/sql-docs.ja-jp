---
title: "[パスワードの入力] ページ (レプリカ追加ウィザード) | Microsoft Docs"
ms.custom: 
ms.date: 05/17/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.addreplicawizard.enterpasswords.f1
ms.assetid: e69207a0-c5c4-44e4-ae9a-4afbb67251d1
caps.latest.revision: 7
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 0e89f1cedff6ee8b3a18e78ce08d5090331a5694
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="enter-passwords-page-add-replica-wizard"></a>[パスワードの入力] ページ (レプリカ追加ウィザード)
  このヘルプ トピックでは、 **[パスワードの入力]** ページのオプションについて説明します。 このトピックの対象は、 [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)] の [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]です。  
  
 **[レプリカの指定]** ページで選択したレプリカに、データベース マスター キーがあるデータベースが含まれている場合は、[パスワードの入力] ページが表示されます。  
  
## <a name="enter-passwords-options"></a>パスワード入力オプション  
 **[この SQL Server のインスタンス上のユーザー データベース]** グリッドには、すべてのローカル ユーザー データベースが表示されます。 次の列で構成されます。  
  
 **名前**  
 ローカル ユーザー データベースの名前が表示されます。  
  
 **サイズ**  
 データベースのサイズが表示されます (サイズをウィザードで使用できる場合)。  
  
 **[状態]**  
 データベース マスターキーがあるデータベースに対して " **パスワードが必要です** " と表示されます。 データベース マスター キーのパスワードを **[パスワード]** 列に入力し、 **[更新]**をクリックします。 パスワードを正しく入力した場合、 **[状態]** 列に **[パスワードが入力されました]**が表示されます。  
  
 データベースにデータベース マスター キーがない場合、 **[状態]** 列には **[パスワードは必要ありません]**が表示されます。  
  
 **Password**  
 **[状態]** 列に " **パスワードが必要です**" と表示されている場合は、データベース マスター キーのパスワードを入力します。  
  
 **[更新]**  
 クリックしてグリッドを最新の情報に更新します。 これは、必要なパスワードを入力した後で役に立ちます。  
  
## <a name="related-tasks"></a>関連タスク  
  
-   [可用性グループへのレプリカ追加ウィザードの使用 &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループの前提条件、制限事項、および推奨事項 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md)  
  
  


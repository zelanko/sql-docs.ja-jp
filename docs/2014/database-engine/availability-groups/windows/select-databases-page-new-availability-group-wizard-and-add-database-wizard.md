---
title: '[データベースの選択] ページ (新しい可用性グループウィザード-データベース追加ウィザード) |Microsoft Docs'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.adddatabasewizard.selectdatabases.f1
- sql12.swb.newagwizard.selectdatabases.f1
ms.assetid: 929c5e15-d087-438d-b1f2-aa97c5f8bff8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a2c6cdeb27dfd1768c9a494497f5b2b1e0b7350a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "62788499"
---
# <a name="select-databases-page-new-availability-group-wizard-add-database-wizard"></a>[データベースの選択] ページ (新しい可用性グループウィザード-データベース追加ウィザード)
   このヘルプ トピックでは、**[データベースの指定]** ページのオプションについて説明します。 このトピックの対象は、 [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] の [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] と [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]です。  
  
##  <a name="select-databases-options"></a><a name="PageOptions"></a> データベース オプションの選択  
 **[この SQL Server のインスタンス上のユーザー データベース]** グリッドには、すべてのローカル ユーザー データベースが表示されます。 次の列で構成されます。  
  
 **名前**  
 ローカル ユーザー データベースの名前が表示されます。  
  
 **[サイズ]**  
 データベースのサイズが表示されます (サイズをウィザードで使用できる場合)。  
  
 **状態**  
 可用性グループに追加するための前提条件を特定のデータベースが満たしているかどうかを示すハイパーリンクが表示されます。 状態が **[前提条件を満たしています]** の場合、データベースを可用性グループに追加できます。 データベースが一部の前提条件を満たしていない場合は、 **[状態]** ハイパーリンクにデータベースが不適格である理由が簡潔に示されます。 詳細については、ハイパーリンクをクリックしてください。  
  
 前提条件を満たすためにデータベースを操作したままで、 **[データベースの選択]** ページでウィザードを終了できます。 **[データベースの選択]** ページに戻ったら、 **[最新の情報に更新]** をクリックしてグリッドを更新します。  
  
 **更新**  
 クリックしてグリッドを最新の情報に更新します。 前提条件を満たすためにデータベースを操作した後で役立ちます。  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> 関連タスク  
  
-   [[新しい可用性グループ] ダイアログ ボックスの使用 &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [可用性グループへのデータベース追加ウィザードの使用 &#40;SQL Server Management Studio&#41;](availability-group-add-database-to-group-wizard.md)  
  
## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [AlwaysOn 可用性グループ &#40;SQL Server の前提条件、制限事項、推奨事項&#41;](prereqs-restrictions-recommendations-always-on-availability.md)  
  
  

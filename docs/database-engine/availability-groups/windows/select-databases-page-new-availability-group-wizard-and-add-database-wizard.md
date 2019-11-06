---
title: '[データベースの選択] ページ (新しい可用性グループ ウィザードおよびデータベース追加ウィザード) | Microsoft Docs'
ms.custom: ''
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql13.swb.adddatabasewizard.selectdatabases.f1
- sql13.swb.newagwizard.selectdatabases.f1
ms.assetid: 929c5e15-d087-438d-b1f2-aa97c5f8bff8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 04836a29531c1eaab61277891e22e31b669d9ffd
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68014189"
---
# <a name="select-databases-page-new-availability-group-wizard-and-add-database-wizard"></a>[データベースの選択] ページ (新しい可用性グループ ウィザードおよびデータベース追加ウィザード)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  このヘルプ トピックでは、 **[データベースの指定]** ページのオプションについて説明します。 このトピックの対象は、 [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] の [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] と [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]です。  
  
##  <a name="PageOptions"></a> データベース オプションの選択  
 **[この SQL Server のインスタンス上のユーザー データベース]** グリッドには、すべてのローカル ユーザー データベースが表示されます。 次の列で構成されます。  
  
 **[名前]**  
 ローカル ユーザー データベースの名前が表示されます。  

 **[サイズ]**  
 データベースのサイズが表示されます (サイズをウィザードで使用できる場合)。  
  
 **ステータス**  
 可用性グループに追加するための前提条件を特定のデータベースが満たしているかどうかを示すハイパーリンクが表示されます。 状態が **[前提条件を満たしています]** の場合、データベースを可用性グループに追加できます。 データベースが一部の前提条件を満たしていない場合は、 **[状態]** ハイパーリンクにデータベースが不適格である理由が簡潔に示されます。 詳細については、ハイパーリンクをクリックしてください。  
  
 前提条件を満たすためにデータベースを操作したままで、 **[データベースの選択]** ページでウィザードを終了できます。 **[データベースの選択]** ページに戻ったら、 **[最新の情報に更新]** をクリックしてグリッドを更新します。  
  
 **パスワード**  
 データベースにデータベース マスター キーが含まれている場合は、データベース マスター キーのパスワードを入力します。  
  
 **[最新の情報に更新]**  
 クリックしてグリッドを最新の情報に更新します。 前提条件を満たすためにデータベースを操作した後で役立ちます。  
  
##  <a name="RelatedTasks"></a> 関連タスク  
  
-   [[新しい可用性グループ] ダイアログ ボックスの使用 &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [可用性グループへのデータベース追加ウィザードの使用 &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/availability-group-add-database-to-group-wizard.md)  
  
## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループの概要 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Always On 可用性グループの前提条件、制限事項、および推奨事項 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md)  
  
  

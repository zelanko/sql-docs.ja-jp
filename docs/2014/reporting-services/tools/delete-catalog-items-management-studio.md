---
title: カタログ アイテムの削除 (Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.deleteitems.f1
ms.assetid: b0599e01-6dc3-4484-80d4-022a412e0ebd
caps.latest.revision: 15
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 31ca797c34be8624c5d47ea874439167c5dbeede
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37315982"
---
# <a name="delete-catalog-items-management-studio"></a>カタログ アイテムの削除 (Management Studio)
  このページを使用すると、共有スケジュールとロール定義を削除できます。  
  
 複数のレポートおよびサブスクリプションによって使用される共有スケジュールを削除した場合、以前にその共有スケジュールを使用していたレポートおよびサブスクリプションごとに別個のスケジュールが作成されます。 新たに作成される各スケジュールには、共有スケジュールで指定されていた日付、時刻、および定期的なパターンが保持されます。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] には、個々のスケジュールを一元管理する手段は存在しません。 共有スケジュールを削除した場合、それ以降は、各アイテムのスケジュール情報を個別に管理する必要があります。 共有スケジュールを削除する前に、使用して、[レポート ページ](schedule-properties-reports-page.md)レポートは、共有スケジュールを現在使用しているかを判断します。  
  
 ロール定義のうち削除できるのは、ロールの割り当てに現在使用されていないものだけです。 現在使用されているロールを削除しようとすると、レポート サーバーでロールが削除されずにエラー メッセージが表示されます。 このページに含まれるロール定義が 1 つだけで、それが現在使用されていない場合、 **[OK]** をクリックするとその定義が削除されます。 このページに複数のロールが含まれている場合、保持するロールと削除するロールを選択することはできません。 **[OK]** をクリックすると、使用されていないロール定義がすべて削除されます。  
  
 削除操作は元に戻せません。 削除したアイテムを復旧するには、そのアイテムを再作成するか、レポート サーバー データベースのバックアップ コピーを復元する必要があります。  
  
## <a name="options"></a>および  
 **名前**  
 削除するアイテムの名前を指定します。  
  
 **型**  
 削除するアイテムの種類を表示します。  
  
 **所有者**  
 所有者の名前を表示します。 ほとんどの場合は [システム] です。  
  
 **ステータス**  
 削除操作の進行状況を表示します。  
  
 **Error**  
 アイテムの削除中にエラーが発生した場合はエラー コードを表示します。  
  
## <a name="see-also"></a>参照  
 [アイテムの削除&#40;Management Studio&#41;](delete-an-item-management-studio.md)   
 [Management Studio のレポート サーバーの F1 ヘルプ](report-server-in-management-studio-f1-help.md)   
 [スケジュールの作成、変更、および削除](../subscriptions/create-modify-and-delete-schedules.md)  
  
  

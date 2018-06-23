---
title: レポートおよびサブスクリプションの処理を一時停止 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pausing schedules
- subscriptions [Reporting Services], pausing
- report processing [Reporting Services], pausing
- shared data sources [Reporting Services]
- pausing subscription processing
- pausing report processing
- temporarily stopping report processing
- disabling shared data sources
- roles [Reporting Services], modifying
- shared schedules [Reporting Services], pausing
ms.assetid: 3cf9a240-24cc-46d4-bec6-976f82d8f830
caps.latest.revision: 38
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: a10c8a9b2d23ea5d4803dfc97911cc5695b26b38
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36085819"
---
# <a name="pause-report-and-subscription-processing"></a>レポートとサブスクリプションの処理を一時停止する
  レポートまたはサブスクリプションを直接一時停止することはできません。 ただし、処理の開始前、またはデータ ソースへの接続時に、レポートおよびサブスクリプションの処理を中断できます。 また、レポートやサブスクリプションにユーザーがアクセスできないようにして、レポートやサブスクリプションが処理されないようにすることもできます。  
  
 以下の操作は、一時的な処理の中断に使用できます。  
  
## <a name="modify-role-assignments-to-prevent-access"></a>アクセス防止のためのロールの割り当ての変更  
 レポートを使用できないようにする最善の方法は、レポートにアクセスするためのロールの割り当てを一時的に削除することです。 この方法は、データ ソースへの接続方法に関係なくすべてのレポートに使用できます。 この方法は、ロールの割り当てを一時的に削除したレポートのみに有効で、他のレポートやアイテムの操作には影響しません。  
  
 ロールの割り当てを削除するには、レポート マネージャーでレポートの [セキュリティ] プロパティ ページを開きます。 そのレポートが親レポートからセキュリティを継承している場合は、 **[アイテムのセキュリティを編集]** をクリックして、広範囲なアクセスを提供するロールの割り当てを削除する、制限付きのセキュリティ ポリシーを作成できます。たとえば、Everyone にアクセスを提供するロールの割り当てを削除し、Administrators など小さなユーザー グループにアクセスを提供するロールの割り当てを保持できます。  
  
## <a name="disable-a-shared-data-source"></a>共有データ ソースを無効にします。  
 共有データ ソースを使用する利点の 1 つは、共有データ ソースを無効にして、レポートまたはデータ ドリブン サブスクリプションの実行を中止できることです。 共有データ ソースを無効にすると、レポートは外部ソースから切断されます。 共有データ ソースが無効な間は、すべてのレポートと共有データ ソースを使用するサブスクリプションで共有データ ソースを使用できません。 共有データ ソースを無効にするレポート マネージャーで、データ ソースを開くし、クリア、**このデータ ソースを有効にする**チェック ボックスをオンします。  
  
 データ ソースが使用できない場合でも、レポートは読み込まれることに注意してください。 レポートにはデータは含まれていませんが、適切な権限を持ったユーザーは、レポートに関連付けられたプロパティ ページ、セキュリティ設定、レポート履歴、およびサブスクリプション情報にアクセスできます。  
  
## <a name="pause-a-shared-schedule"></a>共有スケジュールの一時停止  
 レポートまたはサブスクリプションが共有スケジュールから実行される場合、スケジュールを一時停止して処理を中止できます。 すべてのレポートとは、スケジュールで実行されるサブスクリプションの処理は、スケジュールが再開されるまで遅延します。 詳細については、次を参照してください。[一時停止と再開共有スケジュール](schedules.md)です。  
  
## <a name="see-also"></a>参照  
 [Reporting Services レポート サーバー (ネイティブ モード)](../report-server/reporting-services-report-server-native-mode.md)   
 [レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../report-manager-ssrs-native-mode.md)   
 [[セキュリティのプロパティ] ページ、アイテム (レポート マネージャー)](../security-properties-page-items-report-manager.md)  
  
  
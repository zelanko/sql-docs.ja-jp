---
title: '[スケジュール] ページ (レポートマネージャー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ef19d96e-9f00-4434-950e-152dda9c1ced
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 927a9fc96e11bffdcacf7a12f09ee93d25f153fd
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66102315"
---
# <a name="schedules-page-report-manager"></a>[スケジュール] ページ (レポート マネージャー)
  [スケジュール] ページでは、共有スケジュールを作成、変更、削除、一時停止、または再開できます。 共有スケジュールとは、レポート、サブスクリプション、およびスケジュール情報を利用するその他のプロセスとは別に作成および管理できる名前付きのスケジュールです。 追加した共有スケジュールは、全ユーザーが選択できます。  
  
 共有スケジュールを削除、一時停止、または再開するには、該当する共有スケジュールの横にあるチェック ボックスをオンにします。  
  
> [!NOTE]  
>  この機能は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のすべてのエディションで使用できるわけではありません。 の[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]各エディションでサポートされる機能の一覧については、「 [SQL Server 2014 の各エディションがサポートする機能](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」を参照してください。  
  
## <a name="navigation"></a>「ナビゲーション」  
 ユーザー インターフェイス (UI) のこの場所に移動するには、次の手順に従います。  
  
### <a name="to-open-the-schedules-page"></a>[スケジュール] ページを開くには  
  
1.  レポート マネージャーを開きます。  
  
2.  ページの右上隅の **[サイトの設定]** をクリックします。 この操作により、サイトの [全般] プロパティ ページが開きます。  
  
3.  **[スケジュール]** タブをクリックします。  
  
## <a name="options"></a>オプション  
 **新しいスケジュール**  
 クリックすると、[スケジュール] ページが開きます。このページは、頻度に関する情報の指定に使用します。  
  
 **削除**  
 共有スケジュールを削除する場合にクリックします。  
  
 **一時停止**  
 共有スケジュールの実行を一時的に停止する場合にクリックします。 スケジュールを一時停止することで、サブスクリプションおよびスケジュール設定されているその他の処理が実行されなくなります。  
  
 **よる**  
 共有スケジュールを再度設定する場合にクリックします。 スケジュールを一時停止している間に実行される予定だった無効になった処理は、破棄されます。  
  
 **スケジュール**  
 現在定義されている共有スケジュールが表示されます。 頻度に関する情報を表示または編集するには、共有スケジュールをクリックします。  
  
 **作成者**  
 共有スケジュールを作成したユーザーの名前が表示されます。  
  
 **[最終実行]、[次の実行]**  
 共有スケジュールが最後に実行された日時と、次に実行される日時が表示されます。  
  
 **状態**  
 共有スケジュールが一時停止されているか、稼動中かが表示されます。  
  
## <a name="see-also"></a>参照  
 [Create, Modify, and Delete Schedules](subscriptions/create-modify-and-delete-schedules.md)   
 [レポート マネージャー F1 ヘルプ](../../2014/reporting-services/report-manager-f1-help.md)  
  
  

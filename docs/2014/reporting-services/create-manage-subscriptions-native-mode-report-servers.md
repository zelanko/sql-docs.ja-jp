---
title: ネイティブ モード レポート サーバーのサブスクリプションの作成と管理 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [Reporting Services], managing
ms.assetid: 7f46cbdb-5102-4941-bca2-5e0ff9012c6b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d6f18ff05cf6283e4358e8f8afd76a5858b0b41a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66109598"
---
# <a name="create-and-manage-subscriptions-for-native-mode-report-servers"></a>ネイティブ モード レポート サーバーのサブスクリプションの作成と管理
  このセクションでは、サブスクリプションの処理、管理、および制御について説明します。 サブスクリプションの管理は、標準のサブスクリプションとデータ ドリブン サブスクリプションで異なります。 標準のサブスクリプションは、通常、ユーザーが所有および管理します。 一方、データ ドリブン サブスクリプションは、通常、レポート サーバー管理者が作成およびメンテナンスします。  
  
 サブスクリプション機能および配信機能は、既定で使用できます (電子メールの配信は構成しないと使用できません)。 既定の配信拡張機能には、レポート サーバーの電子メールおよびファイル共有の配信が含まれます。 カスタム配信拡張機能を作成またはインストールしない限り、ネイティブ モードのレポート サーバー上のサブスクリプションに使用できる配信方法は、これらの既定の配信拡張機能のみとなります。  
  
## <a name="permissions-for-subscribing-to-reports-on-a-native-mode-report-server"></a>ネイティブ モードのレポート サーバーからレポートをサブスクライブするための権限  
 ロールの使用方法に応じて、異なるロールのサブスクリプション タスクを有効または無効にすることにより、選択したユーザー グループにサブスクリプション機能を指定できます。 サブスクリプション機能をユーザーが使用するには、以下の 2 つのタスクを使用します。  
  
-   "個別のサブスクリプションを管理" タスクでは、ユーザーが特定のレポートのサブスクリプションを作成、変更、および削除できます。 定義済みのロールである閲覧者ロールとレポート ビルダー ロールには、このタスクが含まれています。 このタスクを含むロールの割り当てを使用すると、ユーザーは自分が作成するサブスクリプションのみを管理できます。  
  
-   "すべてのサブスクリプションを管理" タスクでは、ユーザーがすべてのサブスクリプションにアクセスしてそれらを変更できます。 このタスクは、データ ドリブン サブスクリプションを作成する場合に必要です。 定義済みのロールでは、コンテンツ マネージャー ロールにのみ、このタスクが含まれます。  
  
## <a name="disabling-subscriptions"></a>サブスクリプションの無効化  
 ユーザーがサブスクリプションを作成できないようにするには、ロールから "個別のサブスクリプションを管理" タスクをオフにします。 このタスクを削除すると、[サブスクリプション] ページは使用できなくなります。 レポート マネージャーでは、[個人用サブスクリプション] ページには、既にサブスクリプションが含まれていても、何も表示されません (このページは削除できません)。 サブスクリプション関連タスクを削除すると、ユーザーはサブスクリプションを作成および変更できなくなりますが、既存のサブスクリプションは削除されません。 既存のサブスクリプションは、削除するまで引き続き実行されます。 サブスクリプションの削除の詳細については、「[ネイティブモードでの Reporting Services の &#40;の標準サブスクリプションの作成、変更、および削除」&#41;](subscriptions/create-and-manage-subscriptions-for-native-mode-report-servers.md)を参照してください。  
  
 レポートサーバーでのサブスクリプションの処理を無効にするには`ScheduleEventsAndReportDeliveryEnabled` 、ポリシー `False`ベースの管理の[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Reporting Services ファセット**のセキュリティ構成**で、プロパティをに設定します。 この場合、スケジュールされている処理は一切実行されません。 レポート サーバーのサブスクリプション処理だけを無効にすることはできません。  
  
 レポートサーバーで処理中のサブスクリプションを取り消す方法については、「[実行中のプロセスの管理](subscriptions/manage-a-running-process.md)」を参照してください。  
  
## <a name="disabling-delivery-extensions"></a>配信拡張機能の無効化  
 レポート サーバーにインストールされたすべての配信拡張機能は、特定のレポートのサブスクリプションを作成する権限を持つユーザーが使用できます。 使用できる配信拡張機能は次のとおりです。自動的に構成されます。  
  
-   Windows ファイル共有  
  
-   SharePoint ライブラリ (sharepoint 統合モードのレポートサーバーと統合された SharePoint サイトからのみ使用可能)  
  
 電子メール配信は使用前に構成する必要があります。 構成が済んでいない場合、使用できません。 詳細については、「[レポートサーバーの電子メール配信用の構成 &#40;SSRS Configuration Manager&#41;](../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)」を参照してください。  
  
 特定の拡張機能を無効にするには、RSReportServer.config ファイルから拡張機能のエントリを削除します。 詳細については、「 [Rsreportserver 構成ファイル](report-server/rsreportserver-config-configuration-file.md)」および「 [SSRS Configuration Manager&#41;&#40;電子メール配信用にレポートサーバーを構成](../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)する」を参照してください。  
  
 配信拡張機能の削除後は、この機能はレポート マネージャーまたは SharePoint サイトで使用できなくなります。 配信拡張機能を削除すると、サブスクリプションが無効になることがあります。 配信拡張機能を削除する前に、このようなサブスクリプションを削除するか、または別の配信拡張機能を使用するように構成する必要があります。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [個人用サブスクリプションを使用する](subscriptions/use-my-subscriptions-native-mode-report-server.md)  
 [個人用サブスクリプション] ページを使用して、所有するサブスクリプションを管理する方法を説明します。  
  
 [レポートとサブスクリプションの処理を一時停止する](subscriptions/disable-or-pause-report-and-subscription-processing.md)  
 ロールの割り当てを使用したり、レポートサーバーのリソースを無効にしたりするなど、レポートの処理を一時停止するさまざまな方法について説明します。  
  
 [レポートの配信を制御する](../../2014/reporting-services/control-report-distribution.md)  
 レポートの配信を制御するために使用する構成設定および配信オプションについて説明します。  
  
 [Reporting Services のサブスクリプションを監視する](subscriptions/monitor-reporting-services-subscriptions.md)  
 サブスクリプションが成功したか失敗したかを判断する方法、および既存のサブスクリプションに対するレポート変更の影響について説明します。  
  
## <a name="see-also"></a>参照  
 [ネイティブモードで Reporting Services &#40;標準のサブスクリプションを作成、変更、および削除&#41;](subscriptions/create-and-manage-subscriptions-for-native-mode-report-servers.md)  
  
  

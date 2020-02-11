---
title: '[サイトの設定] ページ (レポートマネージャー) |Microsoft Docs'
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4d67a01c-eae4-49ba-a6e8-8e983c0248f5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 07fc0207020887d7e3ceb8716ee76c78a55d2bac
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66101122"
---
# <a name="site-settings-page-report-manager"></a>[サイトの設定] ページ (レポート マネージャー)
  [サイトの設定] ページでは、アプリケーションのタイトルの変更、レポート履歴の制限やレポート処理タイムアウトに関するサーバー全体の既定値の設定、システム レベルのロールの割り当ての管理、および共有スケジュールの管理を実行できます。 このページを表示するには、コンテンツ マネージャーとシステム管理者の権限が必要です。  
  
> [!NOTE]  
>  レポート履歴、レポート実行、および共有スケジュール機能は、すべてのエディションの SQL Server で使用できるわけではありません。 の[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]各エディションでサポートされる機能の一覧については、「 [SQL Server 2014 の各エディションがサポートする機能](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」を参照してください。  
  
## <a name="navigation"></a>「ナビゲーション」  
 ユーザー インターフェイス (UI) のこの場所に移動するには、次の手順に従います。  
  
### <a name="to-open-the-site-settings-page"></a>[サイトの設定] ページを開くには  
  
1.  レポート マネージャーを開きます。  
  
2.  ページの上部にある **[サイトの設定]** をクリックします。 この操作により、サイトの [全般] プロパティ ページが開きます。  
  
     **注:** メニューに [**サイトの設定**] オプションが表示されない場合は、必要なアクセス許可がありません。詳細については、「[ローカル管理用のネイティブモードのレポートサーバーの構成 &#40;SSRS&#41;](report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md)」の「サイトの設定」セクションを参照してください。  
  
## <a name="options"></a>オプション  
 **名前**  
 この [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] レポート マネージャーのインスタンスに使用するタイトルを指定します。 既定では、タイトルは "[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]" です。  
  
 **[レポート履歴の既定の設定を選択します]**  
 レポート履歴で保持されるコピー数の既定値を選択します。 既定値には、レポート履歴の制限を規定する初期設定が用意されています。 これらの設定は、レポート レベルで異なります。 詳細については、「[[スナップショット オプション] プロパティ ページ &#40;レポート マネージャー&#41;](../../2014/reporting-services/snapshot-options-properties-page-report-manager.md)」を参照してください。  
  
 これから指定するレポート履歴の制限を超えてから、既存のレポート履歴を制限した場合、既存のレポート履歴が新しい制限値まで削減されます。 最初に、最も古いレポート スナップショットが削除されます。 レポート履歴が空であるか、制限を超えていない場合は、新しいレポート スナップショットが追加されます。 制限に達すると、新しいレポート スナップショットが追加されたときに最も古いスナップショットが削除されます。  
  
 **[レポート実行タイムアウト]**  
 特定の秒数が経過した後、レポート処理をタイムアウトさせるかどうかを指定します。  
  
 この値は、レポート サーバーでのレポート処理に適用されます。 レポートにデータを提供するデータベース サーバーで処理されるデータには影響しません。  
  
 レポート処理時間の時計は、レポートを選択したときに開始され、レポートを開くと終了します。 この値を設定する際、データ処理とレポート処理の両方を十分に完了できる時間を指定します。  
  
 **[カスタムのレポート ビルダーの起動 URL]**  
 レポート サーバーで既定のレポート ビルダー URL を使用しない場合に、カスタムの URL を指定します。 この設定はオプションです。 この値が指定されなかった場合は、レポート ビルダーを ClickOnce アプリケーションとして起動する既定の URL が使用されます。 既定の URL は、次のいずれかになります。  
  
 **ネイティブモードのレポートサーバー:** ネイティブモードのインストールでは、既定の URL の形式は http://\<*computername*>/reportserver/reportbuilder/ReportBuilder_3_0_0_0 になります。  
  
 SharePoint 統合モード: 既定の URL は、http://\<*SharePoint_site*>/_vti_bin/reportbuilder/ReportBuilder_3_0_0_0. "の形式になります。  
  
 **[適用]**  
 レポート サーバーに変更を保存する場合にクリックします。  
  
 **セキュリティ**  
 このリンクをクリックすると、[システム ロールの割り当て] ページが開きます。このページでは、ユーザー アカウントおよびグループ アカウントを定義済みのシステム ロールに割り当てることができます。  
  
 **スケジュール**  
 このリンクをクリックすると、[スケジュール] ページが開きます。このページでは、ユーザーがレポートおよびサブスクリプションに対して選択できる共有スケジュールを事前に定義できます。  
  
## <a name="see-also"></a>参照  
 [レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [ネイティブ モードのレポート サーバーに対する権限の許可](security/granting-permissions-on-a-native-mode-report-server.md)   
 [定義済みロール](security/role-definitions-predefined-roles.md)   
 [レポート マネージャー F1 ヘルプ](../../2014/reporting-services/report-manager-f1-help.md)  
  
  

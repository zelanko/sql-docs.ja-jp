---
title: Reporting Services のサイトの設定とサイト機能 (SharePoint モード) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e0040fec-e2b7-4099-ae01-3b9bb9128bbd
caps.latest.revision: 9
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: 1128105b7334fc5bf81fd72b9e178c15634a1cab
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36070299"
---
# <a name="reporting-services-site-settings-and-site-featuressharepoint-mode"></a>Reporting Services のサイト設定とサイト機能 (SharePoint モード)
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] の SharePoint モードには、SharePoint の [サイトの設定] ページから管理できるいくつかのサイト レベルのカスタム機能とサイト機能があります。 これらはサイト全体に対する設定で、すべての [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] サービス アプリケーションに影響を与えます。 このページを表示するには、コンテンツ マネージャーとシステム管理者の権限が必要です。  
  
|サイトの設定|説明|  
|------------------|-----------------|  
|[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] のサイト設定|このトピックで説明するサイト全体の設定。|  
|データ警告の管理|データ警告機能の管理。|  
|レポート サーバー ファイル同期|既定では非アクティブ化されているサイト レベルの機能。<br /><br /> ドキュメント ライブラリ内でファイルが直接追加または更新された場合に、SharePoint ドキュメント ライブラリのレポート サーバー ファイル (.rdl、.rsds、.smdl、.rsd、.rsc、および .rdlx) をレポート サーバーと同期します。<br /><br /> 詳細については、次を参照してください[SharePoint サーバーの全体管理でレポート サーバー ファイル同期機能をアクティブ化。](../../2014/reporting-services/activate-report-server-file-sync-feature-sharepoint-central-administration.md)|  
  
## <a name="to-open-the-reporting-services-site-settings-page"></a>[Reporting Services のサイト設定] ページを開くには  
  
1.  SharePoint サイトの **[サイトの操作]** メニューの **[サイトの設定]** をクリックします。  
  
2.  **[Reporting Services]** セクションで、 **[Reporting Services のサイト設定]** をクリックします。  
  
## <a name="options-for-reporting-services-site-settings"></a>[Reporting Services のサイト設定] のオプション  
  
|オプション|説明|  
|------------|-----------------|  
|**RSClientPrint ActiveX コントロールのダウンロードの有効化**|このコントロールによって表示されるカスタム印刷ダイアログ ボックスでは、印刷プレビュー、特定のページや範囲を指定するためのページ選択、ページ余白、ページの向きなど、一般的な印刷ダイアログ ボックスの機能がサポートされています。 コントロールの詳細については、「 [カスタム アプリケーション内での RSClientPrint コントロールの使用](report-server-web-service/net-framework/using-the-rsclientprint-control-in-custom-applications.md)」をご覧ください。|  
|**ローカル モードでのリモート エラーを有効にします**|ローカル モードでの実行時にリモート コンピューターの詳細なエラー メッセージの表示と非表示を切り替えます。 次のようなエラー メッセージが表示される場合は、リモート エラーを有効にすると役立つことがあります。<br /><br /> `For more information about this error navigate to the report server on the local server machine or enable remote errors`|  
|**レポートのアクセシビリティ メタデータを有効にします**|レポートの HTML 出力でアクセシビリティ メタデータを有効にします。|  
|**データの視覚エフェクトをレポートのサイズに正確に合わせます**|Tablix 内でデータの視覚エフェクトが正確に調整されるように調整動作を構成します。 これには、グラフ、ゲージ、およびマップが含まれます。 この動作を無効にすると、データの視覚エフェクトをおおよそのサイズに合わせることになり、空白が残る場合があります。 この設定は、レポート ビューアー Web パーツの表示にのみ適用されます。 サーバー側の表示に対するこの動作を管理する場合は、 **rsreportserver.config** ファイルを変更する必要があります。 詳細については、以下を参照してください。<br /><br /> [RSReportServer 構成ファイル](report-server/rsreportserver-config-configuration-file.md)です。<br /><br /> [RSReportServer.Config で拡張機能パラメーターの表示をカスタマイズ](customize-rendering-extension-parameters-in-rsreportserver-config.md)です。<br /><br /> [HTML デバイス情報設定](html-device-information-settings.md)です。<br /><br /> このオプションを有効にした場合は、正確なサイズを特定するために、おおよそのサイズに合わせる場合よりも処理に時間がかかることがあるため、パフォーマンスに影響する可能性があります。|  
  
## <a name="see-also"></a>参照  
 [Reporting Services SharePoint サービス アプリケーションの管理](../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md)  
  
  
---
title: '[サーバーのプロパティ] ([全般] ページ) | Microsoft Docs'
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.reportserver.serverproperties.general.f1
ms.assetid: 23537d52-4356-450f-a671-5921cef2431f
caps.latest.revision: 33
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: 05bcbd306dc29769db143fb4614c01d527144b82
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36164714"
---
# <a name="server-properties-general-page"></a>[サーバーのプロパティ] ([全般] ページ)
  このページを使用すると、レポート マネージャーで使用されるタイトルの表示と変更、個人用レポートの有効化と無効化、個人用レポートのセキュリティに関するロール定義の選択、およびクライアントの印刷コントロールの有効化または無効化ができます。  
  
 このページを開くを起動[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、レポート サーバー インスタンスへの接続をレポート サーバーの名前を右クリックしを選択し、**プロパティ**です。  
  
 サーバー モードによって、設定できるサーバー プロパティが決まります。 SharePoint 統合モード用に構成されたレポート サーバーを管理している場合は、個人用レポートを有効にしたり、レポート マネージャーのアプリケーション タイトルを設定することができません。  
  
## <a name="options"></a>および  
 **Name**  
 レポート マネージャーで表示されるアプリケーション名を入力します。 既定では、この値は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]です。 指定した名前は、レポート マネージャーでのみ表示されます。  
  
 **[バージョン]**  
 このプロパティは読み取り専用です。 使用している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のバージョンを示します。  
  
 **のエディション**  
 このプロパティは読み取り専用です。 現在のレポート サーバー インスタンスを指定します。 レポート マネージャーは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のすべてのエディションで使用できるわけではありません。 各エディションでサポートされている機能の一覧については[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を参照してください[SQL Server 2014 のエディションでサポートされる機能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)します。  
  
 **認証モード**  
 このプロパティは読み取り専用です。 レポート サーバー インスタンスで受け入れられる認証要求の種類を示します。 認証モードを変更するには、RSReportServer.config ファイルを編集する必要があります。 詳細については、「 [レポート サーバーでの認証](../security/authentication-with-the-report-server.md)」を参照してください。  
  
 **URL**  
 このプロパティは読み取り専用です。 レポート サーバー Web サービスへの URL を示します。 この値は [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成ツールで指定されます。 詳細については、「[URL の構成 &#40;SSRS 構成マネージャー&#41;](../install-windows/configure-a-url-ssrs-configuration-manager.md)」をご覧ください。  
  
 **[ユーザーごとに個人用レポート フォルダーを有効にする]**  
 ユーザーが個人用レポートを使用できるようにします。 このオプションはネイティブ モードのレポート サーバーでのみ使用できます。  
  
 **[個人用フォルダーごとに適用するロールを選択します]**  
 個人用レポートのセキュリティに使用するロール定義を指定します。 ロール定義は、各個人用レポート フォルダーでサポートされるタスクのセットを特定します。  
  
 **ActiveX クライアントの印刷コントロールのダウンロードを有効にします。**  
 セット、`EnableClientPrinting`レポート サーバー システム プロパティ。 クライアント側の印刷を有効にすると、ローカル管理者の権限を持つユーザーは、HTML レポートを印刷するための署名済み ActiveX コントロールをダウンロードすることができます。 詳細については、次を参照してください。[の有効化と Reporting Services のクライアント側の印刷を無効にする](../report-server/enable-and-disable-client-side-printing-for-reporting-services.md)です。  
  
## <a name="see-also"></a>参照  
 [レポート サーバーのプロパティを設定する (Management Studio)](set-report-server-properties-management-studio.md)   
 [Management Studio でレポート サーバーに接続する](connect-to-a-report-server-in-management-studio.md)   
 [個人用レポートの有効化と無効化](../report-server/enable-and-disable-my-reports.md)   
 [Management Studio のレポート サーバーの F1 ヘルプ](report-server-in-management-studio-f1-help.md)   
 [個人用レポートをセキュリティで保護する](../security/secure-my-reports.md)  
  
  
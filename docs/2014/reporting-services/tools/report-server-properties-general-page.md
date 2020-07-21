---
title: '[サーバーのプロパティ] ([全般] ページ) | Microsoft Docs'
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.serverproperties.general.f1
ms.assetid: 23537d52-4356-450f-a671-5921cef2431f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 93365925d412f672b9e8d3e5a9b5f67a850e508a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66100012"
---
# <a name="server-properties-general-page"></a>[サーバーのプロパティ] ([全般] ページ)
  このページを使用すると、レポート マネージャーで使用されるタイトルの表示と変更、個人用レポートの有効化と無効化、個人用レポートのセキュリティに関するロール定義の選択、およびクライアントの印刷コントロールの有効化または無効化ができます。  
  
 このページを開くには[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、を起動してレポートサーバーインスタンスに接続し、レポートサーバー名を右クリックして、[**プロパティ**] を選択します。  
  
 サーバー モードによって、設定できるサーバー プロパティが決まります。 SharePoint 統合モード用に構成されたレポート サーバーを管理している場合は、個人用レポートを有効にしたり、レポート マネージャーのアプリケーション タイトルを設定することができません。  
  
## <a name="options"></a>Options  
 **名前**  
 レポート マネージャーで表示されるアプリケーション名を入力します。 既定では、この値[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]はです。 指定した名前は、レポート マネージャーでのみ表示されます。  
  
 **Version**  
 このプロパティは読み取り専用です。 使用している[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]のバージョンを指定します。  
  
 **のエディション**  
 このプロパティは読み取り専用です。 現在のレポート サーバー インスタンスを指定します。 レポート マネージャーは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のすべてのエディションで使用できるわけではありません。 の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]各エディションでサポートされる機能の一覧については、「 [SQL Server 2014 の各エディションがサポートする機能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」を参照してください。  
  
 **認証モード**  
 このプロパティは読み取り専用です。 レポート サーバー インスタンスで受け入れられる認証要求の種類を示します。 認証モードを変更するには、RSReportServer.config ファイルを編集する必要があります。 詳細については、「 [レポート サーバーでの認証](../security/authentication-with-the-report-server.md)」を参照してください。  
  
 **URL**  
 このプロパティは読み取り専用です。 レポート サーバー Web サービスへの URL を示します。 この値は [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成ツールで指定されます。 詳細については、「[URL の構成 &#40;SSRS 構成マネージャー&#41;](../install-windows/configure-a-url-ssrs-configuration-manager.md)」をご覧ください。  
  
 **[ユーザーごとに個人用レポート フォルダーを有効にする]**  
 ユーザーが個人用レポートを使用できるようにします。 このオプションはネイティブ モードのレポート サーバーでのみ使用できます。  
  
 **[個人用フォルダーごとに適用するロールを選択します]**  
 個人用レポートのセキュリティに使用するロール定義を指定します。 ロール定義は、各個人用レポート フォルダーでサポートされるタスクのセットを特定します。  
  
 **[ActiveX クライアントの印刷コントロールのダウンロードを有効にする]**  
 `EnableClientPrinting` レポート サーバー システム プロパティを設定します。 クライアント側の印刷を有効にすると、ローカル管理者の権限を持つユーザーは、HTML レポートを印刷するための署名済み ActiveX コントロールをダウンロードすることができます。 詳細については、「 [Reporting Services のクライアント側印刷機能の有効化と無効化](../report-server/enable-and-disable-client-side-printing-for-reporting-services.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [レポートサーバーのプロパティ &#40;Management Studio の設定&#41;](set-report-server-properties-management-studio.md)   
 [Management Studio でレポートサーバーに接続する](connect-to-a-report-server-in-management-studio.md)   
 [個人用レポートを有効または無効にする](../report-server/enable-and-disable-my-reports.md)   
 [Management Studio F1 ヘルプのレポートサーバー](report-server-in-management-studio-f1-help.md)   
 [個人用レポートをセキュリティで保護する](../security/secure-my-reports.md)  
  
  

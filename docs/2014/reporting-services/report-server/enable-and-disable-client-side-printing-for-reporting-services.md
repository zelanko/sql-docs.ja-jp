---
title: Reporting Services のクライアント側印刷機能の有効化と無効化 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 0e709c96-7517-4547-8ef6-5632f8118524
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ea5016aa51a25bd296d2e77516b30b84a7a28cec
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66103928"
---
# <a name="enable-and-disable-client-side-printing-for-reporting-services"></a>Reporting Services のクライアント側印刷機能の有効化と無効化
  ActiveX [!INCLUDE[msCoName](../../includes/msconame-md.md)]コントロール ( **rsclientprint**) は、ブラウザーに表示されるレポートのクライアント側印刷機能を提供します。 このコントロールによって表示されるカスタム印刷ダイアログ ボックスでは、一般的な印刷ダイアログ ボックスの機能がサポートされています。 この機能には、印刷プレビュー、特定のページや範囲を指定するためのページ選択、ページ余白、ページの向きなどが含まれます。 クライアント側印刷機能は既定で有効になっていますが、無効にして使用できないようにすることもできます。  
  
> [!NOTE]  
>  ActiveX コントロールをダウンロードするには、管理者権限が必要です。  
  
## <a name="downloading-the-activex-control"></a>ActiveX コントロールのダウンロード  
 印刷機能を使用する各ユーザーは、クライアント側印刷機能を提供する ActiveX コントロールをダウンロードしてインストールする必要があります。 ユーザーがレポートツールバーの [**プリンター** ] アイコンを初めてクリックすると、Microsoft ActiveX コントロールがコンピューターにダウンロードされます。 コントロールがダウンロードされると、ユーザーが**プリンター**アイコンをクリックするたびに [**印刷**] ダイアログボックスが表示されます。  
  
 ブラウザーの設定によって、コントロールをインストールするかどうかを確認するメッセージが表示される場合と、コントロールをインストールできない場合と、ユーザーへの通知を行わずにコントロールがバックグラウンドでインストールされる場合があります。  
  
 Internet [!INCLUDE[msCoName](../../includes/msconame-md.md)] Explorer の場合、activex コントロールのダウンロードとインストールに影響を与える設定は、Web コンテンツゾーンの [セキュリティの**設定**] ページの [ **activex コントロールとプラグイン**] ノードで指定します。 印刷コントロールをダウンロードして実行できるかどうかは、Web ゾーンの以下のセキュリティ設定によって決まります。  
  
-   署名済み ActiveX コントロールのダウンロード。  
  
-   スクリプトを実行しても安全とマークされている ActiveX コントロールのスクリプトの実行。  
  
-   ActiveX コントロールとプラグインの実行。  
  
 **Rsclientprint**を使用してクライアント側印刷を実行するユーザーは、次の機能を有効にする必要があります。  
  
-   署名された**activex コントロールをダウンロード**し、スクリプト用に安全とマークされた**スクリプト activex コントロール**をインストールのためにダウンロードします。  
  
-   **ActiveX コントロールとプラグインを実行して、実行**中の印刷操作を行います。  
  
 **Rsclientprint** ActiveX コントロールは署名されています。これは、から[!INCLUDE[msCoName](../../includes/msconame-md.md)]の有効なデジタル証明書が含まれていることを意味します。  
  
## <a name="enabling-and-disabling-client-side-printing"></a>クライアント側印刷機能の有効化と無効化  
 レポートサーバーの管理者は、レポートサーバーのシステムプロパティ**EnableClientPrinting**をに設定して、印刷`false`機能を無効にすることができます。 これにより、サーバーが管理しているすべてのレポートでクライアント側印刷機能が無効になります。 既定では、 **EnableClientPrinting**はに`true`設定されています。 クライアント側印刷機能は、次の方法で無効にすることができます。  
  
-   
  **ネイティブ モードのレポート サーバー**の場合:  
  
    1.  管理者特権を使用して [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を開始します。  
  
    2.  
  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]でレポート サーバー インスタンスに接続します。  
  
    3.  レポート サーバー ノードを右クリックして、 **[プロパティ]** をクリックします。 
  **[プロパティ]** オプションが無効になっている場合は、管理者特権を使用して [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を開始したことを確認してください。  
  
    4.  [ **ActiveX クライアントの印刷コントロールのダウンロードを有効にする**] を選択します。  
  
    5.  **[OK]** をクリックします。  
  
-   
  **SharePoint モードのレポート サーバー**の場合:  
  
    1.  SharePoint サーバーの全体管理で、 **[アプリケーション構成の管理]** をクリックします。  
  
    2.  
  **[サービス アプリケーションの管理]** をクリックします。  
  
    3.  サービスアプリケーションの名前をクリックし、SharePoint リボンの [管理] をクリックします。 **** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
    4.  **[システム設定]** をクリックします。  
  
    5.  
  **[クライアントの印刷を有効にする]** を選択します。 
  **[クライアントの印刷を有効にする]** オプションは、ページの下部付近にあります。  
  
    6.  **[OK]** をクリックします。  
  
-   レポートサーバーのシステムプロパティ**EnableClientPrinting**を設定するスクリプトまたはコードを作成します。`false.`  
  
 次のサンプル スクリプトは、クライアント側印刷機能を無効にする方法の一例を示しています。 この [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] コードをコンパイルして実行すると、 **EnableClientPrinting** プロパティが **False**に設定されます。 コードの実行後、IIS を再起動してください。  
  
### <a name="sample-script"></a>サンプル スクリプト  
  
```  
Imports System  
Imports System.Web.Services.Protocols  
Class Sample  
   Public Shared Sub Main()  
Dim rs As New ReportingService()  
      rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
        Dim props(0) As [Property]  
        Dim setProp As New [Property]  
        setProp.Name = "EnableClientPrinting"  
        setProp.Value = "False"   
        props(0) = setProp  
        Try  
            rs.SetSystemProperties(props)  
        Catch ex As System.Web.Services.Protocols.SoapException  
            Console.Write(ex.Detail.InnerXml)  
        Catch e as Exception  
            Console.Write(e.Message)  
        End Try  
    End Sub 'Main  
End Class 'Sample  
```  
  
  

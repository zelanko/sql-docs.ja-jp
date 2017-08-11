---
title: "Web アプリケーションで URL アクセスの使用 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- links [Reporting Services], URL access
- URL access [Reporting Services], Web applications
- POST requests
- direct addressing [Reporting Services]
- Web applications [Reporting Services]
- hyperlinks [Reporting Services]
ms.assetid: 39e7918c-ad2d-4ca6-b099-2dd4dbdb83dc
caps.latest.revision: 33
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: b8d7aff6c9afdfa6e6fb322d028b9bccf5cbaaf5
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="integrating-reporting-services-using-url-access---web-application"></a>使用する URL アクセスの Web アプリケーションをサービス レポートの統合
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の URL アクセスは、ネットワークを介して各レポートにアクセスできるように特別に設計されています。 この種類のアクセスは、レポートの表示およびナビゲーションをカスタム Web アプリケーションに統合するのに最適です。 Web アプリケーションで URL アクセスを使用するには、次の方法があります。  
  
-   Web サイトまたはポータルから特定のレポート サーバーへの URL を指定する。  
  
-   フォームの POST メソッドを使用する。さらに、フォーム フィールドを使用してクエリ文字列パラメーターをレポート サーバーの URL に渡す。  
  
## <a name="url-access-through-direct-addressing"></a>直接アドレス指定による URL アクセス  
 レポート サーバーまたは URL を使用してレポート サーバー データベース アイテムにアクセスするには、単にから Web ブラウザーまたはアプリケーション内の URL アドレスを提供します。 また、アクセス中のレポートまたはリソースの外観に影響を与える可能性がある URL にパラメーターを指定することもできます。 URL を Web ブラウザーのアドレス バーを使用してレポート サーバーを対象にできますか、URL のソースとして使用できます、 **IFrame**より大規模な Web アプリケーションまたはポータルの一部であります。 レポートの特定のフレームを対象としたり、その過程で新しいブラウザー ウィンドウを開いたりするだけでなく、ポータルの Web ページでレポートのハイパーリンクを含めることもできます。  
  
 次の例では、ハイパーリンクは "main" という名前のフレームを対象とし、ハイパーリンクを含むハイパーリンクとは異なります。 ハイパーリンクは、Web ポータルの一部となる場合もあります。  
  
```  
<a href="http://server/reportserver?/SampleReports/Territory Sales   
Drilldown&rs:Command=Render&rc:LinkTarget=main" target="main" >  
   Click here for the Territory Sales Drilldown sample report  
</a>  
```  
  
 前の例では、デバイス情報設定で**LinkTarget** URL のクエリ文字列に「メイン」の値は渡されます。 これにより、レポートのドリルスルー ハイパーリンクも確実に "main" という名前のフレームを対象とします。  
  
 デバイス情報設定についての詳細については、次を参照してください。[表示拡張機能にデバイス情報設定を渡す](../../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)です。  
  
 多くのサーバーおよびブラウザーでは、URL に使用可能な文字数が制限されているので注意してください。 場合によっては、256 文字の制限が適用されます。 この制限を回避するには、フォーム送信による POST 要求を使用できます。  
  
> [!NOTE]  
>  Internet Explorer の URL の最大文字数は 2,083 文字です。 この制限は、URL を要求する POST および GET に適用されます。 ただし、フォームの一部として名前と値の組を送信する場合、POST は URL のサイズによる制限を受けません。これは、名前と値の組が URL でなくヘッダーで転送されるためです。  
  
## <a name="url-access-through-a-form-post-method"></a>フォームの POST メソッドを使用した URL アクセス  
 URL アクセスを使用してレポート サーバーからデータを要求する場合、HTTP 要求では GET メソッドを使用します。 これは、METHOD="GET" の場合のフォーム送信と同じです。 METHOD="GET" を使用した URL 要求またはフォーム送信は、サーバーまたは Web ブラウザーが処理できる最大文字数による制限を受けます。  
  
 POST 要求 (METHOD="POST" と入力フィールド) の場合、名前と値の組が URL ではなくヘッダーで転送されます。 したがって、クエリ文字列の名前と値の組は URL の一部ではないため、より長い、かつ複雑なパラメーター リストを指定できます。  
  
 ユーザーは直接アクセスを使用して、レポート サーバーの URL を表示したり、クエリ文字列を変更したり、後で使用するために特定の URL 要求とレポート サーバー パラメーターを書き留めたりすることができます。  
  
 次の HTML サンプルは、特定の URL を使用してレポート サーバーを対象とし、クエリ文字列パラメーターをフォームの入力フィールドの一部として渡すことができるフォームの使用を示します。  
  
```  
<FORM id="frmRender" action="http://server/reportserver?/SampleReports/  
   Territory Sales Drilldown" method="post" target="_self">  
   <INPUT type="hidden" name="rs:Command" value="Render">   
   <INPUT type="hidden" name="rc:LinkTarget" value="main">  
   <INPUT type="hidden" name="rs:Format" value="HTML4.0">  
   <INPUT type="submit" value="Button">  
</FORM>  
```  
  
 前の例では、フォームのボタンをクリックすると、レポート サーバーによって、現在のフレームで対象となっている HTML で表示されたレポートが返されます。 前の例に対して、この例での URL アクセスの文字列は、次のようになります。  
  
```  
http://server/reportserver?/SampleReports/Territory Sales   
Drilldown&rs:Command=Render&rc:LinkTarget=main&rs:Format=HTML4.0  
```  
  
## <a name="see-also"></a>参照  
 [アプリケーションへの Reporting Services の統合](../../reporting-services/application-integration/integrating-reporting-services-into-applications.md)   
 [URL アクセスを使用して Reporting Services の統合](../../reporting-services/application-integration/integrating-reporting-services-using-url-access.md)   
 [Windows アプリケーションで URL アクセスの使用](../../reporting-services/application-integration/integrating-reporting-services-using-url-access-windows-application.md)   
 [URL アクセスと #40 です。SSRS &#41;](../../reporting-services/url-access-ssrs.md)  
  
  

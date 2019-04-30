---
title: URL アクセスを使用してレポート サーバー アイテムへのアクセス |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- referencing URL items for report server access
- URL access [Reporting Services], report servers
ms.assetid: a58b4ca6-129d-45e9-95c7-e9169fe5bba4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3a345cd609c4cfd79f9e93a2b63e71bbddde36ee
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63233565"
---
# <a name="access-report-server-items-using-url-access"></a>URL アクセスを使用してレポート サーバー項目にアクセスします。
  このトピックでは、方法、レポート内のさまざまな種類のカタログ項目にアクセスするサーバー データベースまたは SharePoint サイトを使用してについて説明します。 *Rs:command*=*値*します。  
  
 このパラメーターの文字列を追加する必要はありません。 を省略した場合、レポート サーバーは、項目の種類を評価し、適切なパラメーター値を自動的に選択します。 ただしを使用して、 *Rs:command*=*値*URL 内の文字列、レポート サーバーのパフォーマンスが向上します。  
  
 注、`_vti_bin`次の例ではプロキシ構文。 プロキシ構文の使用に関する詳細については、次を参照してください。 [URL アクセス パラメーター リファレンス](url-access-parameter-reference.md)します。  
  
## <a name="access-a-report"></a>レポートへのアクセスします。  
 ブラウザーでレポートを表示する、 *Rs:command*=*レンダリング*パラメーター。 例えば:  
  
 `Native` `http://myrshost/reportserver?/Sales/YearlySalesByCategory&rs:Command=Render`  
  
 `SharePoint` `http://myspsite/subsite/_vti_bin/reportserver? http://myspsite/subsite/Sales/YearlySalesByCategory&rs:Command=Render`  
  
> [!TIP]  
>  SharePoint および `_vti_bin` HTTP プロキシ経由で要求をルーティングする [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] プロキシ構文を URL に含めることは重要です。 プロキシによって、HTTP 要求にいくつかのコンテキストが追加されます。これは、SharePoint モード レポート サーバーに対してレポートを適切に実行するために必要なコンテキストです。  
  
## <a name="access-a-resource"></a>リソースへのアクセスします。  
 リソースにアクセスするには、使用、 *Rs:command*=*GetResourceContents*パラメーター。リソースが、画像など、ブラウザーと互換性のある場合は、ブラウザーで開かれます。 それを開くか、ファイルまたはリソースをディスクに保存するように求められます。  
  
 `Native` `http://myrshost/reportserver?/Sales/StorePicture&rs:Command=GetResourceContents`  
  
 `SharePoint` `http://myspsite/subsite/_vti_bin/reportserver? http://myspsite/subsite/Sales/StorePicture.jpg&rs:Command=GetResourceContents`  
  
## <a name="access-a-data-source"></a>データ ソースへのアクセスします。  
 データ ソースにアクセスするには、使用、 *Rs:command*=*GetDataSourceContents*パラメーター。 お使いのブラウザーでは、XML をサポートする場合で認証済みのユーザーの場合データ ソースの定義が表示されます。`Read Contents`データ ソースに対する権限。 例:  
  
 `Native` `http://myrshost/reportserver?/Sales/AdventureWorks2012&rs:Command=GetDataSourceContents`  
  
 `SharePoint` `http://myspsite/subsite/_vti_bin/reportserver? http://myspsite/subsite/Sales/AdventureWorks2012&rs:Command=GetDataSourceContents`  
  
 XML 構造は、次の例のようになります。  
  
```  
<DataSourceDefinition>  
   <Extension>SQL</Extension>  
   <ConnectString>Provider=SQLOLEDB.1;Integrated Security=SSPI;Persist Security Info=False;Initial Catalog=AdventureWorks2012;Data Source=MYSERVER1;</ConnectString>  
   <CredentialRetrieval>Integrated</CredentialRetrieval>  
   <WindowsCredentials>False</WindowsCredentials>  
   <ImpersonateUser>False</ImpersonateUser>  
   <Prompt />  
   <Enabled>True</Enabled>  
</DataSourceDefinition>  
```  
  
 接続文字列が返されますに基づいて、 **SecureConnectionLevel**レポート サーバーの設定。 詳細については、 **SecureConnectionLevel**設定、表示[セキュリティで保護された Web サービス メソッドを使用して](report-server-web-service/net-framework/using-secure-web-service-methods.md)します。  
  
## <a name="access-the-contents-of-a-folder"></a>フォルダーの内容にアクセスします。  
 フォルダーの内容にアクセスするには、使用、 *Rs:command*=*GetChildren*パラメーター。 汎用フォルダー ナビゲーション ページは、サブフォルダー、レポート、データ ソース、および要求されたフォルダー内のリソースへのリンクを格納しているが返されます。 例:  
  
 `Native` `http://myrshost/reportserver?/Sales&rs:Command=GetChildren`  
  
 `SharePoint` `http://myspsite/subsite/_vti_bin/reportserver? http://myspsite/subsite/Sales&rs:Command=GetChildren`  
  
 ユーザー インターフェイスはディレクトリで使用されるモードの参照に似ています[!INCLUDE[msCoName](../includes/msconame-md.md)]インターネット インフォメーション サーバー (IIS)。 バージョン番号は、レポート サーバーのビルド番号を含むは、以下のフォルダーの一覧も表示されます。  
  
## <a name="see-also"></a>関連項目  
 [URL アクセス&#40;SSRS&#41;](url-access-ssrs.md)   
 [URL アクセス パラメーター リファレンス](url-access-parameter-reference.md)  
  
  

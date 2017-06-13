---
title: "カスタム セキュリティ拡張機能をインストールする方法 |Microsoft ドキュメント"
ms.custom: 
ms.date: 04/18/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: bfa0a35b-ccfb-4279-bae6-106c227c5f16
caps.latest.revision: 3
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: e7058e9c0edce2b457dc63bf9e2d5cf61b6ee64f
ms.contentlocale: ja-jp
ms.lasthandoff: 06/13/2017

---
# <a name="how-to-install-custom-security-extensions"></a>カスタム セキュリティ拡張機能をインストールする方法
Reporting Services 2016 には、新しい Odata Api をホストしもモバイル レポートと KPI などの新しいレポート ワークロードをホストするために新しい web ポータルが導入されました。 この新しいポータルは新しいテクノロジに依存しています、別のプロセスで実行して、使い慣れた ReportingServicesService から分離します。 このプロセスは、ホストされる ASP.NET アプリケーションではないおよび、ような既存のカスタム セキュリティ拡張機能から前提条件を改行します。 さらに、カスタム セキュリティ拡張機能の現在のインターフェイスを許可しないすべての外部に渡されるコンテキスト、既知のグローバル ASP.NET オブジェクトを検査する唯一の選択肢を持つ実装者のままこの必須インターフェイスには、いくつか変更します。

## <a name="what-changed"></a>何が変更されたか。

新しいインターフェイスが導入されたを実装できる認証に関連する意思決定を行う拡張機能で使用される一般的なプロパティを提供する、IRSRequestContext を提供します。
    
以前のバージョンでは、レポート マネージャーは、フロント エンドがおよび、独自のカスタム ログイン ページを使用して構成できます。 Reporting Services 2016 で reportserver によってホストされている 1 つだけのページがサポートされ、両方のアプリケーションを認証する必要があります。

## <a name="implementation"></a>実装
以前のバージョンでは、拡張機能が ASP.NET オブジェクトすぐに使用できることが一般的な前提としてに頼る。 ASP.NET では、新しいポータルが実行されないため、拡張機能可能性がありますオブジェクトが NULL で問題に達しています。
    
最も一般的な例は、ヘッダーとクッキーなどの要求情報を読み取る HttpContext.Current にアクセスします。 拡張機能を同じ決定を行うを許可するために要求情報を提供し、ポータルからの認証時に呼び出される拡張機能で新しいメソッドが導入されました。 
    
拡張機能が実装するために、<xref:Microsoft.ReportingServices.Interfaces.IAuthenticationExtension2>これを活用するためにインターフェイスです。 拡張機能が両方のバージョンを実装する必要があります<xref:Microsoft.ReportingServices.Interfaces.IAuthenticationExtension.GetUserInfo%2A>メソッドは、reportserver コンテキストと web ホスト プロセスで使用されるその他によって呼び出されます。 以下のサンプルは、reportserver によって解決 id が使用されているものをここでは、ポータルの単純な実装のいずれかを示しています。

``` 
      public void GetUserInfo(IRSRequestContext requestContext, out IIdentity userIdentity, out IntPtr userId)
      {
           userIdentity = null;
           if (requestContext.User != null)
           {
               userIdentity = requestContext.User;
           }

          // initialize a pointer to the current user id to zero
           userId = IntPtr.Zero;
      }
```

## <a name="deployment-and-configuration"></a>展開と構成
カスタム セキュリティ拡張機能に必要な基本的な構成では、以前のリリースと同じです。 Web.config および rsreportserver.config の変更が必要な: 詳細については、次を参照してください。[を構成するカスタムまたはフォーム認証は、レポート サーバー上](../../../reporting-services/security/configure-custom-or-forms-authentication-on-the-report-server.md)です。
    
レポート マネージャーの別の web.config はなくなりますが、ポータルは、reportserver エンドポイントと同じ設定を継承します。

## <a name="machine-keys"></a>コンピューター キー

認証 cookie の復号化を必要となるフォーム認証の場合は、両方のプロセスを同じマシン キーと復号化アルゴリズムを使用して構成する必要があります。 これは、以前は、スケール アウト環境で動作するセットアップ Reporting Services があったが、今すぐ要件もの単一のコンピューターに展開するユーザーになじみのステップをでした。

例:
    
**\ReportServer\web.config**

追加`<system.web>`です。
    
```
    <machineKey validationKey="[YOUR KEY]" decryptionKey=="[YOUR KEY]" validation="AES" decryption="AES" />
```

**\RSWebApp\Microsoft.ReportingServices.Portal.WebHost.exe.config**

追加`<configuration>`です。

```
    <system.web>
        <machineKey validationKey=="[YOUR KEY]" decryptionKey=="[YOUR KEY]" validation="AES" decryption="AES" />
    </system.web>
```

展開の特定のキーの検証を使用する必要があります、インターネット インフォメーション サービス マネージャー (IIS) のようなキーを生成するツールがいくつかあります。 その他のツールは、インターネットで確認できます。

## <a name="configure-passthrough-cookies"></a>パススルー cookie を構成します。

新しいポータルと、reportserver は、いくつかの操作 (レポート マネージャーの以前のバージョンに似ています) の内部の soap Api を使用して通信します。 ポータルからサーバーに渡される追加のクッキーが必要な場合は、PassThroughCookies プロパティを引き続き使用できます。 詳細については、次を参照してください。[カスタム認証クッキーを Web ポータルを構成する](../../../reporting-services/security/configure-the-web-portal-to-pass-custom-authentication-cookies.md)です。

```
<UI>
   <CustomAuthenticationUI>
      <PassThroughCookies>
         <PassThroughCookie>sqlAuthCookie</PassThroughCookie>
      </PassThroughCookies>
   </CustomAuthenticationUI>
</UI>
```

## <a name="see-also"></a>参照

[レポート サーバーでカスタム認証またはフォーム認証を構成します。](../../../reporting-services/security/configure-custom-or-forms-authentication-on-the-report-server.md)  
[カスタム認証クッキーを渡すためのレポート マネージャーを構成します。](https://msdn.microsoft.com/library/ms345241(v=sql.120).aspx)

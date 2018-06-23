---
title: Reporting Services 配信拡張機能の設定 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- XML Web service [Reporting Services], delivery extension settings
- Report Server Web service, delivery extension settings
- delivery [Reporting Services]
- network share delivery [Reporting Services]
- file share delivery [Reporting Services]
- e-mail [Reporting Services]
- mailing reports [Reporting Services]
- sharing reports
- extensions [Reporting Services], delivery
- mail [Reporting Services]
- Web service [Reporting Services], delivery extension settings
ms.assetid: 68c31a85-261c-4ec4-b8df-1f9842b46f8a
caps.latest.revision: 36
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 94c05bce76e29f3147af8143fa22f03bdd7844a8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36164022"
---
# <a name="reporting-services-delivery-extension-settings"></a>Reporting Services 配信拡張機能の設定
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] には、電子メールの配信拡張機能とファイル共有の配信拡張機能があります。 電子メールの配信拡張機能では、電子メールを使用して、個々のユーザーやグループにレポートを送信できます。 ファイル共有の配信機能では、生成したレポートをネットワーク上の共有者に自動的に送信できます。 サポートされているいずれかの配信拡張機能を、標準的なサブスクリプションまたはデータ ドリブン サブスクリプションと一緒に使用できます。 <xref:ReportService2010.ReportingService2010.CreateSubscription%2A> メソッド、<xref:ReportService2010.ReportingService2010.CreateDataDrivenSubscription%2A> メソッド、<xref:ReportService2010.ReportingService2010.SetSubscriptionProperties%2A> メソッド、および <xref:ReportService2010.ReportingService2010.SetDataDrivenSubscriptionProperties%2A> メソッドを呼び出すときは常に、配信拡張機能の種類に固有の配信設定を渡す必要があります。 配信設定の一覧をプログラムによって取得するには、<xref:ReportService2010.ReportingService2010.GetExtensionSettings%2A> メソッドを使用します。  
  
> [!NOTE]  
>  配信拡張機能の設定では、大文字と小文字が区別されます。  
  
## <a name="e-mail-delivery-settings"></a>電子メール配信の設定  
 次の表は、レポート サーバー電子メールを使用するサブスクリプションの電子メール配信設定を示しています。  
  
|設定|値|  
|-------------|-----------|  
|**宛先**|電子メール メッセージの `To` 行に表示される電子メール アドレス。 複数の電子メール アドレスを指定するときは、それぞれをセミコロンで区切ります。 必須。|  
|**Cc**|電子メール メッセージの `Cc` 行に表示される電子メール アドレス。 複数の電子メール アドレスを指定するときは、それぞれをセミコロンで区切ります。 任意。|  
|**[Bcc]**|電子メール メッセージの `Bcc` 行に表示される電子メール アドレス。 複数の電子メール アドレスを指定するときは、それぞれをセミコロンで区切ります。 任意。|  
|**ReplyTo**|電子メール メッセージの `Reply-To` ヘッダーに表示される電子メール アドレス。 値は、電子メール アドレス 1 つである必要があります。 任意。|  
|`IncludeReport`|電子メール配信にレポートを含めるかどうかを示す値。 この値が `true` の場合は、レポートを電子メール メッセージの本文として配信することを示します。|  
|**RenderFormat**|表示レポートの生成に使用する表示拡張機能の名前。 名前は、レポート サーバーにインストールされている表示可能な表示拡張機能のいずれかに対応している必要があります。 `IncludeReport` の設定値が `true` の場合は、この値を必ず指定する必要があります。|  
|**[Priority]**|電子メール メッセージを送信する優先順位。 有効な値は`LOW`、 `NORMAL`、および`HIGH`です。 既定値は `NORMAL` です。|  
|**[Subject]**|電子メール メッセージの件名のテキスト。|  
|**解説**|電子メール メッセージの本文のテキスト。|  
|**IncludeLink**|電子メールの本文にレポートへのリンクを含めるかどうかを示す値。|  
  
## <a name="file-share-delivery-settings"></a>ファイル共有配信の設定  
 次の表は、サブスクリプションのファイル共有配信設定を示しています。  
  
|設定|値|  
|-------------|-----------|  
|**FILENAME**|ディスクに保存するファイルの名前。|  
|**FILEEXTN**|表示レポートのファイル拡張機能を含めるかどうかを示します。 いずれかの値が`true`または`false`です。|  
|**PATH**|レポートを保存するフォルダー パスまたは UNC ファイル共有パス。|  
|**RENDER_FORMAT**|ディスクに保存するレポートの形式。|  
|**USERNAME**|ネットワーク リソースまたはディスクへのアクセスに必要なユーザー名。|  
|**PASSWORD**|ネットワーク リソースまたはディスクへのアクセスに必要なパスワード。|  
|**WRITEMODE**|ディスクへのアクセスに使用する書き込みモード。 有効な値は`None`、 `Overwrite`、および`AutoIncrement`です。|  
  
## <a name="see-also"></a>参照  
 [テクニカル リファレンス (SSRS)](../../technical-reference-ssrs.md)   
 [Web サービスと .NET Framework を使用してのアプリケーションの構築](building-applications-using-the-web-service-and-the-net-framework.md)  
  
  
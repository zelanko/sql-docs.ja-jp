---
title: "Reporting Services の配信拡張機能の設定 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
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
author: sabotta
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 668c3d31af5f287d7d254c2dc666e20a5f6328fa
ms.contentlocale: ja-jp
ms.lasthandoff: 06/13/2017

---
# <a name="reporting-services-delivery-extension-settings"></a>Reporting Services 配信拡張機能の設定
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]電子メール配信拡張機能とファイル共有配信拡張機能が含まれます。 電子メールの配信拡張機能では、電子メールを使用して、個々のユーザーやグループにレポートを送信できます。 ファイル共有の配信機能では、生成したレポートをネットワーク上の共有者に自動的に送信できます。 サポートされているいずれかの配信拡張機能を、標準的なサブスクリプションまたはデータ ドリブン サブスクリプションと一緒に使用できます。 <xref:ReportService2010.ReportingService2010.CreateSubscription%2A> メソッド、<xref:ReportService2010.ReportingService2010.CreateDataDrivenSubscription%2A> メソッド、<xref:ReportService2010.ReportingService2010.SetSubscriptionProperties%2A> メソッド、および <xref:ReportService2010.ReportingService2010.SetDataDrivenSubscriptionProperties%2A> メソッドを呼び出すときは常に、配信拡張機能の種類に固有の配信設定を渡す必要があります。 配信設定の一覧をプログラムによって取得するには、<xref:ReportService2010.ReportingService2010.GetExtensionSettings%2A> メソッドを使用します。  
  
> [!NOTE]  
>  配信拡張機能の設定では、大文字と小文字が区別されます。  
  
## <a name="e-mail-delivery-settings"></a>電子メール配信の設定  
 次の表は、レポート サーバー電子メールを使用するサブスクリプションの電子メール配信設定を示しています。  
  
|設定|値|  
|-------------|-----------|  
|**宛先**|表示される電子メール アドレス、**に**電子メール メッセージの行。 複数の電子メール アドレスを指定するときは、それぞれをセミコロンで区切ります。 必須。|  
|**[CC]**|表示される電子メール アドレス、 **Cc**電子メール メッセージの行。 複数の電子メール アドレスを指定するときは、それぞれをセミコロンで区切ります。 省略可。|  
|**[BCC]**|表示される電子メール アドレス、 **Bcc**電子メール メッセージの行。 複数の電子メール アドレスを指定するときは、それぞれをセミコロンで区切ります。 省略可。|  
|**ReplyTo**|表示される電子メール アドレス、**返信先**電子メール メッセージのヘッダー。 値は、電子メール アドレス 1 つである必要があります。 省略可。|  
|**IncludeReport**|電子メール配信にレポートを含めるかどうかを示す値。 値**true**電子メール メッセージの本文にレポートを配信することを示します。|  
|**RenderFormat**|表示レポートの生成に使用する表示拡張機能の名前。 名前は、レポート サーバーにインストールされている表示可能な表示拡張機能のいずれかに対応している必要があります。 この値が必要な**IncludeReport**設定の値に設定されて**true**です。|  
|**[Priority]**|電子メール メッセージを送信する優先順位。 有効な値は**低**、**標準**、および**高**です。 既定値は**標準**です。|  
|**Subject**|電子メール メッセージの件名のテキスト。|  
|**解説**|電子メール メッセージの本文のテキスト。|  
|**IncludeLink**|電子メールの本文にレポートへのリンクを含めるかどうかを示す値。|  
  
## <a name="file-share-delivery-settings"></a>ファイル共有配信の設定  
 次の表は、サブスクリプションのファイル共有配信設定を示しています。  
  
|設定|値|  
|-------------|-----------|  
|**ファイル名**|ディスクに保存するファイルの名前。|  
|**FILEEXTN**|表示レポートのファイル拡張機能を含めるかどうかを示します。 いずれかの値が**true**または**false**です。|  
|**パス**|レポートを保存するフォルダー パスまたは UNC ファイル共有パス。|  
|**RENDER_FORMAT**|ディスクに保存するレポートの形式。|  
|**ユーザー名**|ネットワーク リソースまたはディスクへのアクセスに必要なユーザー名。|  
|**パスワード**|ネットワーク リソースまたはディスクへのアクセスに必要なパスワード。|  
|**WRITEMODE**|ディスクへのアクセスに使用する書き込みモード。 有効な値は**None**、**上書き**、および**AutoIncrement**です。|  
  
## <a name="see-also"></a>参照  
 [テクニカル リファレンス & #40 です。SSRS &#41;](../../../reporting-services/technical-reference-ssrs.md)   
 [Web サービスと、.NET Framework を使用してアプリケーションの構築](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
  
  

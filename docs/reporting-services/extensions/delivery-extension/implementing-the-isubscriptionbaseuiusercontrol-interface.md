---
title: ISubscriptionBaseUIUserControl インターフェイスの実装 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.component: extensions
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- user controls [Reporting Services]
- ISubscriptionBaseUIUserControl interface
- delivery extensions [Reporting Services], user controls
ms.assetid: a1e9122c-aa0b-45de-b536-4f1202875ab1
caps.latest.revision: 35
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 538c4b578cd8ed323bd3e335bc395f9720664c75
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="implementing-the-isubscriptionbaseuiusercontrol-interface"></a>ISubscriptionBaseUIUserControl インターフェイスの実装
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] の配信拡張機能には、レポート マネージャーで拡張機能固有の情報を収集するためのサブスクリプション ユーザー インターフェイス (UI) の実装を含めることができます。 ユーザーが新しいサブスクリプションを作成するか既存のサブスクリプションを変更するとき、UI が呼び出されます。 新しいサブスクリプションの作成時には、UI に適切な既定値が表示され、ユーザーは配信プロバイダーと対話できます。 サブスクリプションの変更時には、現在のサブスクリプションの情報が UI にあらかじめ表示されます。  
  
 配信拡張機能では、サブスクリプション UI が ASP.NET ユーザー コントロールとして提供されます。 レポート サーバーでは、サブスクリプション UI を表示するとき、配信拡張機能で定義されたユーザー コントロールを組み込みます。 この機能を可能にする抽象メソッドを提供する基本インターフェイスは <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> インターフェイスです。 このインターフェイスでは、入力値の検証など、一般的な操作が正しく実行されます。 また、基本ユーザー コントロールには、レポート サーバーがサブスクリプション間での一貫性を保つために使用する既定のプロパティ セットが用意されています。 これらのプロパティは、レポート マネージャーと統合された配信拡張機能で必要となります。  
  
 レポート マネージャー用のサブスクリプション UI を作成するため、配信プロバイダーに <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> インターフェイスを実装できます。 <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> インターフェイスは、ユーザーがサブスクリプション設定の値を入力できるようにし、配信拡張機能に必要な設定を処理し、設定を検証するためのインフラストラクチャを提供します。  
  
> [!NOTE]  
>  配信拡張機能の一部として <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> インターフェイスを実装する必要はありません。 配信拡張機能を使用するサブスクリプションは、SOAP API メソッドの <xref:ReportService2010.ReportingService2010.CreateSubscription%2A> および <xref:ReportService2010.ReportingService2010.CreateDataDrivenSubscription%2A> を代用していつでも作成できます。 サブスクリプションと配信を管理する SOAP API 機能の詳細については、「[サブスクリプション メソッドおよび配信メソッド](../../../reporting-services/report-server-web-service/methods/subscription-and-delivery-methods.md)」を参照してください。  
  
 <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> インターフェイスは <xref:Microsoft.ReportingServices.Interfaces.IExtension> を拡張します。 <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> を実装するユーザー コントロールも **System.Web.UI.WebControls.WebControl** から継承する必要があります。 **WebControl** クラスの詳細については、『[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 開発者ガイド』を参照してください。  
  
 <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> インターフェイスの使用例については、「[SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889)」 (SQL Server Reporting Services 製品サンプル) を参照してください。  
  
## <a name="see-also"></a>参照  
 [配信拡張機能の実装](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Reporting Services 拡張機能ライブラリ](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  

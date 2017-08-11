---
title: "Implementing a Delivery Extension |Microsoft ドキュメント"
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
- delivery [Reporting Services]
- custom delivery extensions [Reporting Services]
- extensions [Reporting Services], delivery
- delivery extensions [Reporting Services]
ms.assetid: 600cd229-efcd-480e-8c95-3c3c39ff4e7a
caps.latest.revision: 32
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 5db9bf52437c018bc1dcb40e7fa8a8ce2824fa12
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="implementing-a-delivery-extension"></a>配信拡張機能の実装
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]により、ユーザーを作成し、パブリッシュするレポートを作成し、パブリッシュした後のさまざまな場所に配信されることができます。 さらに、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] には配信拡張機能と配信 API も用意されています。開発者は別の配信拡張機能を作成し、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] の配信機能をさらに拡張することもできます。  
  
 配信拡張機能のサンプル実装では、次を参照してください。 [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889)です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [配信拡張機能の概要](../../../reporting-services/extensions/delivery-extension/delivery-extensions-overview.md)  
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] のカスタム配信拡張機能の記述方法について説明します。  
  
 [配信拡張機能を実装する準備をしています](../../../reporting-services/extensions/delivery-extension/preparing-to-implement-a-delivery-extension.md)  
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 配信拡張機能を実装する場合に使用できるインターフェイスとクラスに加え、実装前に考慮する問題についても説明します。  
  
 [配信拡張機能ライブラリを作成します。](../../../reporting-services/extensions/delivery-extension/creating-a-delivery-extension-library.md)  
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 配信拡張機能の名前空間の割り当て、および配信拡張機能のライブラリ DLL へのコンパイルについて説明します。  
  
 [配信拡張機能に対する IDeliveryExtension インターフェイスを実装します。](../../../reporting-services/extensions/delivery-extension/implementing-the-ideliveryextension-interface-for-a-delivery-extension.md)  
 配信拡張機能の属性、および独自の配信拡張機能クラスを実装する方法について説明します。  
  
 [配信拡張機能の Notification クラスの使用](../../../reporting-services/extensions/delivery-extension/using-a-notification-class-for-a-delivery-extension.md)  
 属性について説明します、**通知**クラスと配信拡張機能の実装で使用する方法です。  
  
 [配信拡張機能の設定クラスの使用](../../../reporting-services/extensions/delivery-extension/using-the-setting-class-for-a-delivery-extension.md)  
 属性について説明します、**設定**クラスと配信拡張機能の実装で使用する方法です。  
  
 [配信拡張機能の IDeliveryReportServerInformation インターフェイスの使用](../../../reporting-services/extensions/delivery-extension/using-the-ideliveryreportserverinformation-interface-for-a-delivery-extension.md)  
 属性について説明します、 **IDeliveryReportServerInformation**インターフェイスと、配信拡張機能の実装で使用する方法です。  
  
 [配信拡張機能のレポート クラスの使用](../../../reporting-services/extensions/delivery-extension/using-the-report-class-for-a-delivery-extension.md)  
 属性について説明します、**レポート**クラスと配信拡張機能の実装で使用する方法です。  
  
 [配信拡張機能の RenderedOutputFile クラスの使用](../../../reporting-services/extensions/delivery-extension/using-the-renderedoutputfile-class-for-a-delivery-extension.md)  
 属性について説明します、 **RenderedOutputFile**クラスと配信拡張機能の実装で使用する方法です。  
  
 [配信拡張機能の ISubscriptionBaseUIUserControl インターフェイスを実装します。](../../../reporting-services/extensions/delivery-extension/implementing-the-isubscriptionbaseuiusercontrol-interface.md)  
 配信拡張機能ユーザー コントロールの属性、およびサブスクリプションに独自のインターフェイスを実装する方法について説明します。  
  
 [配信拡張機能の配置](../../../reporting-services/extensions/delivery-extension/deploying-a-delivery-extension.md)  
 配信拡張機能の配置方法について説明します。  
  
 [配信拡張機能コードのデバッグ](../../../reporting-services/extensions/delivery-extension/debugging-delivery-extension-code.md)  
 配信拡張機能でのコードのデバッグ方法について説明します。  
  
 [配信拡張機能を削除します。](../../../reporting-services/extensions/delivery-extension/removing-a-delivery-extension.md)  
 レポート サーバーから配信拡張機能を削除する方法について説明します。  
  
## <a name="see-also"></a>参照  
 [Reporting Services 拡張機能](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Reporting Services 拡張機能ライブラリ](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  

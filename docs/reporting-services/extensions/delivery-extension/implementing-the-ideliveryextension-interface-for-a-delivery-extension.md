---
title: "配信拡張機能に対する IDeliveryExtension インターフェイスを実装する |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
- delivery extensions [Reporting Services], attributes
- delivery extensions [Reporting Services], class creation
- IDeliveryExtension interface
ms.assetid: ab0344db-510b-403f-8dbf-b9831553765d
caps.latest.revision: 37
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: ac54345b14ba3ff84a755e0ce4e8b1c4e9acab13
ms.contentlocale: ja-jp
ms.lasthandoff: 08/12/2017

---
# <a name="implementing-the-ideliveryextension-interface-for-a-delivery-extension"></a>配信拡張機能に対する IDeliveryExtension インターフェイスの実装
  配信拡張機能のクラスは、通知のコンテンツに基づいてレポート通知をユーザーに配信する場合に使用します。 配信拡張機能のクラスは、配信拡張機能に渡すユーザー設定を検証するためのインフラストラクチャも提供します。 また、配信拡張機能のクラスには、クライアントが拡張機能の名前に関する情報を取得する場合に使用できる特定のプロパティ、拡張機能がサポートする設定、および配信拡張機能で使用できる表示形式が含まれている必要があります。  
  
 ![IDeliveryExtension インターフェイス プロセス](../../../reporting-services/extensions/delivery-extension/media/bk-ext-02.gif "IDeliveryExtension インターフェイスの処理")  
IDeliveryExtension インターフェイスを使用すると、ユーザー データを検証できることに加えて、クライアントが必要な配信設定を学習することもできます。  
  
 配信拡張機能のクラスを作成するには、<xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> および <xref:Microsoft.ReportingServices.Interfaces.IExtension> を実装します。 **IDeliveryExtension**インターフェイスを使用してレポート通知を配信する配信拡張機能は有効、<xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A>メソッドを使用して入力方向の拡張機能の設定を検証して、<xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ValidateUserData%2A>メソッドです。 **IExtension**インターフェイスにより、ローカライズされた拡張機能名を実装し、格納されている拡張機能に固有の構成情報を処理するための配信拡張機能、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]構成ファイル。 実装することによって**IExtension**、配信拡張機能が含まれています、<xref:Microsoft.ReportingServices.Interfaces.Extension.LocalizedName%2A>プロパティです。 強くお勧めする[!INCLUDE[ssRS](../../../includes/ssrs-md.md)]配信拡張機能のサポート、 **LocalizedName**プロパティがユーザーに、レポート マネージャーなどのユーザー インターフェイスで拡張機能の既知の名前が表示されます。  
  
 配信拡張機能を実装する必要がありますも、 **ExtensionSettings**のプロパティ、 **IDeliveryExtension**インターフェイスです。 レポート サーバーは、<xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ExtensionSettings%2A> プロパティから返された値を使用して、配信拡張機能が必要とする設定を評価します。 配信拡張機能と対話するクライアントは、レポート サーバー Web サービスの <xref:ReportService2010.ReportingService2010.GetExtensionSettings%2A> メソッドを使用して、配信拡張機能の設定一覧を返します。  
  
 配信拡張機能のクラスを使用すると、RSReportServer.config ファイルに格納されたカスタム構成データを取得および処理することもできます。 カスタム構成データの処理の詳細については、<xref:Microsoft.ReportingServices.Interfaces.IExtension.SetConfiguration%2A> メソッドを参照してください。  
  
 サンプルの**IDeliveryExtension**クラス実装を参照してください[SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889)です。  
  
## <a name="see-also"></a>参照  
 [Implementing a Delivery Extension](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Reporting Services 拡張機能ライブラリ](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  


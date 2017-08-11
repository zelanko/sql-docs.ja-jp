---
title: "承認方法 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
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
- security [Reporting Services], reports
- authorization [Reporting Services]
- reports [Reporting Services], security
- tasks [Reporting Services]
- roles [Reporting Services], methods
ms.assetid: 45e9cf2c-facf-4801-9482-c855403f42a8
caps.latest.revision: 42
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: eb327018c69059a27f7ff21a8f487f2a4eb6f306
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="authorization-methods"></a>Authorization メソッド
  以下のメソッドを使用して、レポート サーバーでタスク、ロール、およびポリシーを管理できます。  
  
|方法|操作|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.CreateRole%2A>|新しいロールをレポート サーバー データベースに追加します。 このメソッド = ネイティブ モードのみに適用されます。|  
|<xref:ReportService2010.ReportingService2010.DeleteRole%2A>|レポート サーバー データベースからロールを削除します。 このメソッドはネイティブ モードにのみ適用されます。|  
|<xref:ReportService2010.ReportingService2010.GetPermissions%2A>|レポート サーバー データベースまたは SharePoint ライブラリ内の特定のアイテムに関連付けられているユーザーのアクセス許可を返します。|  
|<xref:ReportService2010.ReportingService2010.GetPolicies%2A>|レポート サーバー データベースまたは SharePoint ライブラリ内の特定のアイテムに関連付けられているポリシーを返します。|  
|<xref:ReportService2010.ReportingService2010.GetRoleProperties%2A>|ロールのメタデータ プロパティと関連付けられたタスクのコレクションを返します。|  
|<xref:ReportService2010.ReportingService2010.GetSystemPermissions%2A>|ユーザーのシステム権限を返します。 このメソッドはネイティブ モードにのみ適用されます。|  
|<xref:ReportService2010.ReportingService2010.GetSystemPolicies%2A>|システム ポリシーに関連付けられるグループとロールを含むシステム ポリシーを返します。 このメソッドはネイティブ モードにのみ適用されます。|  
|<xref:ReportService2010.ReportingService2010.InheritParentSecurity%2A>|レポート サーバー データベース内の特定のアイテムに関連付けられているポリシーを削除し、その親のアイテムのセキュリティ ポリシーを設定します。|  
|<xref:ReportService2010.ReportingService2010.IsSSLRequired%2A>|<xref:ReportService2010> エンドポイントを使用するために SSL (Secure Sockets Layer) プロトコルが必要かどうかを示すブール値を返します。|  
|<xref:ReportService2010.ReportingService2010.ListRoles%2A>|レポート サーバーによって管理されるロールの名前と説明を返します。|  
|<xref:ReportExecution2005.ReportExecutionService.ListSecureMethods%2A>|呼び出し時にセキュリティで保護された接続が必要な、<xref:ReportExecution2005> エンドポイントの Simple Object Access Protocol (SOAP) メソッドの一覧を返します。 **SecureConnectionLevel**レポート サーバーの設定を使用する方法を返すかを判断します。|  
|<xref:ReportService2010.ReportingService2010.ListTasks%2A>|レポート サーバーが管理するタスクを返します。|  
|<xref:ReportService2010.ReportingService2010.SetPolicies%2A>|指定したアイテムに関連付けられたポリシーを設定します。|  
|<xref:ReportService2010.ReportingService2010.SetRoleProperties%2A>|ロールのメタデータ プロパティを設定し、一連のタスクをロールに関連付けます。 このメソッドはネイティブ モードにのみ適用されます。|  
|<xref:ReportService2010.ReportingService2010.SetSystemPolicies%2A>|グループと、それらに関連付けられたロールを定義するシステム ポリシーを設定します。 このメソッドはネイティブ モードにのみ適用されます。|  
  
## <a name="see-also"></a>参照  
 [Web サービスと、.NET Framework を使用してアプリケーションの構築](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [レポート サーバー Web サービス](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [レポート サーバー Web サービス メソッド](../../../reporting-services/report-server-web-service/methods/report-server-web-service-methods.md)   
 [テクニカル リファレンス & #40 です。SSRS &#41;](../../../reporting-services/technical-reference-ssrs.md)  
  
  

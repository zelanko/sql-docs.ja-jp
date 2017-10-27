---
title: "データ処理拡張機能の Connection クラスの実装 |Microsoft ドキュメント"
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
- connections [Reporting Services], data processing extensions
- Connection class
- data processing extensions [Reporting Services], connections
ms.assetid: 7047d29e-a2c9-4e6f-ad02-635851a38ed7
caps.latest.revision: 42
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 19f059c0041cc9effc48e0db9c4b5ef1a504d020
ms.contentlocale: ja-jp
ms.lasthandoff: 08/12/2017

---
# <a name="implementing-a-connection-class-for-a-data-processing-extension"></a>データ処理拡張機能の Connection クラスの実装
  **接続**オブジェクトはデータベース接続や類似するリソースを表し、ユーザーのための出発点は、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]データ処理拡張機能です。 これを表します。 データベース サーバーへの接続と同様の動作を持つエンティティを公開することができます、**接続**です。  
  
 実装する、**接続**オブジェクトを実装するクラスを作成する<xref:Microsoft.ReportingServices.DataProcessing.IDbConnection>し、必要に応じて実装<xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension>です。  
  
 実装では、接続が作成され、開かれていることを確認した後でコマンドを実行する必要があります。 実装にはクライアントが接続を明示的に開閉する必要があります。実装がクライアントの接続を暗黙的に開閉するのではありません。 接続を取得したら、セキュリティ チェックを実行します。 [!INCLUDE[ssRS](../../../includes/ssrs-md.md)] データ処理拡張機能で他のクラスの既存接続が必要な場合は、データ ソースの操作時にセキュリティ チェックが常に確実に実行されるようにします。  
  
 該当する接続のプロパティは、接続文字列として表されます。 OLE DB によって定義されている使い慣れた名前と値のペアを使用して、[!INCLUDE[ssRS](../../../includes/ssrs-md.md)] データ処理拡張機能で <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection.ConnectionString%2A> プロパティをサポートすることを強くお勧めします。  
  
> [!NOTE]  
>  **接続**オブジェクトは、多くの場合、リソースを消費するのには、接続またはこれを軽減するには、他の手法をプールすることができます。  
  
 <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection> は、<xref:Microsoft.ReportingServices.Interfaces.IExtension> から継承されます。 <xref:Microsoft.ReportingServices.Interfaces.IExtension> インターフェイスは、Connection クラス実装の一部として実装する必要があります。 <xref:Microsoft.ReportingServices.Interfaces.IExtension> インターフェイスによって、クラスがローカライズされた拡張機能名を実装し、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 構成ファイルに格納された拡張機能固有の構成情報を処理できるようになります。  
  
 **接続**オブジェクトが含まれています、<xref:Microsoft.ReportingServices.Interfaces.IExtension.LocalizedName%2A>プロパティの実装を通じて<xref:Microsoft.ReportingServices.Interfaces.IExtension>です。 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] データ処理拡張機能で <xref:Microsoft.ReportingServices.Interfaces.IExtension.LocalizedName%2A> プロパティをサポートすることを強くお勧めします。これにより、レポート マネージャーなどのユーザー インターフェイスの拡張機能に、ローカライズされた使い慣れた名前がユーザーに表示されます。  
  
 <xref:Microsoft.ReportingServices.Interfaces.IExtension>できます、**接続**オブジェクトを取得して、RSReportServer.config ファイルに格納されているカスタム構成データを処理します。 カスタム構成データの処理の詳細については、<xref:Microsoft.ReportingServices.Interfaces.IExtension.SetConfiguration%2A> メソッドを参照してください。  
  
 <xref:Microsoft.ReportingServices.Interfaces.IExtension> を実装するクラスは、残りのデータ処理拡張機能のクラスが読み込まれていない場合は、メモリから読み込まれません。 このため、使用することができます、**拡張子**クロス接続の状態情報を格納する、またはメモリにキャッシュできるデータを格納するクラス。 **拡張子**クラスは、レポート サーバーが実行されている限りメモリに残ります。  
  
 拡張することができます、**接続**で資格情報をサポートするようにクラス[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]実装することによって<xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension>です。 実装する場合、 <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension.IntegratedSecurity%2A>、 <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension.UserName%2A>、および<xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension.Password%2A>のプロパティ、<xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension>インターフェイスを有効にする、**統合セキュリティ** チェック ボックスと**ユーザー名**と**パスワード**のテキスト ボックス、**データ ソース**レポート デザイナーでダイアログ。 これによって、レポート デザイナーは承認をサポートするデータ ソースの資格情報を格納および取得できます。 資格情報は、セキュリティによって保護されて格納され、プレビュー モードでレポートを表示する場合に使用されます。  
  
> [!NOTE]  
>  <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension> を暗黙的に実装するには、<xref:Microsoft.ReportingServices.DataProcessing.IDbConnection> インターフェイスと <xref:Microsoft.ReportingServices.Interfaces.IExtension> インターフェイスのメンバーを実装する必要があります。  
>   
>  サンプルの**接続**クラス実装を参照してください[SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889)です。  
  
## <a name="see-also"></a>参照  
 [Reporting Services 拡張機能](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [データ処理拡張機能の実装](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Reporting Services 拡張機能ライブラリ](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  


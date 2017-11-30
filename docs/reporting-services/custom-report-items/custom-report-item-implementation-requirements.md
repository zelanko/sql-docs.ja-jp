---
title: "カスタム レポート アイテムの実装要件 | Microsoft Docs"
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
applies_to: SQL Server 2016 Preview
helpviewer_keywords: custom report items
ms.assetid: cfacd816-00d6-4a3d-be72-1bba6f7f6886
caps.latest.revision: "22"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 16af6523c736dbf66908f544d1929675a51a8509
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="custom-report-item-implementation-requirements"></a>カスタム レポート アイテムの実装要件
  このトピックでは、カスタム レポート アイテムの開発と配置の前提条件について説明します。  
  
## <a name="development-and-deployment-requirements"></a>開発と配置の要件  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のカスタム レポート アイテムを開発するには、次の条件が必要です。  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] および [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] を使用) を実行するサーバーへの管理アクセス権を持っていること。  
  
-   [!INCLUDE[vsprvsext](../../includes/vsprvsext-md.md)] 以上と [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] ソフトウェア開発キット (SDK) がインストールされていること。  
  
-   [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK ドキュメントへのアクセス権を持つこと。  
  
-   コンポーネントの作成および [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] のコンポーネント モデル名前空間について理解していること。 詳細については、msdn.microsoft.com の「コンポーネントの作成」および「Visual Studio のコンポーネント モデルの名前空間」を参照してください。  
  
## <a name="language-and-namespace-requirements"></a>言語と名前空間の要件  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] カスタム レポート アイテムは、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] を完全にサポートしています。 任意の .NET 準拠の言語を使用してカスタム レポート アイテムを開発できます。  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] には、反復的なコーディング、デバッグ、テストのサイクルを簡素化および高速化し、開発を容易にするための多数のツールと機能が備わっています。 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK には、[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] コンパイラと C# コンパイラ、および関連ツールが含まれています。  
  
-   カスタム レポート アイテムでは、**Microsoft.ReportDesigner** および <xref:Microsoft.ReportingServices.Interfaces> 名前空間を使用します。 これらは、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の一部としてインストールされた Microsoft.ReportingServices.Designer.DLL アセンブリと Microsoft.ReportingServices.Interfaces.DLL アセンブリに格納されています。  
  
-   カスタム レポート アイテムのデザイン時コンポーネントは、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 内の <xref:System.ComponentModel> 名前空間からインターフェイスを実装する必要があります。 <xref:System.ComponentModel> は、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK ドキュメントに記載されています。  
  
> [!IMPORTANT]  
>  既定では、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と共にインストールされますが、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK はインストールされません。 SDK がコンピューターにインストールされておらず、SDK ドキュメントがオンライン ブック コレクションにも含まれていない場合、このセクションの SDK コンテンツへのリンクは機能しません。 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK をインストールしたら、「[SQL Server の製品ドキュメントの追加または削除](http://msdn.microsoft.com/library/ef798cc8-87cf-4d60-a7bf-9e061bdd0052)」の手順に従って、SDK ドキュメントをオンライン ブック コレクションと目次に追加できます。  
  
## <a name="see-also"></a>参照  
 [カスタム レポート アイテムの実行時コンポーネントの作成](../../reporting-services/custom-report-items/creating-a-custom-report-item-run-time-component.md)   
 [カスタム レポート アイテムのデザイン時コンポーネントの作成](../../reporting-services/custom-report-items/creating-a-custom-report-item-design-time-component.md)   
 [カスタム レポート アイテムを配置する方法](../../reporting-services/custom-report-items/how-to-deploy-a-custom-report-item.md)   
 [カスタム レポート アイテムのクラス ライブラリ](../../reporting-services/custom-report-items/custom-report-item-class-libraries.md)  
  
  

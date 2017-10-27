---
title: "カスタム レポート アイテムの実装の要件 |Microsoft ドキュメント"
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
- custom report items
ms.assetid: cfacd816-00d6-4a3d-be72-1bba6f7f6886
caps.latest.revision: 22
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 43770b0b167e2a40874d1b8f31b3b146e62ec2b5
ms.contentlocale: ja-jp
ms.lasthandoff: 08/12/2017

---
# <a name="custom-report-item-implementation-requirements"></a>カスタム レポート アイテムの実装要件
  このトピックでは、カスタム レポート アイテムの開発と配置の前提条件について説明します。  
  
## <a name="development-and-deployment-requirements"></a>開発と配置の要件  
 カスタム レポート アイテムの開発[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]以下が必要です。  
  
-   実行するサーバーへの管理アクセス[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]と[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]です。  
  
-   [!INCLUDE[vsprvsext](../../includes/vsprvsext-md.md)]以上で、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]ソフトウェア開発キット (SDK) にインストールされています。  
  
-   [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK ドキュメントへのアクセス権を持つこと。  
  
-   コンポーネントの作成および [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] のコンポーネント モデル名前空間について理解していること。 詳細については、msdn.microsoft.com の「コンポーネントの作成」および「Visual Studio のコンポーネント モデルの名前空間」を参照してください。  
  
## <a name="language-and-namespace-requirements"></a>言語と名前空間の要件  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] カスタム レポート アイテムは、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] を完全にサポートしています。 任意の .NET 準拠の言語を使用してカスタム レポート アイテムを開発できます。  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] には、反復的なコーディング、デバッグ、テストのサイクルを簡素化および高速化し、開発を容易にするための多数のツールと機能が備わっています。 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK には、[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] コンパイラと C# コンパイラ、および関連ツールが含まれています。  
  
-   カスタム レポート アイテムを使用して、 **Microsoft.ReportDesigner**と<xref:Microsoft.ReportingServices.Interfaces>名前空間。 これらは、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の一部としてインストールされた Microsoft.ReportingServices.Designer.DLL アセンブリと Microsoft.ReportingServices.Interfaces.DLL アセンブリに格納されています。  
  
-   カスタム レポート アイテムのデザイン時コンポーネントは、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 内の <xref:System.ComponentModel> 名前空間からインターフェイスを実装する必要があります。 <xref:System.ComponentModel> は、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK ドキュメントに記載されています。  
  
> [!IMPORTANT]  
>  既定では、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と共にインストールされますが、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK はインストールされません。 SDK がコンピューターにインストールされておらず、SDK ドキュメントがオンライン ブック コレクションにも含まれていない場合、このセクションの SDK コンテンツへのリンクは機能しません。 インストールした後、 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK に追加できます、SDK のドキュメント、オンライン ブック コレクションと目次の次の手順で[の追加と SQL Server の製品ドキュメントを削除する](http://msdn.microsoft.com/library/ef798cc8-87cf-4d60-a7bf-9e061bdd0052)です。  
  
## <a name="see-also"></a>参照  
 [カスタム レポート アイテムの実行時コンポーネントの作成](../../reporting-services/custom-report-items/creating-a-custom-report-item-run-time-component.md)   
 [カスタム レポート アイテムのデザイン時コンポーネントの作成](../../reporting-services/custom-report-items/creating-a-custom-report-item-design-time-component.md)   
 [方法: カスタム レポート アイテムを配置](../../reporting-services/custom-report-items/how-to-deploy-a-custom-report-item.md)   
 [カスタム レポート アイテムのクラス ライブラリ](../../reporting-services/custom-report-items/custom-report-item-class-libraries.md)  
  
  


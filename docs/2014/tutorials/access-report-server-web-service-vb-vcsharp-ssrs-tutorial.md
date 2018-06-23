---
title: Visual Basic または Visual c# (SSRS チュートリアル) を使用してレポート サーバー Web サービスにアクセスする |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- walkthroughs [Reporting Services]
- Reporting Services, Web service
- Web service [Reporting Services], tutorials
ms.assetid: cf688163-4ac0-475b-b6dd-6f2f05b553c6
caps.latest.revision: 45
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 7fc7e1ab0e855bd9ddd208b295cf3a10d44dfce7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36072011"
---
# <a name="accessing-the-report-server-web-service-using-visual-basic-or-visual-c-ssrs-tutorial"></a>Visual Basic または Visual C# を使用したレポート サーバー Web サービスへのアクセス (SSRS チュートリアル)
  次のチュートリアルで作成したアプリケーションからレポート サーバー Web サービスにアクセスする方法を示します[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[vbprvb](../includes/vbprvb-md.md)]または[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[csprcs](../includes/csprcs-md.md)]です。  
  
## <a name="what-you-will-learn"></a>学習する内容  
 このチュートリアルでは次の作業を行います。  
  
-   使用してクライアント アプリケーションを作成、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]コンソール アプリケーション プロジェクト テンプレート。  
  
-   レポート サーバー Web サービスの Web 参照を追加する。  
  
-   Web サービスにアクセスするコードを記述する。  
  
-   デバッグ モードでコンソール アプリケーションを実行する。  
  
## <a name="requirements"></a>要件  
 このチュートリアルを完了するには次の準備が必要です。  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]。  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] または類似した[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]-互換性のある開発ツールです。  
  
-   レポート サーバーが配置されているコンピューター上の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] レポート サーバー Web サービスにアクセスできる十分な権限。  
  
-   レポート サーバーにインストールされているレポート。 このチュートリアルでは、サンプル レポート Company Sales を使用します。 サンプル レポートの詳細については、次を参照してください。 [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889)です。  
  
> [!NOTE]  
>  サンプルはセットアップ中に自動的にインストールされませんが、いつでもインストールできます。 サンプルについては、次を参照してください。 [SQL Server Product Samples](http://go.microsoft.com/fwlink/?LinkId=182887)です。  
  
 **このチュートリアルを完了する時間を推定:** 60 分  
  
## <a name="tasks"></a>処理手順  
 [レッスン 1: Web サービス クライアント プロジェクトの作成](../../2014/tutorials/lesson-1-creating-the-web-service-client-project.md)  
  
 [レッスン 2: Web 参照の追加](../../2014/tutorials/lesson-2-adding-a-web-reference.md)  
  
 [レッスン 3: Web サービスへのアクセス](../../2014/tutorials/lesson-3-accessing-the-web-service.md)  
  
 [レッスン 4: アプリケーションを実行する&#40;VB VC&#35;&#41;](../../2014/tutorials/lesson-4-running-the-application-vb-vcsharp.md)  
  
  
---
title: CA でのサイト コレクションの Power Pivot の統合をアクティブ化 |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ppvt-sharepoint
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 564ff616ec13b5f7f669db4cf6402114175f5670
ms.sourcegitcommit: 9f2edcdf958e6afce9a09fb2e572ae36dfe9edb0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2018
ms.locfileid: "50100063"
---
# <a name="activate-power-pivot-integration-for-site-collections-in-ca"></a>CA でのサイト コレクションの Power Pivot の統合をアクティブ化します。
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [既存のファーム] インストール オプションを使用して SQL Server [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] をインストールした場合は、サイト コレクションごとに [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 機能の統合をアクティブ化する必要があります。 [新しいサーバー] インストール オプションを使用して [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint をインストールした場合は、この作業は必要ありません。このオプションでは、SQL Server セットアップで配置を構成するときに、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 機能の統合がルート サイト コレクションに対してアクティブ化されます。  
  
 サイトでアプリケーション ページやテンプレートを使用できるようにするには、サイト コレクション レベルで機能をアクティブ化する必要があります。これには、定期データを更新するための構成ページや、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ギャラリーとデータ フィード ライブラリのアプリケーション ページなどが含まれます。  
  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 統合は、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] クエリ処理をサポートするサイト コレクションごとにアクティブ化する必要があります。  
  
## <a name="prerequisites"></a>前提条件  
 サイト コレクション管理者である必要があります。  
  
## <a name="activate-power-pivot-features"></a>Power Pivot 機能のアクティブ化  
  
1.  SharePoint サイトで、 **[サイトの操作]** をクリックします。  
  
     既定では、SharePoint Web アプリケーションへのアクセスにはポート 80 が使用されます。 つまり http:// を入力して、SharePoint サイトを多くの場合、アクセスできる\<コンピューター名 > をルート サイト コレクションを開きます。  
  
2.  **[サイトの設定]** をクリックします。  
  
3.  [サイト コレクションの管理] で **[サイト コレクションの機能]** をクリックします。  
  
4.  **[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 統合サイト コレクション機能**が表示されるまで、ページを下にスクロールします。  
  
5.  **[アクティブ化]** をクリックします。  
  
6.  他のサイト コレクションについても、各サイトを開き、 **[サイトの操作]** をクリックして手順を繰り返します。  
  
## <a name="see-also"></a>参照  
 [サーバーの全体管理での Power Pivot サーバーの管理と構成](../../analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration.md)   
 [初期構成 (Power Pivot for SharePoint)](http://msdn.microsoft.com/3a0ec2eb-017a-40db-b8d4-8aa8f4cdc146)   
 [Power Pivot for SharePoint 2010 のインストール](http://msdn.microsoft.com/8d47dde7-c941-4280-a934-e2fe3f9a938f)  
  
  

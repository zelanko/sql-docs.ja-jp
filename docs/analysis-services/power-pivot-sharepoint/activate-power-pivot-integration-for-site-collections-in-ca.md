---
title: "CA でのサイト コレクションの Power Pivot の統合をアクティブ化 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 62a27e53-446a-42d7-b5db-c009e02d4904
caps.latest.revision: 8
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e4c3c7403a6fefb42c15f8b4ba71af403195a057
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="activate-power-pivot-integration-for-site-collections-in-ca"></a>CA でのサイト コレクションの Power Pivot の統合をアクティブ化します。
  [既存のファーム] インストール オプションを使用して SQL Server [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] をインストールした場合は、サイト コレクションごとに [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 機能の統合をアクティブ化する必要があります。 [新しいサーバー] インストール オプションを使用して [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint をインストールした場合は、この作業は必要ありません。このオプションでは、SQL Server セットアップで配置を構成するときに、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 機能の統合がルート サイト コレクションに対してアクティブ化されます。  
  
 サイトでアプリケーション ページやテンプレートを使用できるようにするには、サイト コレクション レベルで機能をアクティブ化する必要があります。これには、定期データを更新するための構成ページや、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ギャラリーとデータ フィード ライブラリのアプリケーション ページなどが含まれます。  
  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 統合は、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] クエリ処理をサポートするサイト コレクションごとにアクティブ化する必要があります。  
  
## <a name="prerequisites"></a>前提条件  
 サイト コレクション管理者である必要があります。  
  
## <a name="activate-power-pivot-features"></a>Power Pivot 機能のアクティブ化  
  
1.  SharePoint サイトで、 **[サイトの操作]**をクリックします。  
  
     既定では、SharePoint Web アプリケーションへのアクセスにはポート 80 が使用されます。 つまり、多くの場合、http:// を入力することで SharePoint サイトにアクセスすることができます、\<コンピューター名 > を開くには、ルート サイト コレクション。  
  
2.  **[サイトの設定]**をクリックします。  
  
3.  [サイト コレクションの管理] で **[サイト コレクションの機能]**をクリックします。  
  
4.  **[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 統合サイト コレクション機能**が表示されるまで、ページを下にスクロールします。  
  
5.  **[アクティブ化]**をクリックします。  
  
6.  他のサイト コレクションについても、各サイトを開き、 **[サイトの操作]**をクリックして手順を繰り返します。  
  
## <a name="see-also"></a>参照  
 [サーバーの全体管理での Power Pivot サーバーの管理と構成](../../analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration.md)   
 [初期構成 (Power Pivot for SharePoint)](http://msdn.microsoft.com/en-us/3a0ec2eb-017a-40db-b8d4-8aa8f4cdc146)   
 [Power Pivot for SharePoint 2010 のインストール](http://msdn.microsoft.com/en-us/8d47dde7-c941-4280-a934-e2fe3f9a938f)  
  
  


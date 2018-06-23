---
title: サーバーの全体管理のサイト コレクションの PowerPivot 機能の統合をアクティブ化 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 62a27e53-446a-42d7-b5db-c009e02d4904
caps.latest.revision: 5
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 00e8f0336c075c14feb8c4e3b4a8b43e0ebdaf9e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36173348"
---
# <a name="activate-powerpivot-feature-integration-for-site-collections-in-central-administration"></a>サイト コレクションを対象とした PowerPivot 機能の統合をサーバーの全体管理でアクティブ化する方法
  [既存のファーム] インストール オプションを使用して SQL Server PowerPivot for SharePoint をインストールした場合は、サイト コレクションごとに PowerPivot 機能の統合をアクティブ化する必要があります。 [新しいサーバー] インストール オプションを使用して PowerPivot for SharePoint をインストールした場合は、この作業は必要ありません。このオプションでは、SQL Server セットアップで配置を構成するときに、PowerPivot 機能の統合がルート サイト コレクションに対してアクティブ化されます。  
  
 サイトでアプリケーション ページやテンプレートを使用できるようにするには、サイト コレクション レベルで機能をアクティブ化する必要があります。これには、定期データを更新するための構成ページや、PowerPivot ギャラリーとデータ フィード ライブラリのアプリケーション ページなどが含まれます。  
  
 PowerPivot 統合は、PowerPivot クエリ処理をサポートするサイト コレクションごとにアクティブ化する必要があります。  
  
## <a name="prerequisites"></a>前提条件  
 サイト コレクション管理者である必要があります。  
  
## <a name="activate-powerpivot-features"></a>PowerPivot 機能のアクティブ化  
  
1.  SharePoint サイトで、 **[サイトの操作]** をクリックします。  
  
     既定では、SharePoint Web アプリケーションへのアクセスにはポート 80 が使用されます。 つまり、多くの場合、http:// を入力することで SharePoint サイトにアクセスすることができます、\<コンピューター名 > を開くには、ルート サイト コレクション。  
  
2.  **[サイトの設定]** をクリックします。  
  
3.  [サイト コレクションの管理] で **[サイト コレクションの機能]** をクリックします。  
  
4.  ページが表示されるまで下へスクロールして**PowerPivot 統合サイト コレクション機能**します。  
  
5.  **[アクティブ化]** をクリックします。  
  
6.  他のサイト コレクションについても、各サイトを開き、 **[サイトの操作]** をクリックして手順を繰り返します。  
  
## <a name="see-also"></a>参照  
 [サーバーの全体管理で PowerPivot サーバーの管理と構成](power-pivot-server-administration-and-configuration-in-central-administration.md)   
 [構成の初期&#40;PowerPivot for SharePoint&#41;](../../sql-server/install/initial-configuration-powerpivot-for-sharepoint.md)   
 [PowerPivot for SharePoint 2010 のインストール](../../sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
---
title: "概要: エクスポートのデータ (Master Data Services) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exporting data [Master Data Services]
- subscription views [Master Data Services]
- subscription views [Master Data Services], about subscription views
ms.assetid: 8b74409a-ea70-45f8-84c7-da6905e4901a
caps.latest.revision: 12
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e22f2f7056bebc648b1ead5d577613e2f252bcbe
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="overview-exporting-data-master-data-services"></a>概要: データのエクスポート (Master Data Services)
  この記事では、サブスクリプション ビュー形式の種類と、モデル オブジェクトが変更されたためにビューを編集する必要がある場合を判断する方法について説明します。  
  
 サブスクリプション ビューを作成して、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データを [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のようなサブスクライブ システムにエクスポートします。 サブスクライブ システムを使用して、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースのデータを表示します。  サブスクライブ ビューを作成する方法については、「 [サブスクリプション ビューを作成してデータをエクスポートする (マスター データ サービス)](../master-data-services/create-a-subscription-view-to-export-data-master-data-services.md)  
  
 ビューの詳細については、「 [ビュー](../relational-databases/views/views.md)」を参照してください。  
  
## <a name="subscription-view-formats"></a>サブスクリプション ビュー形式  
 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]でビューを作成する場合は、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] によって提供される一連の標準ビュー形式から選択します。 これらの形式を使用して、以下を表示するビューを作成できます。  
  
-   すべてのリーフ メンバーとその属性  
  
-   すべての統合メンバーとその属性  
  
-   すべてのコレクションとその属性  
  
-   コレクションに明示的に追加されたメンバー  
  
-   親子形式またはレベル形式の派生階層内のメンバー  
  
-   エンティティのすべての明示的階層内のメンバー (親子形式またはレベル形式)  
  
## <a name="subscription-views-can-become-out-of-date"></a>サブスクリプション ビューが古くなる可能性  
 エンティティまたは階層のサブスクリプション ビューを作成後、関連付けられたモデル オブジェクトへの変更が自動的にビューに反映されるわけではありません。 モデル オブジェクトに対する変更を反映するには、必要に応じて [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] でサブスクリプション ビューを再生成する必要があります。 モデル オブジェクトが変更されると、 **[エクスポート]** ページの **[変更]** 列が **[True]** に更新されます。 **[True]** は、サブスクリプション ビューを編集して保存する必要があることを示します。この操作により、ビューが再生成されます。  
  
## <a name="related-tasks"></a>関連タスク  
  
|タスクの説明|トピック|  
|----------------------|-----------|  
|マスター データのサブスクリプション ビューを作成する。|[サブスクリプション ビューを作成してデータをエクスポートする (マスター データ サービス)](../master-data-services/create-a-subscription-view-to-export-data-master-data-services.md)|  
|既存のサブスクリプション ビューを削除する。|[サブスクリプション ビュー &#40; を削除します。マスター データ サービス &#41;](../master-data-services/delete-a-subscription-view-master-data-services.md)|  
  
## <a name="related-content"></a>関連コンテンツ  
  
-   [サブスクリプション ビュー形式 & #40 です。マスター データ サービス &#41;](../master-data-services/subscription-view-formats-master-data-services.md)  
  
-   [ビュー](../relational-databases/views/views.md)  
  
  

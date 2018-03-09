---
title: "Analysis Services 接続に使用するデータ プロバイダー |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/23/2018
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 128f6dde-409d-4c12-9820-3305bab57b75
caps.latest.revision: "19"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 816919b48f77a4462e8d0f0f04d0bb621a2d2058
ms.sourcegitcommit: 3206a31870f8febab7d1718fa59fe0590d4d45db
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2018
---
# <a name="client-libraries-data-providers-used-for-analysis-services-connections"></a>Analysis Services 接続に使用するクライアント ライブラリ (データ プロバイダー)
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

Analysis Services とも呼ばれる 3 つのクライアント ライブラリを提供**データ プロバイダー**サーバーとツールおよびクライアント アプリケーションからデータにアクセスするために、します。 ツールでは、SSMS と SSDT では、これらのライブラリを使用して Analysis Services に Power BI Desktop と Excel 接続などのアプリケーションと同様にします。 2 つのクライアント ライブラリ、ADOMD.NET および Analysis Services 管理オブジェクト (AMO) は、マネージ クライアント ライブラリです。 Analysis Services OLE DB プロバイダー (MSOLAP DLL) は、ネイティブ クライアント ライブラリです。 クライアント ライブラリは、SQL Server Analysis Services と Azure Analysis Services の両方で同じです。
  
##  <a name="bkmk_downloadsite"></a>新しいバージョンを取得する場所  
 クライアント コンピューターにインストールされているバージョンは、データを提供するサーバーのメジャー バージョンと一致する必要があります。 インストールされているサーバーが、ネットワーク内のワークステーションにインストールされているデータ プロバイダーより新しい場合は、新しいプロバイダーのインストールが必要になることがあります。  

以前の SQL Server Feature Pack に含まれているクライアント ライブラリは、その SQL バージョンに対応しています。ただし、最新版がありますされません。 Azure Analysis Services に接続すると、以降のバージョンが必要があります。 すべてのバージョンは、旧バージョンと互換性のあります。

最新版を取得するには、次を参照してください。 [Azure Analysis Services に接続するためのクライアント ライブラリ](https://docs.microsoft.com/azure/analysis-services/analysis-services-data-providers)です。 
  
## <a name="see-also"></a>参照  
 [Analysis Services への接続](../../analysis-services/instances/connect-to-analysis-services.md)  
  
  

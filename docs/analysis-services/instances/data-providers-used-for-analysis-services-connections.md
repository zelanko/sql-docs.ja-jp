---
title: "Analysis Services 接続に使用するデータ プロバイダー |Microsoft ドキュメント"
ms.custom: 
ms.date: 12/06/2017
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
ms.openlocfilehash: 7be1179fb84b98aa7610e76015cb957d5f18514a
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="client-libraries-data-providers-used-for-analysis-services-connections"></a>Analysis Services 接続に使用するクライアント ライブラリ (データ プロバイダー)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]

Analysis Services とも呼ばれる 3 つのクライアント ライブラリを提供**データ プロバイダー**サーバーとツールおよびクライアント アプリケーションからデータにアクセスするために、します。 ツールでは、SSMS と SSDT では、これらのライブラリを使用して Analysis Services に Power BI Desktop と Excel 接続などのアプリケーションと同様にします。 2 つのクライアント ライブラリ、ADOMD.NET および Analysis Services 管理オブジェクト (AMO) は、マネージ クライアント ライブラリです。 Analysis Services OLE DB プロバイダー (MSOLAP DLL) は、ネイティブ クライアント ライブラリです。 
  
##  <a name="bkmk_downloadsite"></a>新しいバージョンを取得する場所  
 クライアント コンピューターにインストールされているバージョンは、データを提供しているサーバーのメジャー バージョンと一致する必要があります。 インストールされているサーバーが、ネットワーク内のワークステーションにインストールされているデータ プロバイダーより新しい場合は、新しいプロバイダーのインストールが必要になることがあります。  

以前の SQL Server Feature Pack に含まれているクライアント ライブラリは、その SQL バージョンに対応しています。ただし、最新版がありますされません。 Azure Analysis Services に接続すると、以降のバージョンが必要があります。 すべてのバージョンは、旧バージョンと互換性のあります。

最新版を取得するには、次を参照してください。 [Azure Analysis Services に接続するためのクライアント ライブラリ](https://docs.microsoft.com/azure/analysis-services/analysis-services-data-providers)です。 
  
## <a name="see-also"></a>参照  
 [Analysis Services への接続](../../analysis-services/instances/connect-to-analysis-services.md)  
  
  

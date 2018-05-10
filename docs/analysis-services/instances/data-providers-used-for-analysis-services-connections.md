---
title: Analysis Services 接続に使用するデータ プロバイダー |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: ''
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7703bda267a7b646bf6ccbbfee98c7401599f3a0
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="client-libraries-data-providers-used-for-analysis-services-connections"></a>Analysis Services 接続に使用するクライアント ライブラリ (データ プロバイダー)
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

Analysis Services とも呼ばれる 3 つのクライアント ライブラリを提供**データ プロバイダー**サーバーとツールおよびクライアント アプリケーションからデータにアクセスするために、します。 ツールでは、SSMS と SSDT では、これらのライブラリを使用して Analysis Services に Power BI Desktop と Excel 接続などのアプリケーションと同様にします。 2 つのクライアント ライブラリ、ADOMD.NET および Analysis Services 管理オブジェクト (AMO) は、マネージ クライアント ライブラリです。 Analysis Services OLE DB プロバイダー (MSOLAP DLL) は、ネイティブ クライアント ライブラリです。 クライアント ライブラリは、SQL Server Analysis Services と Azure Analysis Services の両方で同じです。
  
##  <a name="bkmk_downloadsite"></a> 新しいバージョンを取得する場所  
 クライアント コンピューターにインストールされているバージョンは、データを提供するサーバーのメジャー バージョンと一致する必要があります。 インストールされているサーバーが、ネットワーク内のワークステーションにインストールされているデータ プロバイダーより新しい場合は、新しいプロバイダーのインストールが必要になることがあります。  

以前の SQL Server Feature Pack に含まれているクライアント ライブラリは、その SQL バージョンに対応しています。ただし、最新版がありますされません。 Azure Analysis Services に接続すると、以降のバージョンが必要があります。 すべてのバージョンは、旧バージョンと互換性のあります。

最新版を取得するには、次を参照してください。 [Azure Analysis Services に接続するためのクライアント ライブラリ](https://docs.microsoft.com/azure/analysis-services/analysis-services-data-providers)です。 
  
## <a name="see-also"></a>参照  
 [Analysis Services への接続](../../analysis-services/instances/connect-to-analysis-services.md)  
  
  

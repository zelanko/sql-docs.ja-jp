---
title: Analysis Services 接続に使用されるデータ プロバイダー |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f5ba97f90b877896d68cd62598f11d0845fb698e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68209529"
---
# <a name="client-libraries-data-providers-used-for-analysis-services-connections"></a>Analysis Services 接続に使用されるクライアント ライブラリ (データ プロバイダー)
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

Analysis Services とも呼ばれる 3 つのクライアント ライブラリを提供**データ プロバイダー**、サーバーおよびツールおよびクライアント アプリケーションからデータにアクセスします。 SSMS と SSDT では、これらのライブラリを使用して Analysis Services に Power BI Desktop や Excel 接続などのアプリケーションなどのツール。 クライアント ライブラリ、ADOMD.NET と Analysis Services 管理オブジェクト (AMO) の 2 つは、マネージ クライアント ライブラリです。 Analysis Services OLE DB プロバイダー (MSOLAP DLL) は、ネイティブ クライアント ライブラリです。 クライアント ライブラリは、SQL Server Analysis Services と Azure Analysis Services の両方で同じです。
  
##  <a name="bkmk_downloadsite"></a> 新しいバージョンを取得する場所  
 クライアント コンピューターにインストールされているバージョンは、データを提供しているサーバーのメジャー バージョンと一致する必要があります。 インストールされているサーバーが、ネットワーク内のワークステーションにインストールされているデータ プロバイダーより新しい場合は、新しいプロバイダーのインストールが必要になることがあります。  

以前の SQL Server Feature Pack に含まれるクライアント ライブラリは、その SQL のバージョンに対応します。ただし、最新版がありますされません。 Azure Analysis Services に接続すると、以降のバージョンが必要があります。 すべてのバージョンは、旧バージョンと互換性があります。

最新を取得するを参照してください。 [Azure Analysis Services に接続するためのクライアント ライブラリ](https://docs.microsoft.com/azure/analysis-services/analysis-services-data-providers)します。 
  
## <a name="see-also"></a>関連項目  
 [Analysis Services への接続](../../analysis-services/instances/connect-to-analysis-services.md)  
  
  

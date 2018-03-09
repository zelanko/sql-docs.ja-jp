---
title: "ADOMD.NET の再配布 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/14/2018
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- ADOMD.NET, redistributing
- redistributing ADOMD.NET
ms.assetid: f8db3c99-0243-4b92-b486-0d8786c264f4
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e4337932ea8ffe9a83d6d899e0d407aebe44dbde
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2018
---
# <a name="redistributing-adomdnet"></a>ADOMD.NET の再配布
  ADOMD.NET を使用したアプリケーションを作成する場合、アプリケーションと共に ADOMD.NET の適切なバージョンを再配布する必要があります。 ADOMD.NET を再配布するには、アプリケーションのセットアップ プログラムに ADOMD.NET セットアップ プログラムを含めます。  
  
 ADOMD.NET セットアップ プログラムと、ADOMD.NET の最新バージョンは、SQL Server Feature Pack の一部として Microsoft ダウンロード センターで見つかります。  
  
 ADOMD.NET セットアップ プログラムに ADOMD.NET ファイルがインストール\<*システム ドライブ*>: \Program Files\Microsoft.NET\ADOMD.NET\\*バージョン番号*です。  
  
 ADOMD.NET セットアップ プログラムを追加したら、アプリケーションのセットアップ プログラムで、ADOMD.NET セットアップ プログラムを起動し、ADOMD.NET をインストールします。 また、環境によっては、関連するアセンブリが SQL Server によって信頼されるようにする必要が生じることがあります。  
  
 詳細:  
  
 [Microsoft SQL Server 用 feature Pack](http://go.microsoft.com/fwlink/?LinkId=389949)  
  
 [Microsoft Connect: ADOMD.NET の依存関係](http://go.microsoft.com/fwlink/?LinkId=389950)  
  
## <a name="see-also"></a>参照  
 [ADOMD.NET クライアント プログラミング](../../../analysis-services/multidimensional-models-adomd-net-client/adomd-net-client-programming.md)   
 [ADOMD.NET サーバー プログラミング](../../../analysis-services/multidimensional-models-adomd-net-server/adomd-net-server-programming.md)  
  
  

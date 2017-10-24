---
title: "ADOMD.NET の再配布 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- ADOMD.NET, redistributing
- redistributing ADOMD.NET
ms.assetid: f8db3c99-0243-4b92-b486-0d8786c264f4
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3851f8dd3eea3fb2a98554bba365e723765a641d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

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
  
  


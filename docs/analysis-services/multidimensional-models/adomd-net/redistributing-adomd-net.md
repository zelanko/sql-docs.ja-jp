---
title: ADOMD.NET の再配布 |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: adomd
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: aef9cf75270e8fccf9572669ad0487fce96c0c61
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
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
  
  

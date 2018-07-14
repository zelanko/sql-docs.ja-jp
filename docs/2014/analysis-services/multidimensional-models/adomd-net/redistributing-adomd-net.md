---
title: ADOMD.NET の再配布 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ADOMD.NET, redistributing
- redistributing ADOMD.NET
ms.assetid: f8db3c99-0243-4b92-b486-0d8786c264f4
caps.latest.revision: 34
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6fde698740a417076f7fe139250765b9610e91b5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37245612"
---
# <a name="redistributing-adomdnet"></a>ADOMD.NET の再配布
  ADOMD.NET を使用したアプリケーションを作成する場合、アプリケーションと共に ADOMD.NET の適切なバージョンを再配布する必要があります。 ADOMD.NET を再配布するには、アプリケーションのセットアップ プログラムに ADOMD.NET セットアップ プログラムを含めます。  
  
 ADOMD.NET セットアップ プログラムと、ADOMD.NET の最新バージョンは、SQL Server Feature Pack の一部として Microsoft ダウンロード センターで見つかります。  
  
 ADOMD.NET セットアップ プログラムに ADOMD.NET ファイルがインストールされます\<*システム ドライブ*>: \Program Files\Microsoft.NET\ADOMD.NET\\*バージョン番号*します。  
  
 ADOMD.NET セットアップ プログラムを追加したら、アプリケーションのセットアップ プログラムで、ADOMD.NET セットアップ プログラムを起動し、ADOMD.NET をインストールします。 また、環境によっては、関連するアセンブリが SQL Server によって信頼されるようにする必要が生じることがあります。  
  
 詳細:  
  
 [Microsoft SQL Server 用 feature Pack](http://go.microsoft.com/fwlink/?LinkId=389949)  
  
 [Microsoft Connect: ADOMD.NET の依存関係](http://go.microsoft.com/fwlink/?LinkId=389950)  
  
## <a name="see-also"></a>参照  
 [ADOMD.NET クライアント プログラミング](../../multidimensional-models-adomd-net-client/adomd-net-client-programming.md)   
 [ADOMD.NET サーバー プログラミング](../../multidimensional-models-adomd-net-server/adomd-net-server-programming.md)  
  
  

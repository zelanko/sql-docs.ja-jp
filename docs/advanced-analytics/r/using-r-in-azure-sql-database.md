---
title: "Azure SQL データベースでの R の使用 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/16/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a90c438-d78b-47be-ac05-479de64378b2
caps.latest.revision: "1"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.openlocfilehash: 4562dc3490f4790a31b4b32e06b9e5133a151c67
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="using-r-in-azure-sql-database"></a>Azure SQL データベースでの R の使用

年 2017年 10 月で SQL Server 開発チームには、R コードでのデータベースの SQL Server 2016 での R Services のようなストアド プロシージャを使用して実行をサポートする予定が発表されました。

> [!IMPORTANT]
> 初期のプレビュー リリースが発表されたテストと探索のみ意図されました。 機能は、現在のところ、**無効になっている**開発をサポートするさらに、Azure SQL データベースでします。 

最新の状態に保持する、パブリックなスケジュールと今後のイベントのリリースを参照してください、 [SQL Server ブログ](https://blogs.technet.microsoft.com/dataplatforminsider/)または[Microsoft R Server のブログ](https://blogs.msdn.microsoft.com/rserver/)です。

**Azure リソース**

その間は、Azure Marketplace で利用できる SQL Server 2017 仮想マシンのいずれかを使用することをお勧めします。 

+ [Azure での機械学習の仮想マシンのプロビジョニングします。](provision-the-r-server-only-sql-server-2016-enterprise-vm-on-azure.md)

また、これらの Vm では、さまざまな人気の機械学習のツールが付属してあらかじめ構成されたご覧ください。

+ [データ サイエンス仮想マシン](https://docs.microsoft.com/azure/machine-learning/data-science-virtual-machine/overview)
+ [仮想マシンを深層学習](https://docs.microsoft.com/azure/machine-learning/data-science-virtual-machine/deep-learning-dsvm-overview)、 


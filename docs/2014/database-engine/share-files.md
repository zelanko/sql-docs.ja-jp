---
title: ファイルの共有 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- sharing files
- file sharing [SQL Server]
- version control services [SQL Server], file sharing
ms.assetid: 645f5c0a-e949-4e87-8988-85e4d6128464
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9e779a0c0da9920b2efda5f52135e85f31959d10
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "62843558"
---
# <a name="share-files"></a>ファイル共有
  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を使用して、ソース管理プロジェクト間で項目を共有できます。 項目を共有すると、1 つの項目に対する変更は、その項目を共有するすべてのプロジェクトに反映されます。  
  
 項目を共有すると、ソース管理のユーザーにとって以下のような利点があります。  
  
-   共有項目を使用する各プロジェクトでは、項目のコピーを個別に格納する必要がなくなり、ソース管理クライアントおよびサーバーでディスク容量を節約できます。 ソース管理プロバイダーは、中心となる 1 つの場所に共有項目を格納し、項目を共有している各プロジェクトは、その場所へのポインターを格納します。  
  
-   バージョンの非互換性を回避できます。 項目を共有している各プロジェクトでは、項目の同じバージョンを使用するため、複数のプロジェクト内で各項目のコピーが個別に変更された場合に発生する競合を回避できます。  
  
### <a name="to-share-an-item"></a>項目を共有するには  
  
1.  ソリューション エクスプローラーで、共有ファイルを配置するフォルダーまたはプロジェクトを選択します。  
  
2.  [**ファイル**] メニューの [**ソース管理**] をポイントし、[**共有**] をクリックします。  
  
3.  [**共有**する] ダイアログボックスで、共有する項目のディレクトリ一覧を参照し、その項目をクリックします。  
  
4.  [**共有**] をクリックします。  
  
## <a name="see-also"></a>参照  
 [ソース管理の基礎](../../2014/database-engine/source-control-basics.md)  
  
  

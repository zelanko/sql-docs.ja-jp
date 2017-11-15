---
title: "[パブリッシャーのプロパティ - パブリッシャー]、[パブリケーション データベース] | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.rep.configdistwizard.pubproperties.pubdb.f1
helpviewer_keywords: Publisher Properties dialog box
ms.assetid: 574ea2e7-4e7b-4733-ab52-429ca93c7b0a
caps.latest.revision: "21"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a89c93aef880f5d092c48f05bc3fef515cb8c4ff
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="publisher-properties---publisher-publication-databases"></a>[パブリッシャーのプロパティ - パブリッシャー]、[パブリケーション データベース]
  **[パブリッシャーのプロパティ]** ダイアログ ボックスの **[パブリケーション データベース]** ページを使用すると、 **sysadmin** 固定サーバー ロール内のユーザーはデータベースをレプリケーションに対して有効にすることができます。 データベースを有効にした場合、データベースはパブリッシュされませんが、そのデータベースの **db_owner** 固定データベース ロール内のすべてのユーザーが 1 つ以上のパブリケーションをデータベース上で作成できるようになります。  
  
## <a name="options"></a>オプション  
 **トランザクション**  
 このチェック ボックスをオンにすると、 **db_owner** 固定データベース ロール内のユーザーは、スナップショット パブリケーションまたはトランザクション パブリケーションをそのデータベースに作成できるようになります。  
  
 **Merge**  
 このチェック ボックスをオンにすると、 **db_owner** 固定データベース ロール内のユーザーは、マージ パブリケーションをそのデータベースに作成できるようになります。  
  
## <a name="see-also"></a>参照  
 [ディストリビューターとパブリッシャーのプロパティの表示および変更](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [プロパティ リファレンス &#40;レプリケーション&#41;](../../relational-databases/replication/properties-reference-replication.md)  
  
  

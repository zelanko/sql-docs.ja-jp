---
title: '[パブリッシャーのプロパティ - パブリッシャー]、[パブリケーション データベース] | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.rep.configdistwizard.pubproperties.pubdb.f1
helpviewer_keywords:
- Publisher Properties dialog box
ms.assetid: 574ea2e7-4e7b-4733-ab52-429ca93c7b0a
caps.latest.revision: 20
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a05c853ff23e0b10434a5e4abc072c950b1cb713
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37276658"
---
# <a name="publisher-properties---publisher-publication-databases"></a>[パブリッシャーのプロパティ - パブリッシャー]、[パブリケーション データベース]
  **[パブリッシャーのプロパティ]** ダイアログ ボックスの **[パブリケーション データベース]** ページを使用すると、 **sysadmin** 固定サーバー ロール内のユーザーはデータベースをレプリケーションに対して有効にすることができます。 データベースを有効にした場合、データベースはパブリッシュされませんが、そのデータベースの **db_owner** 固定データベース ロール内のすべてのユーザーが 1 つ以上のパブリケーションをデータベース上で作成できるようになります。  
  
## <a name="options"></a>および  
 **トランザクション**  
 このチェック ボックスをオンにすると、 **db_owner** 固定データベース ロール内のユーザーは、スナップショット パブリケーションまたはトランザクション パブリケーションをそのデータベースに作成できるようになります。  
  
 **Merge**  
 このチェック ボックスをオンにすると、 **db_owner** 固定データベース ロール内のユーザーは、マージ パブリケーションをそのデータベースに作成できるようになります。  
  
## <a name="see-also"></a>参照  
 [View and Modify Distributor and Publisher Properties (ディストリビューターとパブリッシャーのプロパティの表示および変更)](view-and-modify-distributor-and-publisher-properties.md)   
 [プロパティ リファレンス &#40;レプリケーション&#41;](properties-reference-replication.md)  
  
  

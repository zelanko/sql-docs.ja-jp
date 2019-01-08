---
title: サブスクライバーの種類 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.subscribertypes.f1
ms.assetid: a70656cb-21c9-4489-be77-ccd396747e3b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e34d70b84e20f8c4f65e09baad9d8388aa96fca3
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52806214"
---
# <a name="subscriber-types"></a>サブスクライバーの種類
  マージ レプリケーションを使用すると、パブリケーションがサポートする必要があるサブスクライバーの種類を指定することができます。 サブスクライバーの種類を選択することで、パブリケーションが使用できる機能を決定する *パブリケーションの互換性レベル*が設定されます。  
  
 パブリケーション スナップショットが作成された後は、パブリケーションの互換性レベルは、 **[パブリケーションのプロパティ]** ダイアログ ボックスの **[全般]** ページ上で高く (より制限) することができますが、互換性レベルを低くすることはできません。  
  
## <a name="options"></a>および  
 このパブリケーションでサポートする必要がある各サブスクライバーの種類を選択します。  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
 パブリケーションはすべての機能を使用することができます。  
  
 [!INCLUDE[ssEW](../../includes/ssew-md.md)]  
 パブリケーションは、スナップショット ファイルが文字形式 (これは、スナップショット エージェントによって自動的に処理されます) である必要があります。 [!INCLUDE[ssEW](../../includes/ssew-md.md)] には、互換性レベルとは別の制限事項もあります。  
  
 このオプションが選択されている場合、Web 同期オプションはこのパブリケーションで有効です。 Web 同期の詳細については、「 [Web Synchronization for Merge Replication](web-synchronization-for-merge-replication.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [データとデータベース オブジェクトのパブリッシュ](publish/publish-data-and-database-objects.md)   
 [Create a Publication](publish/create-a-publication.md)   
 [View and Modify Distributor and Publisher Properties (ディストリビューターとパブリッシャーのプロパティの表示および変更)](view-and-modify-distributor-and-publisher-properties.md)   
 [プロパティ リファレンス &#40;レプリケーション&#41;](properties-reference-replication.md)  
  
  

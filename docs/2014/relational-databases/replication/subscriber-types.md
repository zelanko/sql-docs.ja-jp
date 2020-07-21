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
ms.openlocfilehash: ba8a2c83b852abc9d82a84b2d0b2e98f969d0a7b
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85047652"
---
# <a name="subscriber-types"></a>サブスクライバーの種類
  マージ レプリケーションを使用すると、パブリケーションがサポートする必要があるサブスクライバーの種類を指定することができます。 サブスクライバーの種類を選択することで、パブリケーションが使用できる機能を決定する *パブリケーションの互換性レベル*が設定されます。  
  
 パブリケーション スナップショットが作成された後は、パブリケーションの互換性レベルは、 **[パブリケーションのプロパティ]** ダイアログ ボックスの **[全般]** ページ上で高く (より制限) することができますが、互換性レベルを低くすることはできません。  
  
## <a name="options"></a>オプション  
 このパブリケーションでサポートする必要がある各サブスクライバーの種類を選択します。  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
 パブリケーションはすべての機能を使用することができます。  
  
 [!INCLUDE[ssEW](../../includes/ssew-md.md)]  
 パブリケーションは、スナップショット ファイルが文字形式 (これは、スナップショット エージェントによって自動的に処理されます) である必要があります。 [!INCLUDE[ssEW](../../includes/ssew-md.md)] には、互換性レベルとは別の制限事項もあります。  
  
 このオプションが選択されている場合、Web 同期オプションはこのパブリケーションで有効です。 Web 同期の詳細については、「 [Web Synchronization for Merge Replication](web-synchronization-for-merge-replication.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [データとデータベース オブジェクトのパブリッシュ](publish/publish-data-and-database-objects.md)   
 [Create a Publication](publish/create-a-publication.md)   
 [ディストリビューターとパブリッシャーのプロパティの表示および変更](view-and-modify-distributor-and-publisher-properties.md)   

  

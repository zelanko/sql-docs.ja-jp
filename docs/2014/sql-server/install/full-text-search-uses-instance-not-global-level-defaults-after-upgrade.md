---
title: アップグレードすると、フルテキスト検索では、グローバルではなくインスタンスレベルのワードブレーカーとフィルターが既定で使用されるようになります。Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- filters [Full-Text Search]
- word breakers [Full-Text Search]
ms.assetid: 93ee8fcb-d11c-49fa-8fac-51ed31a8f008
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0b6cea7ab63351fad25f0205a614e364328171a9
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85036819"
---
# <a name="upgrading-will-cause-full-text-search-to-use-instance-level-not-global-word-breakers-and-filters-by-default"></a>既定では、アップグレードにより、グローバルではなく、インスタンス レベルのワード ブレーカーおよびフィルターがフルテキスト検索で使用される
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、新しいワード ブレーカーおよびフィルターをインスタンス レベルで登録できる方法が提供されます。  
  
## <a name="component"></a>コンポーネント  
 フルテキスト検索  
  
## <a name="description"></a>説明  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、新しいワード ブレーカーおよびフィルターをインスタンス レベルで登録できます。 このインスタンス レベルの登録により、インスタンス間で機能とセキュリティが分離されます。  
  
## <a name="corrective-action"></a>修正措置  
 アップグレードした後、`sp_fulltext_service` を使用してサービス プロパティと `load_os_resources` を設定します。これにより、コンポーネントを読み込むことができます。 次のコードを実行する必要があります。  
  
 `sp_fulltext_service 'load_os_resources', 1`  
  
## <a name="see-also"></a>参照  
 [アップグレード アドバイザーの使用](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  

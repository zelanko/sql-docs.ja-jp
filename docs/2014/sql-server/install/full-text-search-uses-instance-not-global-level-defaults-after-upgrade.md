---
title: アップグレードにより、既定では、グローバルではなく、インスタンス レベルのワード ブレーカーおよびフィルターを使用するフルテキスト検索 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- filters [Full-Text Search]
- word breakers [Full-Text Search]
ms.assetid: 93ee8fcb-d11c-49fa-8fac-51ed31a8f008
caps.latest.revision: 17
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 45ee5f8235aa79773bf3e92156701e47092c61c9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37311222"
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
  
  

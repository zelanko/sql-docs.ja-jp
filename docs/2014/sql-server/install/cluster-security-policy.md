---
title: クラスターのセキュリティ ポリシー |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- cluster security policy
ms.assetid: 38afa421-2599-404f-8ba6-172668c6325e
caps.latest.revision: 20
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c545910e455d77cf17e944138a6edc902565c656
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36173404"
---
# <a name="cluster-security-policy"></a>クラスターのセキュリティ ポリシー
  フェールオーバー クラスター インスタンスのセキュリティ ポリシーを構成するには、[クラスターのセキュリティ ポリシー] ページを使用します。  
  
## <a name="options"></a>および  
 クラスター化されるサービスのグローバルまたはローカルのドメイン グループを指定します。 すべてのリソースの権限は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス アカウントがグループ メンバーとして含まれる、ドメイン レベルのグループによって制御されます。 [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)]のサービス セキュリティ ID (SID) 機能の詳細については、「 [Windows サービス アカウントと権限の構成](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)」をご覧ください。  
  
  
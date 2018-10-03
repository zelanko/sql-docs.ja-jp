---
title: Master、tempdb、および model データベースでフルテキスト インデックスはサポートされていません |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- full-text indexes
ms.assetid: f7992965-42c1-4eb8-a7fb-afb38b67c740
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f055640dbdbf4ece491b2d8552c1581b122faed3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48064912"
---
# <a name="full-text-indexes-on-master-tempdb-and-model-databases-are-not-supported"></a>master、tempdb、および model データベースに対するフルテキスト インデックスはサポートされない
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、いずれのシステム データベースに対してもフルテキスト インデックスが許可されません。  
  
## <a name="description"></a>説明  
 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] では、フルテキスト インデックスが master、tempdb、および model の各データベースでサポートされていました。  
  
 Master、tempdb、および model データベースでは、すべてのフルテキスト カタログは、アップグレード中に削除されます。  
  
## <a name="see-also"></a>参照  
 [アップグレード アドバイザーの使用](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  

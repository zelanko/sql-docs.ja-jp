---
title: フルテキスト検索のワード ブレーカーおよびフィルターが SQL Server 2005 および SQL Server 2008 で大幅に向上 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
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
ms.assetid: 8d06bda9-0bbf-4baa-b270-07b1c1f640eb
caps.latest.revision: 23
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6a28f0ba9c29be0366b34626fd1c28a7f98c404f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37315572"
---
# <a name="full-text-search-word-breakers-and-filters-significantly-improved-in-sql-server-2005-and-sql-server-2008"></a>SQL Server 2005 および SQL Server 2008 では、フルテキスト検索ワード ブレーカーとフィルターが大幅に機能向上
  ワード ブレーカーとフィルターは大幅に変更されました。 対応言語の拡充や信頼性の向上など、ワード ブレーカーにさらなる改良が加えられています。  
  
## <a name="description"></a>説明  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のフルテキスト検索で使用されるワード ブレーカーとフィルターは、機能性と信頼性を高めるために大幅に変更されています。 ある特定のケースでは、ワード ブレーカーへの変更が、データのトークンを作成する方法に影響を与える可能性があります。 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] で作成されたトークンは、[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] または [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] で作成された以前のトークンとは異なる場合があります。  
  
 ワード ブレーカーの詳細については、次を参照してください。[ワード ブレーカーの管理と検索のステミング機能の構成と](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md)します。  
  
## <a name="see-also"></a>参照  
 [アップグレード アドバイザーの使用](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  

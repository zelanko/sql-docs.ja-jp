---
title: 既定では、SQL Server 用の Microsoft フルテキストエンジンは、署名されていないサードパーティのコンポーネントを読み込みません。Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Full-Text Engine for SQL service
- MSFTESQL service
ms.assetid: 029f9895-7232-4149-9362-3ab1a4133d21
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 12ff188fb6aa6ac286817a7cc1c3ad726483c886
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85012484"
---
# <a name="the-microsoft-full-text-engine-for-sql-server-will-not-load-unsigned-third-party-components-by-default"></a>既定では Microsoft Full-Text Engine for SQL Server は署名のないサード パーティ コンポーネントを読み込まない
  既定では、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Full-Text Engine for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、[!INCLUDE[msCoName](../../includes/msconame-md.md)] によって署名されていないコンポーネントを読み込みません。  
  
## <a name="component"></a>コンポーネント  
 フルテキスト検索  
  
## <a name="description"></a>説明  
 既定では、サーバー上に現在インストールされている PDF フィルターなどのサード パーティのフィルターは、アップグレード後に [!INCLUDE[msCoName](../../includes/msconame-md.md)] Full-Text Engine for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって読み込まれません。  
  
## <a name="corrective-action"></a>修正措置  
 サードパーティのフィルターを読み込むには、 *load_os_resource*を設定し、そのインスタンスの*verify_signature*をオフにする必要があります。  
  
## <a name="see-also"></a>参照  
 [アップグレード アドバイザーの使用](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  

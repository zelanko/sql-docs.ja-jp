---
title: Microsoft Full-text Engine for SQL Server では既定で符号なしのサード パーティのコンポーネントが読み込まれません |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Full-Text Engine for SQL service
- MSFTESQL service
ms.assetid: 029f9895-7232-4149-9362-3ab1a4133d21
caps.latest.revision: 20
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8c66544657e97ed8efcf2ed0dc46dfe21702787a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36084916"
---
# <a name="the-microsoft-full-text-engine-for-sql-server-will-not-load-unsigned-third-party-components-by-default"></a>既定では Microsoft Full-Text Engine for SQL Server は署名のないサード パーティ コンポーネントを読み込まない
  既定では、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Full-Text Engine for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、[!INCLUDE[msCoName](../../includes/msconame-md.md)] によって署名されていないコンポーネントを読み込みません。  
  
## <a name="component"></a>コンポーネント  
 フルテキスト検索  
  
## <a name="description"></a>説明  
 既定では、サーバー上に現在インストールされている PDF フィルターなどのサード パーティのフィルターは、アップグレード後に [!INCLUDE[msCoName](../../includes/msconame-md.md)] Full-Text Engine for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって読み込まれません。  
  
## <a name="corrective-action"></a>修正措置  
 サード パーティのフィルターを読み込むには、設定する必要があります*load_os_resource*をオフにして*verify_signature*そのインスタンスにします。  
  
## <a name="see-also"></a>参照  
 [アップグレード アドバイザーの使用](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
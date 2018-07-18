---
title: access check cache サーバー構成オプション | Microsoft Docs
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
- access check cache option
ms.assetid: 0a992ea8-3ec6-4a4d-97b5-460ae7326247
caps.latest.revision: 8
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 0024a9d0f9999b372ff50d7144a23490529e472e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37287898"
---
# <a name="access-check-cache-server-configuration-options"></a>access check cache サーバー構成オプション
  データベース オブジェクトに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]からアクセスすると、アクセス チェックが **access check result cache**と呼ばれる内部構造にキャッシュされます。 **access check cache quota** オプションと **access check cache bucket count** オプションは、 **access check result cache**に使用されるエントリ数とハッシュ バケット数を制御します。 まれに、これらのオプションを変更することによってパフォーマンスが向上する場合があります。  
  
 既定値は 0 で、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がこれらのオプションを管理していることを示します。 これらのオプションはマイクロソフト カスタマー サポート サービスから指示があった場合にのみ変更することをお勧めします。  
  
## <a name="see-also"></a>参照  
 [サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  

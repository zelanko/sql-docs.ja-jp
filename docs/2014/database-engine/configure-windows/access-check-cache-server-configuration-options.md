---
title: access check cache サーバー構成オプション | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- access check cache option
ms.assetid: 0a992ea8-3ec6-4a4d-97b5-460ae7326247
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8f05e2a9bfd2cacfcbeb6128411f7d10c531600e
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84935978"
---
# <a name="access-check-cache-server-configuration-options"></a>access check cache サーバー構成オプション
  データベース オブジェクトに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]からアクセスすると、アクセス チェックが **access check result cache**と呼ばれる内部構造にキャッシュされます。 **access check cache quota** オプションと **access check cache bucket count** オプションは、 **access check result cache**に使用されるエントリ数とハッシュ バケット数を制御します。 まれに、これらのオプションを変更することによってパフォーマンスが向上する場合があります。  
  
 既定値は 0 で、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がこれらのオプションを管理していることを示します。 これらのオプションはマイクロソフト カスタマー サポート サービスから指示があった場合にのみ変更することをお勧めします。  
  
## <a name="see-also"></a>参照  
 [サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  

---
title: アプリケーション ドメインと CLR 統合のセキュリティ |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- security [CLR integration]
- application domains [CLR integration]
ms.assetid: 54ee904e-e21a-4ee7-b4ad-a6f6f71bd473
caps.latest.revision: 14
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0c97f958126dc7b19478bf0864a23ce4ab4fe07b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36076282"
---
# <a name="application-domains-and-clr-integration-security"></a>アプリケーション ドメインと CLR 統合のセキュリティ
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、同じアプリケーション ドメインの同じ所有者に属するアセンブリを読み込みます。 一連のアセンブリが同じアプリケーション ドメインで実行されるので、.NET Framework リフレクション アプリケーション プログラミング インターフェイスやその他の手段を使用して、実行時にアセンブリを相互に検出することができ、遅延バインディングの形式で呼び出すことができます。 このような呼び出しは同じ所有者に属するアセンブリに対して行われるので、これらの呼び出しに対して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 権限はチェックされません。 アプリケーション ドメインでのアセンブリの配置方法は、主に、スケーラビリティ、セキュリティ、および分離の実現を目標に設計されていますが、この設計は今後のリリースで変更される可能性があります。 したがって、遅延バインディング メカニズムを使用して同じアプリケーション ドメインのアセンブリを検出する方法に依存しないでください。  
  
## <a name="see-also"></a>参照  
 [CLR 統合のセキュリティ](../../relational-databases/clr-integration/security/clr-integration-security.md)  
  
  
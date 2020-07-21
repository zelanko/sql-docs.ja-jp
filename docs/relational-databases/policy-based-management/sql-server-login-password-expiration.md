---
title: SQL Server ログイン パスワードの有効期限 | Microsoft Docs
description: 各 SQL Server ログインのパスワードの有効期限が有効になっているかどうかを確認します。これは、SQL Server に対して発生する可能性のある攻撃に対抗するのに役立ちます。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 7e3bf9da-a436-433d-847a-47c30428cad3
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 50f33195e18af58e782c03118a7e3176f1340cd1
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85774164"
---
# <a name="sql-server-login-password-expiration"></a>SQL Server ログイン パスワードの有効期限
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  このルールでは、各 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインの "パスワードの有効期限" が有効になっているかどうかを確認します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証が有効で、オペレーティング システムが [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)]よりも前のバージョンである場合、攻撃者は既知の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログイン パスワードを繰り返し利用できます。  
  
## <a name="best-practices-recommendations"></a>ベスト プラクティスと推奨事項  
 オペレーティング システムを [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)]にアップグレードすることをお勧めします。  
  
 使用している環境で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証が必要ではない場合は、Windows 認証を使用します。 詳細については、「 [認証モードの選択](../../relational-databases/security/choose-an-authentication-mode.md)」を参照してください。  
  
 すべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインに対して、"パスワードの有効期限" を有効にします。 [ログインのパスワード ポリシーを構成するには、](../../t-sql/statements/alter-login-transact-sql.md) ALTER LOGIN [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を使用します。  
  
## <a name="for-more-information"></a>詳細情報  
 [パスワード ポリシー](../../relational-databases/security/password-policy.md)  
  
## <a name="see-also"></a>参照  
 [ポリシーベースの管理を使用したベスト プラクティスの監視と実行](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  

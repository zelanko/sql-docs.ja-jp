---
title: 休止中の SQL Server 6.5 ログインはアップグレードできません |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- passwords [SQL Server], dormant logins
- dormant logins
- logins [SQL Server], upgrading dormant logins
- identifying dormant logins
- password hashes [SQL Server]
ms.assetid: ebe18a74-0375-4df4-b894-239f8fdabb64
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 03cfdc1e7c639c387e175829f34329344fd9e160
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48227182"
---
# <a name="dormant-sql-server-65-logins-cannot-be-upgraded"></a>休止している SQL Server 6.5 ログインはアップグレードできない
  アップグレード アドバイザーによって、パスワードを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に直接アップグレードできない [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ログインが検出されました。  
  
 このログインを有効にするには、パスワードをリセットする必要があります。 パスワードをリセットするには、ALTER LOGIN を使用します。  
  
```  
ALTER LOGIN <login name> WITH PASSWORD = '<new password>' MUST_CHANGE  
```  
  
 新しいパスワードがシステムのパスワード複雑性ポリシーを満たしているか検証されます。ポリシーのチェックが無効になっている場合は検証が行われません。 複雑なパスワードを使用し、ポリシーのチェックを無効にしないことをお勧めします。 MUST_CHANGE オプションを使用すると、新しいパスワードの選択がユーザーに強制されます。 これは必須ではありませんが、推奨されています。  
  
 次のクエリを使用すると、休止ログインを特定できます。  
  
```  
SELECT * FROM sysxlogins WHERE (xstatus & 2048) = 2048;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [データベース エンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 アップグレード アドバイザー&#91;新規&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  

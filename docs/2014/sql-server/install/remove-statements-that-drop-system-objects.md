---
title: システム オブジェクトを削除するステートメントを削除する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- drop system objects [SQL Server]
ms.assetid: cdfc3c50-c801-4039-a4bf-b35f876f1c61
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 68e5000e924c438a4611e2fa8c134f0dd822f930
ms.sourcegitcommit: 46a2c0ffd0a6d996a3afd19a58d2a8f4b55f93de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/15/2019
ms.locfileid: "59581546"
---
# <a name="remove-statements-that-drop-system-objects"></a>システム オブジェクトを破棄するステートメントを削除する
  アップグレード アドバイザーによって、システム オブジェクトを削除するステートメントが検出されました。 拡張ストアド プロシージャを含む、システム オブジェクトは、読み取り専用でデプロイされる**リソース**データベース (mssqlsystemresource) を削除できません。 システム オブジェクトに対する EXECUTE 権限を禁止または拒否するように、アプリケーションを変更します。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>説明  
 DROP TABLE、DROP PROCEDURE などのステートメントと**sp_dropextendedproc** 、読み取り専用でこれらのオブジェクトが展開されるため、システム オブジェクトを削除するのには使用できません**リソース**データベース。  
  
## <a name="corrective-action"></a>修正措置  
 アプリケーションからシステム オブジェクトの削除を試行するすべてのステートメントを削除します。 システム オブジェクトに対する EXECUTE 権限を禁止または拒否するように、アプリケーションを変更します。 または、セキュリティ構成 (SAC) ツールを使用して、システム オブジェクトの一部を無効にすることもできます。 たとえば、 **xp_cmdshell**拡張ストアド プロシージャを無効にできますか、SAC ツールを使用して有効になっています。  
  
## <a name="see-also"></a>参照  
 [データベース エンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 アップグレード アドバイザー&#91;新規&#93;](sql-server-2014-upgrade-advisor.md)  
  
  

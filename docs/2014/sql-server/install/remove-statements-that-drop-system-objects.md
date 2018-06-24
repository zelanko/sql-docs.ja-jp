---
title: システム オブジェクトを削除するステートメントを削除します |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- drop system objects [SQL Server]
ms.assetid: cdfc3c50-c801-4039-a4bf-b35f876f1c61
caps.latest.revision: 18
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 4c017e6fedbc7fd994e5b2d2ca4de184a082da65
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36072475"
---
# <a name="remove-statements-that-drop-system-objects"></a>システム オブジェクトを破棄するステートメントを削除する
  アップグレード アドバイザーによって、システム オブジェクトを削除するステートメントが検出されました。 拡張ストアド プロシージャなどのシステム オブジェクトは、読み取り専用で配置されて**リソース**データベース (mssqlsystemresource) を削除できません。 システム オブジェクトに対する EXECUTE 権限を禁止または拒否するように、アプリケーションを変更します。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>説明  
 DROP TABLE、DROP PROCEDURE などのステートメントと**sp_dropextendedproc** 、読み取り専用でこれらのオブジェクトが展開されているため、システム オブジェクトを削除するのには使用できません**リソース**データベース。  
  
## <a name="corrective-action"></a>修正措置  
 アプリケーションからシステム オブジェクトの削除を試行するすべてのステートメントを削除します。 システム オブジェクトに対する EXECUTE 権限を禁止または拒否するように、アプリケーションを変更します。 または、セキュリティ構成 (SAC) ツールを使用して、システム オブジェクトの一部を無効にすることもできます。 たとえば、 **xp_cmdshell**拡張ストアド プロシージャを無効にできますまたは SAC ツールを使用して有効にします。  
  
## <a name="see-also"></a>参照  
 [データベース エンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 アップグレード アドバイザー&#91;新規&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  

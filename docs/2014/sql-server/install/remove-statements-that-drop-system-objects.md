---
title: システムオブジェクトを削除するステートメントを削除する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- drop system objects [SQL Server]
ms.assetid: cdfc3c50-c801-4039-a4bf-b35f876f1c61
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d9e8fbfd4a436e87cee413d95468ccf5dd36b9dd
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059183"
---
# <a name="remove-statements-that-drop-system-objects"></a>システム オブジェクトを破棄するステートメントを削除する
  アップグレード アドバイザーによって、システム オブジェクトを削除するステートメントが検出されました。 拡張ストアドプロシージャを含むシステムオブジェクトは、読み取り専用の**リソース**データベース (mssqlsystemresource.mdf) に配置され、削除することはできません。 システム オブジェクトに対する EXECUTE 権限を禁止または拒否するように、アプリケーションを変更します。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>説明  
 DROP TABLE、DROP PROCEDURE、 **sp_dropextendedproc**などのステートメントを使用してシステムオブジェクトを削除することはできません。これらのオブジェクトは読み取り専用の**リソース**データベースに配置されているためです。  
  
## <a name="corrective-action"></a>修正措置  
 アプリケーションからシステム オブジェクトの削除を試行するすべてのステートメントを削除します。 システム オブジェクトに対する EXECUTE 権限を禁止または拒否するように、アプリケーションを変更します。 または、セキュリティ構成 (SAC) ツールを使用して、システム オブジェクトの一部を無効にすることもできます。 たとえば、 **xp_cmdshell**の拡張ストアドプロシージャは、SAC ツールを使用して無効または有効にすることができます。  
  
## <a name="see-also"></a>参照  
 [データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;新しい&#93;](sql-server-2014-upgrade-advisor.md)  
  
  

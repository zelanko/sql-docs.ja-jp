---
title: システムオブジェクトを変更するステートメントを削除する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- direct system catalog updates [SQL Server]
- system catalogs [SQL Server]
ms.assetid: 221b46c2-c27e-4df8-bd8c-8b990d6d5e98
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 526181bc4bf7ab81df2eaa25f19e7627c9b7af10
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059160"
---
# <a name="remove-statements-that-modify-system-objects"></a>システム オブジェクトを変更するステートメントを削除する
  アップグレード アドバイザーによって、システム カタログを更新するステートメントが検出されました。 システム カタログを直接更新できません。 ドキュメントに記載されている公式の API を使用するように SQL スクリプトを変更してください。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>説明  
 システム カタログを直接更新できません。 システム カタログを直接更新しようとすると、次のエラーが生成されます。  
  
 `Server: Msg 259, Level 16, State 1, Line 1`  
  
 `Ad hoc updates to system catalogs are not allowed.`  
  
## <a name="corrective-action"></a>修正措置  
 ドキュメントに記載されている公式の API を使用するように SQL スクリプトを変更してください。 たとえば、 **sysdatabases**システムテーブルで UPDATE ステートメントを実行するのではなく、ALTER database *database_name* SET 緊を使用します。  
  
## <a name="see-also"></a>参照  
 [データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;新しい&#93;](https://docs.microsoft.com/sql/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  

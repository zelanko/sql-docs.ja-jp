---
title: 予約済みキーワードを削除コロン次 |Microsoft ドキュメント
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
- reserved keywords
ms.assetid: 4f23f7e4-7b4d-4e19-86c9-7527bb8b107d
caps.latest.revision: 11
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ae83b0d45ea08a7087bafbd7ee9d1c063e9cf7d9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36073382"
---
# <a name="remove-colon-following-reserved-keyword"></a>予約されたキーワードの後のコロンを削除する
  アップグレード アドバイザーは、予約されたキーワードの後にコロン (:) が含まれたスクリプトを検出しました。 以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、この構文は無視され、ステートメントが正常に実行されます。 現在、データベース互換性モードが 100 以上に設定されていると、この構文が原因でステートメントが失敗します。  
  
 ユーザー データベースでは、互換性モードが維持されます。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>修正措置  
 データベース互換性モードを 100 以上に変更する前に、スクリプト内の予約されたキーワードの後にあるコロンを削除してください。 詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「sp_dbcmptlevel」を参照してください。  
  
## <a name="see-also"></a>参照  
 [データベース エンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 アップグレード アドバイザー&#91;新規&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  

---
title: 固定サーバー ロールの名前と一致するログインの名前を変更する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- user-defined login names [SQL Server]
- fixed server roles [SQL Server]
- renamed logins [SQL Server]
- logins [SQL Server], names
ms.assetid: 10a1d77c-3153-474f-a6a0-969556794467
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c5c46c934dff0e882b50dcf7520ba231ba5187eb
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48181928"
---
# <a name="rename-logins-matching-fixed-server-role-names"></a>固定サーバー ロール名と一致するログイン名を変更する
  アップグレード アドバイザーによって、固定サーバー ロール名と一致する 1 つ以上のユーザー定義ログイン名が検出されました。 固定サーバー ロール名は予約されています。 アップグレードする前に、ログイン名を変更してください。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>説明  
 以下の固定サーバー ロール名は予約されているため、ユーザー定義ログイン名として使用できません。  
  
-   **sysadmin**  
  
-   **serveradmin**  
  
-   **setupadmin**  
  
-   **securityadmin**  
  
-   **processadmin**  
  
-   **dbcreator**  
  
-   **diskadmin**  
  
-   **bulkadmin**  
  
## <a name="corrective-action"></a>修正措置  
 アップグレードする前に、次の操作を行ってください。  
  
1.  次のステートメントを実行することによって、ログインのセキュリティ識別子 (SID) を記録します。  
  
    ```  
    SELECT name, sid   
    FROM master.dbo.syslogins   
    WHERE name IN('sysadmin', 'serveradmin','setupadmin', 'securityadmin','processadmin', 'dbcreator','diskadmin','bulkadmin')  
    ```  
  
2.  ログイン名を削除します。  
  
3.  使用して、 **sp_addlogin**システム プロシージャを新しいログインを作成します。 手順 1. で返された SID を指定、 **@sid**対応するログインごとのパラメーター。  
  
## <a name="see-also"></a>参照  
 [データベース エンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 アップグレード アドバイザー&#91;新規&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  

---
title: 固定サーバー ロールの名前と一致するログインの名前を変更する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
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
ms.openlocfilehash: d983f514f7cc0185021de40f153d78fd6e4dd112
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66092876"
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
 [SQL Server 2014 アップグレード アドバイザー&#91;新規&#93;](sql-server-2014-upgrade-advisor.md)  
  
  

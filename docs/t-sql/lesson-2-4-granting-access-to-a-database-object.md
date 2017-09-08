---
title: "データベース オブジェクトにアクセス権の付与 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- granting access to database objects
ms.assetid: a44d9bbf-f58e-4734-b7f4-eb3b492b777b
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7cc5c15a44f16e4049974ff76095a389348707c7
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="lesson-2-4---granting-access-to-a-database-object"></a>レッスン 2-4-データベースのオブジェクトへのアクセスを許可します。
管理者は **Products** テーブルおよび **vw_Names** ビューから SELECT を実行し、 **pr_Names** プロシージャを実行できますが、ユーザー Mary は実行できません。 Mary に必要な権限を付与するには、GRANT ステートメントを使用します。  
  
### <a name="procedure-title"></a>手順のタイトル  
  
1.  次のステートメントを実行して、 `Mary` ストアド プロシージャの `EXECUTE` 権限を `pr_Names` に与えます。  
  
    ```  
    GRANT EXECUTE ON pr_Names TO Mary;  
    GO  
    ```  
  
このシナリオでは、Mary はストアド プロシージャを使用して **Products** テーブルにのみアクセスできます。 Mary がビューに対して SELECT ステートメントを実行できるようにする場合は、 `GRANT SELECT ON vw_Names TO Mary`も実行する必要があります。 データベース オブジェクトへのアクセス権を削除するには、REVOKE ステートメントを使用します。  
  
> [!NOTE]  
> テーブル、ビュー、およびストアド プロシージャが同じスキーマに所有されていない場合は、権限を付与すると、複雑になります。  
  
## <a name="about-grant"></a>GRANT について  
ストアド プロシージャを実行するには、EXECUTE 権限が必要です。 データにアクセスしたり、データを変更するには、SELECT、INSERT、UPDATE、および DELETE 権限が必要です。 GRANT ステートメントは、テーブルを作成する権限など、他の権限にも使用されます。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
[概要 : データベース オブジェクトに対する権限の構成](../t-sql/lesson-2-5-summary-configuring-permissions-on-database-objects.md)  
  
## <a name="see-also"></a>参照  
[GRANT &#40;Transact-SQL&#41;](../t-sql/statements/grant-transact-sql.md)  
[REVOKE &#40;Transact-SQL&#41;](../t-sql/statements/revoke-transact-sql.md)  
  
  
  


---
title: データベース オブジェクトへのアクセス権の付与 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- granting access to database objects
ms.assetid: a44d9bbf-f58e-4734-b7f4-eb3b492b777b
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 19381b0c5dbe690a60b2c536a8da759205c08c31
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62643446"
---
# <a name="granting-access-to-a-database-object"></a>データベース オブジェクトへのアクセス権の付与
  管理者は、 **Products**テーブルと**VW_NAMES**ビューから SELECT を実行して、 **pr_Names**プロシージャを実行できます。ただし、Mary はできません。 Mary に必要な権限を付与するには、GRANT ステートメントを使用します。  
  
### <a name="procedure-title"></a>手順のタイトル  
  
1.  次のステートメントを実行して、 `Mary` ストアド プロシージャの `EXECUTE` 権限を `pr_Names` に与えます。  
  
    ```  
    GRANT EXECUTE ON pr_Names TO Mary;  
    GO  
    ```  
  
 このシナリオでは、Mary はストアド プロシージャを使用して **Products** テーブルにのみアクセスできます。 Mary がビューに対して SELECT ステートメントを実行できるようにする場合は、 `GRANT SELECT ON vw_Names TO Mary`も実行する必要があります。 データベース オブジェクトへのアクセス権を削除するには、REVOKE ステートメントを使用します。  
  
> [!NOTE]  
>  テーブル、ビュー、およびストアド プロシージャが同じスキーマに所有されていない場合は、権限を付与すると、複雑になります。  
  
## <a name="about-grant"></a>GRANT について  
 ストアド プロシージャを実行するには、EXECUTE 権限が必要です。 データにアクセスしたり、データを変更するには、SELECT、INSERT、UPDATE、および DELETE 権限が必要です。 GRANT ステートメントは、テーブルを作成する権限など、他の権限にも使用されます。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [概要 : データベース オブジェクトに対する権限の構成](lesson-2-5-summary-configuring-permissions-on-database-objects.md)  
  
## <a name="see-also"></a>参照  
 [GRANT &#40;Transact-sql&#41;](/sql/t-sql/statements/grant-transact-sql)   
 [&#40;Transact-sql&#41;を取り消す](/sql/t-sql/statements/revoke-transact-sql)  
  
  

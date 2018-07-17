---
title: データベース オブジェクトへのアクセス権の付与 | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.technology: t-sql
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- SQL Server 2016
helpviewer_keywords:
- granting access to database objects
ms.assetid: a44d9bbf-f58e-4734-b7f4-eb3b492b777b
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: e5641055b11a53bcf39e2eb87ca547553521f9bf
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37427021"
---
# <a name="lesson-2-4---granting-access-to-a-database-object"></a>レッスン 2-4 - データベース オブジェクトへのアクセス権の付与
[!INCLUDE[tsql-appliesto-ss2008-all-md](../includes/tsql-appliesto-ss2008-all-md.md)]
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
  
  
  

---
title: "ミラー化メディア セットへのバックアップ (Transact-SQL) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: backup-restore
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-backup-restore
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5fc43a5d-dfd6-4c53-a4ef-3c8da23ccc81
caps.latest.revision: "7"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4d273a8bb928abfd46e23d28dfdd362f2e8a1441
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="back-up-to-a-mirrored-media-set-transact-sql"></a>ミラー化メディア セットへのバックアップ (Transact-SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] このトピックでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースのバックアップ時に、[!INCLUDE[tsql](../../includes/tsql-md.md)] の [BACKUP](../../t-sql/statements/backup-transact-sql.md) ステートメントを使用して、ミラー化メディア セットを指定する方法を説明します。 BACKUP ステートメントの TO 句で最初のミラーを指定します。 次に、このステートメントの MIRROR TO 句で各ミラーを指定します。 TO 句および MIRROR TO 句では、同じ数と種類のバックアップ デバイスを指定する必要があります。  
  
## <a name="example"></a>例  
 次の例では、上の図のミラー化メディア セットを作成し、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースを両方のミラーにバックアップします。  
  
```  
BACKUP DATABASE AdventureWorks2012  
TO TAPE = '\\.\tape0', TAPE = '\\.\tape1'  
MIRROR TO TAPE = '\\.\tape2', TAPE = '\\.\tape3'  
WITH  
    FORMAT,  
    MEDIANAME = 'AdventureWorks2012Set1';  
GO  
```  
  
## <a name="related-tasks"></a>関連タスク  
 **ミラー化バックアップから復元するには**  
  
-   [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)  
  
## <a name="see-also"></a>参照  
 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)   
 [ミラー化バックアップ メディア セット &#40;SQL Server&#41;](../../relational-databases/backup-restore/mirrored-backup-media-sets-sql-server.md)  
  
  

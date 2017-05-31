---
title: "ミラー化メディア セットへのバックアップ (Transact-SQL) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5fc43a5d-dfd6-4c53-a4ef-3c8da23ccc81
caps.latest.revision: 7
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 5c73a69d7816dee3f9be301995a2522fafb8091c
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="back-up-to-a-mirrored-media-set-transact-sql"></a>ミラー化メディア セットへのバックアップ (Transact-SQL)
  このトピックでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースのバックアップ時に、[!INCLUDE[tsql](../../includes/tsql-md.md)] の [BACKUP](../../t-sql/statements/backup-transact-sql.md) ステートメントを使用して、ミラー化メディア セットを指定する方法を説明します。 BACKUP ステートメントの TO 句で最初のミラーを指定します。 次に、このステートメントの MIRROR TO 句で各ミラーを指定します。 TO 句および MIRROR TO 句では、同じ数と種類のバックアップ デバイスを指定する必要があります。  
  
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
  
  

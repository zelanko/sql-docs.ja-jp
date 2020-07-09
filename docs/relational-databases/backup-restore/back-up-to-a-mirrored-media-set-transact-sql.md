---
title: ミラー化メディア セットへのバックアップ (Transact-SQL) | Microsoft Docs
description: この記事では、SQL Server データベースをバックアップする場合に、Transact-SQL の BACKUP ステートメントを使用して、ミラー化されたメディア セットを指定する方法について説明します。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 5fc43a5d-dfd6-4c53-a4ef-3c8da23ccc81
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: dcaa9ed0516767a590af02bebf521215411a3c4d
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85722495"
---
# <a name="back-up-to-a-mirrored-media-set-transact-sql"></a>ミラー化メディア セットへのバックアップ (Transact-SQL)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  このトピックでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースのバックアップ時に、[!INCLUDE[tsql](../../includes/tsql-md.md)] の [BACKUP](../../t-sql/statements/backup-transact-sql.md) ステートメントを使用して、ミラー化メディア セットを指定する方法を説明します。 BACKUP ステートメントの TO 句で最初のミラーを指定します。 次に、このステートメントの MIRROR TO 句で各ミラーを指定します。 TO 句および MIRROR TO 句では、同じ数と種類のバックアップ デバイスを指定する必要があります。  
  
## <a name="example"></a>例  
 次の例では、上の図のミラー化メディア セットを作成し、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースを両方のミラーにバックアップします。  
  
```sql  
BACKUP DATABASE AdventureWorks2012  
TO TAPE = '\\.\tape0', TAPE = '\\.\tape1'  
MIRROR TO TAPE = '\\.\tape2', TAPE = '\\.\tape3'  
WITH  
    FORMAT,  
    MEDIANAME = 'AdventureWorks2012Set1';  
GO  
```  
  
## <a name="related-tasks"></a>Related Tasks  
 **ミラー化バックアップから復元するには**  
  
-   [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)  
  
## <a name="see-also"></a>参照  
 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)   
 [ミラー化バックアップ メディア セット &#40;SQL Server&#41;](../../relational-databases/backup-restore/mirrored-backup-media-sets-sql-server.md)  
  
  

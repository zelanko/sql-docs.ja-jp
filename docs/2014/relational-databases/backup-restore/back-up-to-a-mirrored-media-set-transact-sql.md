---
title: ミラー化メディア セットへのバックアップ (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 5fc43a5d-dfd6-4c53-a4ef-3c8da23ccc81
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 255a3c190139c029f5211dcab9780b6d07d975a4
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84959492"
---
# <a name="back-up-to-a-mirrored-media-set-transact-sql"></a>ミラー化メディア セットへのバックアップ (Transact-SQL)
  このトピックでは、BACKUP ステートメントを使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)] [BACKUP](/sql/t-sql/statements/backup-transact-sql)データベースのバックアップ時にミラー化メディアセットを指定する方法について説明し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。 BACKUP ステートメントの TO 句で最初のミラーを指定します。 次に、このステートメントの MIRROR TO 句で各ミラーを指定します。 TO 句および MIRROR TO 句では、同じ数と種類のバックアップ デバイスを指定する必要があります。  
  
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
  
## <a name="related-tasks"></a>Related Tasks  
 **ミラー化バックアップから復元するには**  
  
-   [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)  
  
## <a name="see-also"></a>参照  
 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)   
 [ミラー化バックアップ メディア セット &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md)  
  
  

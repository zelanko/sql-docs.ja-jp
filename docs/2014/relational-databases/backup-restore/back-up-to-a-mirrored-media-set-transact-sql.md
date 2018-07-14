---
title: ミラー化メディア セットへのバックアップ (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: backup-restore
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 5fc43a5d-dfd6-4c53-a4ef-3c8da23ccc81
caps.latest.revision: 4
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: b423352337f224c0f3a920e08040f686fd4d49fb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37201522"
---
# <a name="back-up-to-a-mirrored-media-set-transact-sql"></a>ミラー化メディア セットへのバックアップ (Transact-SQL)
  このトピックでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースのバックアップ時に、[!INCLUDE[tsql](../../includes/tsql-md.md)] の [BACKUP](/sql/t-sql/statements/backup-transact-sql) ステートメントを使用して、ミラー化メディア セットを指定する方法を説明します。 BACKUP ステートメントの TO 句で最初のミラーを指定します。 次に、このステートメントの MIRROR TO 句で各ミラーを指定します。 TO 句および MIRROR TO 句では、同じ数と種類のバックアップ デバイスを指定する必要があります。  
  
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
  
  

---
title: TRUSTWORTHY プロパティを使用するようにミラー データベースを設定する方法 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- TRUSTWORTHY database option
- mirror database [SQL Server]
- database mirroring [SQL Server], security
ms.assetid: 6993b076-78ef-453e-b0ea-e341b8e5ee3e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 29cafc7e9669ca322571ff171961dd64cab114cf
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62754335"
---
# <a name="set-up-a-mirror-database-to-use-the-trustworthy-property-transact-sql"></a>TRUSTWORTHY プロパティを使用するようにミラー データベースを設定する方法 (Transact-SQL)
  データベースをバックアップするときに、TRUSTWORTHY データベース プロパティは OFF に設定されます。 したがって、新しいミラー データベースでは TRUSTWORTHY は常に OFF です。 フェールオーバー後にデータベースを信頼可能にする必要がある場合は、ミラーリングを開始した後で追加の設定が必要です。  
  
> [!NOTE]  
>  このデータベース プロパティの詳細については、「 [TRUSTWORTHY データベース プロパティ](../../relational-databases/security/trustworthy-database-property.md)」を参照してください。  
  
## <a name="procedure"></a>手順  
  
#### <a name="to-setup-a-mirror-database-to-use-the-trustworthy-property"></a>TRUSTWORTHY プロパティを使用するようにミラー データベースを設定するには  
  
1.  プリンシパル サーバー インスタンスで、プリンシパル データベースの TRUSTWORTHY プロパティがオンになっていることを確認します。  
  
    ```  
    SELECT name, database_id, is_trustworthy_on FROM sys.databases   
    ```  
  
     詳細については、「[sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)」を参照してください。  
  
2.  ミラーリングが開始された後、データベースが現在プリンシパル データベースであること、セッションが同期動作モードを使用していること、およびセッションが既に同期していることを確認します。  
  
    ```  
    SELECT database_id, mirroring_role, mirroring_safety_level_desc, mirroring_state_desc FROM sys.database_mirroring  
    ```  
  
     詳細については、「[sys.database_mirroring &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-transact-sql)」を参照してください。  
  
3.  ミラーリング セッションが同期されたら、ミラー データベースに手動でフェールオーバーします。  
  
     この操作を行うには、SQL Server Management Studio または Transact-SQL を使用します。  
  
    -   [データベースミラーリングセッションを手動でフェールオーバーする &#40;SQL Server Management Studio&#41;](manually-fail-over-a-database-mirroring-session-sql-server-management-studio.md)  
  
    -   [Transact-sql&#41;&#40;データベースミラーリングセッションを手動でフェールオーバーする](manually-fail-over-a-database-mirroring-session-transact-sql.md)  
  
4.  次の ALTER DATABASE コマンドを使用して、TRUSTWORTHY データベース プロパティをオンにします。  
  
    ```  
    ALTER DATABASE <database_name> SET TRUSTWORTHY ON  
    ```  
  
     詳細については、「[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)」を参照してください。  
  
5.  必要に応じて、手動で再度フェールオーバーし、元のプリンシパルに戻します。  
  
6.  必要に応じて、SAFETY を OFF に設定し、WITNESS も OFF に設定されていることを確認して、非同期の高パフォーマンス モードに切り替えます。  
  
     Transact-SQL での操作  
  
    -   [データベースミラーリングセッションでのトランザクションの安全性の変更 Transact-sql&#41;の &#40;](change-transaction-safety-in-a-database-mirroring-session-transact-sql.md)  
  
    -   [データベースミラーリングセッションからミラーリング監視サーバーを削除 &#40;SQL Server&#41;](remove-the-witness-from-a-database-mirroring-session-sql-server.md)  
  
     SQL Server Management Studio での操作  
  
    -   [Windows 認証 &#40;SQL Server Management Studio を使用してデータベースミラーリングセッションを確立&#41;](establish-database-mirroring-session-windows-authentication.md)  
  
## <a name="see-also"></a>参照  
 [信頼可能データベースのプロパティ](../../relational-databases/security/trustworthy-database-property.md)   
 [暗号化されたミラー データベースの設定](set-up-an-encrypted-mirror-database.md)  
  
  

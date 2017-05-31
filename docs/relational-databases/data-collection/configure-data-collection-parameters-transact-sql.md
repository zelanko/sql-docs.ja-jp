---
title: "データ コレクションのパラメーターの構成 (Transact-SQL) | Microsoft Docs"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data collection [SQL Server]
ms.assetid: 850905b6-35d2-4ed1-ab51-de64daa832b2
caps.latest.revision: 16
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 26de604b9af6c7640e8289f9a702948d348b83e5
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="configure-data-collection-parameters-transact-sql"></a>データ コレクションのパラメーターの構成 (Transact-SQL)
  カスタム コレクション セットを作成する前に、データ コレクションのパラメーターを構成しておく必要があります。 これには、データ コレクターで用意されているストアド プロシージャを使用します。 この作業には、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のクエリ エディターを使用した次の手順の実行も含まれます。  
  
> [!NOTE]  
>  データ コレクションのパラメーターは一度構成するだけです。 構成後に作成した追加のコレクション セットには、すべてこれらのパラメーターが使用されます。  
  
### <a name="configure-data-collection-parameters"></a>データ コレクションのパラメーターの構成  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、カスタム コレクション セットを作成するデータベースに接続します。  
  
2.  クエリ エディターで、次のステートメントを実行します。  
  
    ```tsql  
    USE msdb;  
    EXEC sp_syscollector_set_warehouse_instance_name N'INSTANCE_NAME';-- where instance name is the name of the SQL Server instance  
    EXEC sp_syscollector_set_warehouse_database_name N'MDW';  
    EXEC sp_syscollector_set_cache_directory N'D:\tempdata';  
    ```  
  
## <a name="see-also"></a>参照  
 [データ コレクション](../../relational-databases/data-collection/data-collection.md)   
 [データ コレクター ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)  
  
  

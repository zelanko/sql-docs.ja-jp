---
title: 同じ SQL インスタンスでユーティリティとユーティリティ以外のコレクション セットを実行する | Microsoft Docs
description: ユーティリティとユーティリティ以外のコレクション セットを並行して使用して SQL Server のインスタンスを監視する方法について説明します。 構成要件を表示します。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: ca7ee9b3-ef9a-4ba4-83d0-9ee9f80dab27
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 522b21e2a2c7e78c8ca16483fc02f2564e0ebaf5
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85773470"
---
# <a name="run-utility-and-non-utility-collection-sets-on-same-sql-instance"></a>同じ SQL インスタンスでユーティリティとユーティリティ以外のコレクション セットを実行する
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティ コレクション セットは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティ以外のコレクション セットとサイド バイ サイドで実行できます。 つまり、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のマネージド インスタンスは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティのメンバーであれば、他のコレクション セットによって監視できます。 ただし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティ以外のデータ収集機能は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティに登録されている場合は無効にする必要があります。  
  
 インスタンスが UCP に登録されたら、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティ以外のコレクション セットを再開できます。 ただし、マネージド インスタンス上のすべてのコレクション セットは、そのデータをユーティリティ管理データ ウェアハウス (UMDW) にアップロードすることに注意してください。UMDW ファイル名は sysutility_mdw です。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティ コレクション セットを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティ以外のコレクション セットとサイド バイ サイドで実行する場合は、次の点を考慮してください。  
  
-   コレクション セットはサイド バイ サイドで実行できます。  
  
-   インスタンスを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティに登録している間は、既存のデータ コレクターを無効にする必要があります。  
  
-   検証要件を満たすには、次のストアド プロシージャを、UCP を作成する前に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティに登録する前に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスで実行する必要があります。  
  
    ```  
    exec msdb.dbo.sp_syscollector_set_warehouse_database_name NULL  
    exec msdb.dbo.sp_syscollector_set_warehouse_instance_name NULL  
    ```  
  
     UCP の作成ウィザードまたはマネージド インスタンスの追加ウィザードを起動する前にこれらのストアド プロシージャを実行しないと、操作は失敗します。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティの UMDW (sysutility_mdw) は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のマネージド インスタンス上のすべてのコレクション セットに対して使用する必要があります。  
  
## <a name="see-also"></a>参照  
 [SQL Server ユーティリティの機能とタスク](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)   
 [ユーティリティ コントロール ポイント データ ウェアハウスの構成 &#40;SQL Server Utility&#41;](../../relational-databases/manage/configure-your-utility-control-point-data-warehouse-sql-server-utility.md)  
  
  

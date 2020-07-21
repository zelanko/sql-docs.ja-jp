---
title: マネージド SQL Server でユーティリティ コレクションのプロキシ アカウントを変更する | Microsoft Docs
description: SQL Server Management Studio を使用して、SQL Server のマネージド インスタンスでユーティリティ コレクション セットのプロキシ アカウントを変更する方法について説明します。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: ff37ba8b-a08c-4109-b6e2-5748c995a52c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 052f0e6c1e60c5753f879e325c7cfa0603ba4303
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85776047"
---
# <a name="change-proxy-account-for-utility-collection-on--managed-sql-server"></a>マネージド SQL Server でユーティリティ コレクションのプロキシ アカウントを変更する
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  このトピックでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のマネージド インスタンスでユーティリティ コレクション セットのプロキシ アカウントを変更する方法について説明します。  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-change-the-proxy-account-for-the-utility-collection-set-on-a-managed-instance-of-sql-server"></a>SQL Server のマネージド インスタンスにおけるユーティリティ コレクション セットのプロキシ アカウントを変更するには  
  
1.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のマネージド インスタンスを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティから削除します。  
  
    -   SSMS の **ユーティリティ エクスプローラー** で **[マネージド インスタンス]** ノードをクリックします。  
  
    -   **ユーティリティ エクスプローラー** のリスト ビューで、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの名前を右クリックし、 **[マネージド インスタンスの削除]** をクリックします。詳細については、「 [SQL Server ユーティリティからの SQL Server のインスタンスの削除](../../relational-databases/manage/remove-an-instance-of-sql-server-from-the-sql-server-utility.md)」を参照してください。  
  
2.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティに再度登録します。  

    -   SSMS の**ユーティリティ エクスプローラー**で、 **[マネージド インスタンス]** ノードを右クリックし、 **[マネージド インスタンスの追加]** をクリックします。  
  
    -   新しいプロキシ アカウントを指定して、画面の指示に従ってウィザードを完了します。  
  
## <a name="see-also"></a>参照  
 [SQL Server ユーティリティの機能とタスク](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)   
 [SQL Server ユーティリティのトラブルシューティング](https://msdn.microsoft.com/library/f5f47c2a-38ea-40f8-9767-9bc138d14453)  
  
  

---
title: マネージ SQL Server でユーティリティ コレクションのプロキシ アカウントを変更する | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: maintenance-plans
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff37ba8b-a08c-4109-b6e2-5748c995a52c
caps.latest.revision: 8
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c1bf9c697415f214f9164a503126a3174de40154
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="change-proxy-account-for-utility-collection-on--managed-sql-server"></a>マネージ SQL Server でユーティリティ コレクションのプロキシ アカウントを変更する
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]のマネージ インスタンスでユーティリティ コレクション セットのプロキシ アカウントを変更する方法について説明します。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-change-the-proxy-account-for-the-utility-collection-set-on-a-managed-instance-of-sql-server"></a>SQL Server のマネージ インスタンスにおけるユーティリティ コレクション セットのプロキシ アカウントを変更するには  
  
1.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のマネージ インスタンスを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティから削除します。  
  
    -   SSMS の **ユーティリティ エクスプローラー** で **[マネージ インスタンス]** ノードをクリックします。  
  
    -   **ユーティリティ エクスプローラー** のリスト ビューで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの名前を右クリックし、 **[マネージ インスタンスの削除]**をクリックします。 詳細については、「 [SQL Server ユーティリティからの SQL Server のインスタンスの削除](../../relational-databases/manage/remove-an-instance-of-sql-server-from-the-sql-server-utility.md)」を参照してください。  
  
2.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティに再度登録します。  
  
    -   SSMS の **ユーティリティ エクスプローラー** で、 **[マネージ インスタンス]** ノードを右クリックし、 **[マネージ インスタンスの追加]**をクリックします。  
  
    -   新しいプロキシ アカウントを指定して、画面の指示に従ってウィザードを完了します。  
  
## <a name="see-also"></a>参照  
 [SQL Server ユーティリティの機能とタスク](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)   
 [SQL Server ユーティリティのトラブルシューティング](http://msdn.microsoft.com/library/f5f47c2a-38ea-40f8-9767-9bc138d14453)  
  
  

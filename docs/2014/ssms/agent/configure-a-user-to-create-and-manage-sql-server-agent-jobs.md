---
title: SQL Server エージェント ジョブ ステップを作成および管理するユーザーの構成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, user configuration
- jobs [SQL Server Agent], user configuration
- SQLAgentUserRole database role
- proxy accounts [SQL Server Agent]
ms.assetid: 67897e3e-b7d0-43dd-a2e2-2840ec4dd1ef
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a62f6c2e1ef86a6fcd5e532b2ef413d8142698e6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63253559"
---
# <a name="configure-a-user-to-create-and-manage-sql-server-agent-jobs"></a>Configure a User to Create and Manage SQL Server Agent Jobs
  このトピックでは、エージェントジョブを作成または実行[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]するユーザーを構成する方法について説明します。  
  
-   **作業を開始する準備:**  [セキュリティ](#Security)  
  
-   **SQL Server エージェントジョブを作成および管理するユーザーを構成するために使用するもの:**  [SQL Server Management Studio](#SSMS)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Security"></a> セキュリティ  
 エージェントジョブを作成または実行[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]するユーザーを構成するには、msdb データベースの SQLAgentUserRole、SQLAgentReaderRole、または sqlagentoperatorrole のいずれかの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント固定データベースロールに、既存の SQL Server ログインまたは msdb ロールを追加する必要があります。  
  
 既定では、これらのデータベース ロールのメンバーは、メンバー自身が実行する独自のジョブ ステップを作成できます。 このような管理者権限のないユーザーが他の種類のジョブ ステップ ( [!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージなど) を実行するには、プロキシ アカウントへのアクセスが必要です。 sysadmin 固定サーバー ロールのすべてのメンバーには、プロキシ アカウントを作成、変更、および削除する権限があります。 これら [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント固定のデータベース ロールに関連付けられている権限の詳細については、「 [SQL Server エージェントの固定データベース ロール](sql-server-agent-fixed-database-roles.md)」を参照してください。  
  
####  <a name="Permissions"></a> Permissions  
 詳細については、「 [SQL Server エージェントのセキュリティの実装](implement-sql-server-agent-security.md)」をご覧ください。  
  
##  <a name="SSMS"></a> SQL Server Management Studio の使用  
 **SQL Server エージェント固定データベースロールに SQL ログインまたは msdb ロールを追加するには**  
  
1.  
  **オブジェクト エクスプローラー**で、サーバーを展開します。  
  
2.  
  **[セキュリティ]** を展開し、 **[ログイン]** を展開します。  
  
3.  
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント固定データベース ロールに追加するログインを右クリックし、 **[プロパティ]** をクリックします。  
  
4.  [**ログインのプロパティ**] ダイアログボックスの [**ユーザーマッピング**] ページで、を`msdb`含む行を選択します。  
  
5.  
  **[データベース ロールのメンバーシップ: msdb]** で、該当する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント固定データベース ロールのチェック ボックスをオンにします。  
  
 **SQL Server エージェントジョブステップを作成および管理するようにプロキシアカウントを構成するには**  
  
1.  
  **オブジェクト エクスプローラー**で、サーバーを展開します。  
  
2.  
  **[SQL Server エージェント]** を展開します。  
  
3.  
  **[プロキシ]** を右クリックして **[新しいプロキシ]** をクリックします。  
  
4.  
  **[新しいプロキシ アカウント]** ダイアログの **[全般]** ページで、新しいプロキシのプロキシ名、資格情報名、および説明を指定します。 SQL Server エージェントのプロキシを作成する前に、まず資格情報を作成する必要があることに注意してください。 資格情報の作成の詳細については、「 [create a credential](../../relational-databases/security/authentication-access/create-a-credential.md) 」と「 [Create credential &#40;transact-sql&#41;](/sql/t-sql/statements/create-credential-transact-sql)」を参照してください。  
  
5.  このプロキシに適したサブシステムを確認します。  
  
6.  
  **[プリンシパル]** ページで、プロキシ アカウントへのアクセスを許可するログインまたはロールを追加するか、あるいは拒否するログインまたはロールを削除します。  
  
## <a name="see-also"></a>参照  
 [SQL Server エージェントのセキュリティの実装](implement-sql-server-agent-security.md)  
  
  

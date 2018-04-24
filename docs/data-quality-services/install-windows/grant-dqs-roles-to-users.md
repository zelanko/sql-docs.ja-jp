---
title: ユーザーに DQS ロールを付与する | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: data-quality-services
ms.service: ''
ms.component: install-windows
ms.reviewer: ''
ms.suite: sql
ms.technology:
- data-quality-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: afb445b5-bdbe-4bfe-844f-344766cdc2b2
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2a9bc901465e2b329cf1491e84e8f3dd87f66923
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="grant-dqs-roles-to-users"></a>ユーザーに DQS ロールを付与する

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  このトピックでは、Windows プリンシパルに基づいて SQL ログインを作成し、DQS_MAIN データベースで [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS) ロールを付与する方法を説明します。  
  
## <a name="prerequisites"></a>Prerequisites  
  
-   DQSInstaller.exe ファイルを実行して [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] のインストールを完了しておく必要があります。 詳細については、「 [Data Quality Server のインストールを完了するための DQSInstaller.exe の実行](../../data-quality-services/install-windows/run-dqsinstaller-exe-to-complete-data-quality-server-installation.md)」を参照してください。  
  
-   SQL ログインを作成し、DQS ロールを付与するには、Windows ユーザー アカウントが適切な固定サーバー ロール (securityadmin、serveradmin、sysadmin など) のメンバーであることが必要です。  
  
### <a name="to-create-sql-login-and-grant-dqs-roles"></a>SQL ログインを作成し、DQS ロールを付与するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を起動します。  
  
2.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、SQL Server インスタンスを展開し、 **[セキュリティ]** を展開します。  
  
3.  **[セキュリティ]** フォルダーを右クリックし、 **[新規作成]** をポイントして、 **[ログイン]** をクリックします。  
  
4.  **[ログイン - 新規作成]** ダイアログ ボックスの **[ログイン名]** ボックスで Windows ユーザーの名前を指定し、認証の種類として **[Windows 認証]** を指定し、 **[検索]** をクリックしてユーザーを検証します。  
  
5.  ユーザーの検証後、左ペインの **[ユーザー マッピング]** ページをクリックします。  
  
6.  右ペインで、 **[DQS_MAIN]** データベースの **[マップ]** 列のチェック ボックスをオンにし、ユーザーに必要なアクセス レベルに応じて、 **[DQS_MAIN のデータベース ロール メンバーシップ]** ペインで **[dqs_administrator]**、 **[dqs_kb_editor]** 、または **[dqs_kb_operator]** チェック ボックスをオンにします。 3 つの DQS ロールの詳細については、「 [DQS Security](../../data-quality-services/dqs-security.md)」を参照してください。  
  
7.  **[ログイン - 新規作成]** ダイアログ ボックスで、 **[OK]** をクリックして変更を適用します。  
  
    > [!NOTE]  
    >  **dqs_administrator** ロールをユーザーに付与し、変更を適用してから、ユーザー権限を再びオンにすると、その他の 2 つの DQS ロールのチェック ボックス (**[dq_kb_editor]** および **[dqs_kb_operator]**) もオンになります。  
  
## <a name="next-steps"></a>Next Steps  
 先ほど SQL ログインを作成し、DQS ロールを付与した Windows ユーザー アカウントを使用して [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] へのログオンを試みます。  
  
## <a name="see-also"></a>参照  
 [Data Quality Services のインストール](../../data-quality-services/install-windows/install-data-quality-services.md)   
 [ログインの作成](../../relational-databases/security/authentication-access/create-a-login.md)  
  
  

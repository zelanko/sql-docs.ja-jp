---
title: ポリシー ベースの管理の全般プロパティの構成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.dmf.PolicyManagement.f1
helpviewer_keywords:
- Policy-Based Management, configure properties
ms.assetid: 6d1e0e37-29ea-408a-a055-384984d884be
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 249b338148dc762e091d0be47bc081fe87c72fcd
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "63162395"
---
# <a name="configure-the-general-properties-of-policy-based-management"></a>ポリシー ベースの管理の全般プロパティの構成
  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]でポリシー ベースの管理のプロパティを構成する方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [セキュリティ](#Security)  
  
-   **ポリシー ベースの管理を構成するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="security"></a><a name="Security"></a> セキュリティ  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 PolicyAdministratorRole 固定データベース ロールのメンバーシップが必要です。  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-configure-policy-based-management"></a>ポリシー ベースの管理を構成するには  
  
1.  **オブジェクト エクスプローラー**で、プラス記号をクリックして、ポリシー ベースの管理のプロパティを構成するサーバーを展開します。  
  
2.  プラス記号をクリックして **[管理]** フォルダーを展開します。  
  
3.  **[ポリシー管理]** を右クリックし、 **[プロパティ]** をクリックします。  
  
     **[ポリシー管理のプロパティ]** ダイアログ ボックスでは、次のオプションを使用できます。  
  
     **Enabled**  
     ポリシー ベースの管理を有効にするかどうかを指定します。  
  
     **HistoryRetentionInDays**  
     ポリシー評価履歴を保持する日数を指定します。 この値が 0 (既定値) の場合、履歴は自動的には削除されません。  
  
     **LogOnSuccess**  
     ポリシー ベースの管理のログに成功したポリシー評価を記録するかどうかを指定します。  
  
    -   この値が false (既定値) の場合、失敗したポリシー評価だけが記録されます。  
  
    -   この値が true の場合、成功したポリシー評価と失敗したポリシー評価の両方が記録されます。  
  
4.  完了したら、[**OK**] をクリックします。  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-configure-policy-based-management"></a>ポリシー ベースの管理を構成するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。  
  
    ```  
    -- enables Policy-Based Management   
    USE msdb;  
    GO  
    EXEC dbo.sp_syspolicy_configure   
         @name = N'Enabled',   
         @value = 1;  
    GO  
    ```  
  
 詳細については、「[sp_syspolicy_configure &#40;Transact SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syspolicy-configure-transact-sql)」を参照してください。  
  
  

---
title: "ポリシー ベースの管理ポリシーのプロパティの表示または変更 | Microsoft Docs"
ms.custom: 
ms.date: 10/06/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Policy-Based Management, modify policies
- Policy-Based Management, view policies
ms.assetid: ba805504-5db5-4731-a8da-a0e89cb20c37
caps.latest.revision: "9"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: bd1b7cd56c3db5bd65ace16d9002ad468c455683
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="view-or-modify-the-properties-of-a-policy-based-management-policy"></a>ポリシー ベースの管理ポリシーのプロパティの表示または変更
  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]でポリシー ベースの管理ポリシーのプロパティを表示または変更する方法について説明します。  
  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
  
####  <a name="Permissions"></a> Permissions  
 msdb データベースの PolicyAdministratorRole ロールのメンバーシップが必要です。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-view-the-properties-of-all-policies-on-an-object"></a>オブジェクトのすべてのポリシーのプロパティを表示するには  
  
1.  オブジェクト エクスプローラーで、サーバー、サーバー オブジェクト、データベース、またはデータベース オブジェクトを右クリックして、 **[ポリシー]** をポイントし、 **[表示]**をクリックします。 **[ポリシーの表示 -***object_name]* ダイアログ ボックスで使用可能なオプションの詳細については、「 [[ポリシーの表示] ダイアログ ボックス](../../relational-databases/policy-based-management/view-policies-dialog-box.md)」を参照してください。  
  
2.  完了したら、 **[閉じる]**をクリックします。  
  
#### <a name="to-view-or-modify-a-specific-policys-properties"></a>特定のポリシーのプロパティを表示または変更するには:  
  
1.  **オブジェクト エクスプローラー**で、表示または変更するポリシー ベースの管理ポリシーを含むサーバーをプラス記号をクリックして展開します。  
  
2.  プラス記号をクリックして **[管理]** フォルダーを展開します。  
  
3.  プラス記号をクリックして **[ポリシー管理]**を展開します。  
  
4.  プラス記号をクリックして **[ポリシー]** フォルダーを展開します。  
  
5.  表示または変更するポリシーを右クリックし、 **[プロパティ]**をクリックします。 **[ポリシーを開く -***policy_name]* ダイアログ ボックスで使用可能なオプションの詳細については、「 [[新しいポリシーの作成] または [ポリシーを開く] ダイアログ ボックスの [全般] ページ](../../relational-databases/policy-based-management/create-new-policy-or-open-policy-dialog-box-general-page.md) 」および「 [[新しいポリシーの作成] または [ポリシーを開く] ダイアログ ボックスの [説明] ページ](../../relational-databases/policy-based-management/create-new-policy-or-open-policy-dialog-box-description-page.md)」を参照してください。  
  
6.  完了したら、 **[OK]**をクリックします。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-view-a-policys-properties"></a>ポリシーのプロパティを表示するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。  
  
    ```  
    USE msdb;  
    GO  
    SELECT name,  
       execution_mode,  
       description,  
       is_enabled,  
       job_id  
    FROM syspolicy_policies;  
    GO  
    ```  
  
 詳細については、「[syspolicy_policies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/syspolicy-policies-transact-sql.md)」を参照してください。  
  
  

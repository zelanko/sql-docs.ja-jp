---
title: "メンバー権限を直ちに適用する (マスター データ サービス) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "メンバー [マスター データ サービス], 権限を直ちに適用する"
  - "権限 [マスター データ サービス], メンバー権限を直ちに適用する"
ms.assetid: 5b16de66-5c39-49f5-992f-402a9eb319aa
caps.latest.revision: 6
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 6
---
# メンバー権限を直ちに適用する (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] で、メンバー セキュリティが定期的に適用されるのを待つ代わりに、メンバー権限を直ちに適用できます。  
  
## 前提条件  
 この手順を実行するには  
  
-   [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースで mdm.udpSecurityMemberProcessRebuildModel ストアド プロシージャを実行するための権限が必要です。 詳細については、「[データベース オブジェクト セキュリティ (マスター データ サービス)](../master-data-services/database-object-security-master-data-services.md)」を参照してください。  
  
### 階層メンバーの権限を直ちに適用するには  
  
1.  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を開き、[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースの [!INCLUDE[ssDE](../includes/ssde-md.md)] インスタンスに接続します。  
  
2.  新しいクエリを作成します。  
  
3.  次のテキストを入力します。その場合、*database* をデータベースの名前で置き換え、*Model_Name* をモデルの名前で置き換えます。  
  
    ```  
    USE [database];  
    GO  
  
    DECLARE @Model_ID INT;  
    SELECT @Model_ID = ID FROM mdm.tblModel WHERE [Name] = N'Model_Name';  
    EXEC [mdm].[udpSecurityMemberProcessRebuildModel] @Model_ID=@Model_ID, @ProcessNow=1;  
    GO  
    ```  
  
4.  クエリを実行します。  
  
## 参照  
 [階層メンバーの権限を割り当てる (マスター データ サービス)](../master-data-services/assign-hierarchy-member-permissions-master-data-services.md)   
 [階層メンバーの権限 (マスター データ サービス)](../master-data-services/hierarchy-member-permissions-master-data-services.md)  
  
  
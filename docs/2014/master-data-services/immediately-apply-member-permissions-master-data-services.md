---
title: メンバー アクセス許可を直ちに適用する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- members [Master Data Services], applying permissions immediately
- permissions [Master Data Services], applying member permissions immediately
ms.assetid: 5b16de66-5c39-49f5-992f-402a9eb319aa
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 88c574e713862699e72a0f596371c64f9f6a11cd
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62765155"
---
# <a name="immediately-apply-member-permissions-master-data-services"></a>メンバー権限を直ちに適用する (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で、メンバー セキュリティが定期的に適用されるのを待つ代わりに、メンバー権限を直ちに適用できます。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 この手順を実行するには  
  
-   [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースで mdm.udpSecurityMemberProcessRebuildModel ストアド プロシージャを実行するための権限が必要です。 詳細については、「[データベース オブジェクト セキュリティ (マスター データ サービス)](database-object-security-master-data-services.md)」を参照してください。  
  
### <a name="to-immediately-apply-hierarchy-member-permissions"></a>階層メンバーの権限を直ちに適用するには  
  
1.  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を開き、 [!INCLUDE[ssDE](../includes/ssde-md.md)] データベースの [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] インスタンスに接続します。  
  
2.  新しいクエリを作成します。  
  
3.  次のテキストを入力します。その場合、 *database* をデータベースの名前で置き換え、 *Model_Name* をモデルの名前で置き換えます。  
  
    ```  
    USE [database];  
    GO  
  
    DECLARE @Model_ID INT;  
    SELECT @Model_ID = ID FROM mdm.tblModel WHERE [Name] = N'Model_Name';  
    EXEC [mdm].[udpSecurityMemberProcessRebuildModel] @Model_ID=@Model_ID, @ProcessNow=1;  
    GO  
    ```  
  
4.  クエリを実行します。  
  
## <a name="see-also"></a>関連項目  
 [階層メンバーの権限を割り当てる (マスター データ サービス)](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md)   
 [階層メンバーの権限 (マスター データ サービス)](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md)  
  
  

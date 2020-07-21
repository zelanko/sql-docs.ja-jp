---
title: システム管理者アカウントを変更する (マスターデータサービス) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- administrators [Master Data Services], changing
ms.assetid: cf30312e-4338-49a7-90f0-6e4f7b431ff8
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 6266664bc4e1d1c782ce75a9de4edebe52d11f0c
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84972032"
---
# <a name="change-the-system-administrator-account-master-data-services"></a>システム管理者アカウントの変更 (マスター データ サービス)
  システム管理者として指定されているユーザーアカウントを変更することができ [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] ます。  
  
> [!WARNING]  
>  この手順が完了すると、前のシステム管理者のユーザー アカウントは削除されます。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   新しい管理者のユーザー名を[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]のユーザーの一覧に追加する必要があります。 詳細については、「 [Add a User &#40;マスターデータサービス&#41;](add-a-user-master-data-services.md)」を参照してください。  
  
-   [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースで mdm.tblUser を表示して mdm.udpSecurityMemberProcessRebuildModel ストアド プロシージャを実行するための権限が必要です。 詳細については、「[データベース オブジェクト セキュリティ (マスター データ サービス)](../../2014/master-data-services/database-object-security-master-data-services.md)」を参照してください。  
  
### <a name="to-change-the-administrator-account"></a>管理者アカウントを変更するには  
  
1.  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を開き、 [!INCLUDE[ssDE](../includes/ssde-md.md)] データベースの [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] インスタンスに接続します。  
  
2.  Mdm.tbluser で、新しい管理者となるユーザーを見つけて、列の値をコピーし `SID` ます。  
  
3.  新しいクエリを作成します。  
  
4.  次のテキストを入力し、*ドメイン \ user_name*を新しい管理者のユーザー名と*SID*に置き換え、手順 2. でコピーした値を使用します。  
  
    ```  
    EXEC [mdm].[udpSecuritySetAdministrator] @UserName='DOMAIN\user_name', @SID = 'SID', @PromoteNonAdmin = 1  
    ```  
  
5.  クエリを実行します。  
  
## <a name="see-also"></a>参照  
 [管理者 (マスター データ サービス)](../../2014/master-data-services/administrators-master-data-services.md)  
  
  

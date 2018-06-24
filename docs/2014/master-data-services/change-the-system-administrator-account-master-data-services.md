---
title: システム管理者アカウント (Master Data Services) の変更 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- administrators [Master Data Services], changing
ms.assetid: cf30312e-4338-49a7-90f0-6e4f7b431ff8
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: a0e9a79120b4f184fb7acf07eeaf46101740a173
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36076618"
---
# <a name="change-the-system-administrator-account-master-data-services"></a>システム管理者アカウントの変更 (マスター データ サービス)
  として指定されているユーザー アカウントを変更することができます、[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]システム管理者です。  
  
> [!WARNING]  
>  この手順が完了すると、前のシステム管理者のユーザー アカウントは削除されます。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   新しい管理者のユーザー名を[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]のユーザーの一覧に追加する必要があります。 詳細については、次を参照してください。[ユーザーを追加&#40;Master Data Services&#41;](add-a-user-master-data-services.md)です。  
  
-   [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースで mdm.tblUser を表示して mdm.udpSecurityMemberProcessRebuildModel ストアド プロシージャを実行するための権限が必要です。 詳細については、「[データベース オブジェクト セキュリティ (マスター データ サービス)](../../2014/master-data-services/database-object-security-master-data-services.md)」を参照してください。  
  
### <a name="to-change-the-administrator-account"></a>管理者アカウントを変更するには  
  
1.  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を開き、 [!INCLUDE[ssDE](../includes/ssde-md.md)] データベースの [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] インスタンスに接続します。  
  
2.  Mdm.tblUser で、新しい管理者しの値をコピーするユーザーを見つけ、`SID`列です。  
  
3.  新しいクエリを作成します。  
  
4.  次のテキストを入力交換*domain \user_name*新しい管理者のユーザー名を持つと*SID*手順 2. でコピーした値を使用します。  
  
    ```  
    EXEC [mdm].[udpSecuritySetAdministrator] @UserName='DOMAIN\user_name', @SID = 'SID', @PromoteNonAdmin = 1  
    ```  
  
5.  クエリを実行します。  
  
## <a name="see-also"></a>参照  
 [管理者&#40;マスター データ サービス&#41;](../../2014/master-data-services/administrators-master-data-services.md)  
  
  
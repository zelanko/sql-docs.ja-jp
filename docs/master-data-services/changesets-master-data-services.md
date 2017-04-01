---
title: "変更セット (Master Data Services) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f227c49a-ed46-4e0f-8992-83093456cf94
caps.latest.revision: 13
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 13
---
# 変更セット (Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] では、エンティティに対する保留中の変更を変更セットに保存する機能をサポートします。 この機能には、2 つの使用シナリオがあります。  
  
-   **“承認が必要” がエンティティ管理者によって有効にされる場合の変更**  
  
     エンティティ管理者が、指定されたエンティティへの変更がコミットされる前に承認が必要と指定した場合、エンティティへの変更は、新しい変更セットまたは既存の変更セットに保存されてからのみ、承認のために送信することができます。  詳細については、「[承認が必要 (マスター データ サービス)](../master-data-services/approval-required-master-data-services.md)」を参照してください。  
  
     このワークフローを実行します。  
  
    1.  変更セットを作成します。 変更セットは、[開く] の状態です。 「[変更セットを作成する (マスター データ サービス)](../master-data-services/create-a-changeset-master-data-services.md)」を参照してください。  
  
    2.  変更セットを適用し、いくつかの変更を変更セットに加えます。 「[変更セットの適用および更新 (マスター データ サービス)](../master-data-services/apply-and-update-a-changeset-master-data-services.md)」を参照してください。  
  
    3.  承認のために、変更セットをエンティティ管理者に送信します。 変更セットは、[保留] の状態です。 「[変更セットのコミットまたは送信 (マスター データ サービス)](../master-data-services/commit-or-submit-a-changeset-master-data-services.md)」を参照してください。  
  
    4.  エンティティ管理者は、変更セットが承認待ちをしている電子メール通知を受け取ります。 エンティティ管理者が変更セットを承認した場合、変更セットは [承認済み] の状態になります。 「[変更セットの承認または拒否 (マスター データ サービス)](../master-data-services/approve-or-reject-a-changeset-master-data-services.md)」を参照してください。  
  
    5.  承認された変更セットは、自動的にコミットされます。 変更が正常にコミットされると、変更セットはコミット (committed) 状態になります。  
  
-   **ローカル ユーザーの変更**  
  
     後で使用または取得できるように、ローカルの変更を保存する必要がある場合は、変更セットを使用して保存できます。  
  
     このワークフローを実行します。  
  
    1.  変更セットを作成します。 変更セットは、[開く] の状態です。 「[変更セットを作成する (マスター データ サービス)](../master-data-services/create-a-changeset-master-data-services.md)」を参照してください。  
  
    2.  変更セットを適用し、いくつかの変更を変更セットに加えます。 「[変更セットの適用および更新 (マスター データ サービス)](../master-data-services/apply-and-update-a-changeset-master-data-services.md)」を参照してください。  
  
    3.  準備ができたら、変更セットをコミットします。 「[変更セットのコミットまたは送信 (マスター データ サービス)](../master-data-services/commit-or-submit-a-changeset-master-data-services.md)」を参照してください。  
  
## 参照  
 [変更セットを作成する (マスター データ サービス)](../master-data-services/create-a-changeset-master-data-services.md)   
 [変更セットの適用および更新 (マスター データ サービス)](../master-data-services/apply-and-update-a-changeset-master-data-services.md)   
 [変更セットのコミットまたは送信 (マスター データ サービス)](../master-data-services/commit-or-submit-a-changeset-master-data-services.md)   
 [変更セットの承認または拒否 (マスター データ サービス)](../master-data-services/approve-or-reject-a-changeset-master-data-services.md)   
 [変更セットの管理 (マスター データ サービス)](../master-data-services/manage-changesets-master-data-services.md)  
  
  
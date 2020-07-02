---
title: 変更セット
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: f227c49a-ed46-4e0f-8992-83093456cf94
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c6b91f1d0b4fbfff3294502b0953462f97efc707
ms.sourcegitcommit: 6be9a0ff0717f412ece7f8ede07ef01f66ea2061
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85811624"
---
# <a name="changesets-master-data-services"></a>変更セット (Master Data Services)

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] では、エンティティに対する保留中の変更を変更セットに保存する機能をサポートします。 この機能には、2 つの使用シナリオがあります。  
  
-   **"承認が必要" がエンティティ管理者によって有効にされた場合の変更**  
  
     エンティティ管理者が、指定されたエンティティへの変更がコミットされる前に承認が必要と指定した場合、エンティティへの変更は、新しい変更セットまたは既存の変更セットに保存されてからのみ、承認のために送信することができます。  詳細については、「[承認が必要 (マスター データ サービス)](../master-data-services/approval-required-master-data-services.md)」を参照してください。  
  
     このワークフローを実行します。  
  
    1.  変更セットを作成します。 変更セットは、[開く] の状態です。 「 [変更セットを作成する (マスター データ サービス)](../master-data-services/create-a-changeset-master-data-services.md)  
  
    2.  変更セットを適用し、いくつかの変更を変更セットに加えます。 「 [変更セットの適用および更新 (マスター データ サービス)](../master-data-services/apply-and-update-a-changeset-master-data-services.md)  
  
    3.  承認のために、変更セットをエンティティ管理者に送信します。 変更セットは、[保留] の状態です。 「 [変更セットのコミットまたは送信 (マスター データ サービス)](../master-data-services/commit-or-submit-a-changeset-master-data-services.md)  
  
    4.  エンティティ管理者は、変更セットが承認待ちをしている電子メール通知を受け取ります。 エンティティ管理者が変更セットを承認した場合、変更セットは [承認済み] の状態になります。 「 [変更セットの承認または拒否 (マスター データ サービス)](../master-data-services/approve-or-reject-a-changeset-master-data-services.md)  
  
    5.  承認された変更セットは、自動的にコミットされます。 変更が正常にコミットされると、変更セットはコミット (committed) 状態になります。  
  
-   **ローカル ユーザーの変更**  
  
     後で使用または取得できるように、ローカルの変更を保存する必要がある場合は、変更セットを使用して保存できます。  
  
     このワークフローを実行します。  
  
    1.  変更セットを作成します。 変更セットは、[開く] の状態です。 「 [変更セットを作成する (マスター データ サービス)](../master-data-services/create-a-changeset-master-data-services.md)  
  
    2.  変更セットを適用し、いくつかの変更を変更セットに加えます。 「 [変更セットの適用および更新 (マスター データ サービス)](../master-data-services/apply-and-update-a-changeset-master-data-services.md)  
  
    3.  準備ができたら、変更セットをコミットします。 「 [変更セットのコミットまたは送信 (マスター データ サービス)](../master-data-services/commit-or-submit-a-changeset-master-data-services.md)  
  
## <a name="see-also"></a>関連項目  
 [変更セット &#40;マスターデータサービスを作成し&#41;](../master-data-services/create-a-changeset-master-data-services.md)   
 [変更セットの適用および更新 &#40;マスターデータサービス&#41;](../master-data-services/apply-and-update-a-changeset-master-data-services.md)   
 [変更セット &#40;マスターデータサービスのコミットまたは送信&#41;](../master-data-services/commit-or-submit-a-changeset-master-data-services.md)   
 [変更セット &#40;マスターデータサービスを承認または拒否する&#41;](../master-data-services/approve-or-reject-a-changeset-master-data-services.md)   
 [変更セットの管理 &#40;マスター データ サービス&#41;](../master-data-services/manage-changesets-master-data-services.md)  
  
  

---
title: ID およびアクセス制御 (レプリケーション) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- access controls [SQL Server replication]
- security [SQL Server replication], identity and access control
- authentication [SQL Server replication]
- identity [Replication]
ms.assetid: 4da0e793-1ee4-4f69-a80b-45c6732a238d
caps.latest.revision: 8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ca8cbf2c68de39fc5f918390246a762955cf48a0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32961437"
---
# <a name="identity-and-access-control-replication"></a>ID およびアクセス制御 (レプリケーション)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  認証とは、あるエンティティ (ここでは、一般的にコンピューターを指します) によって、別のエンティティ ( *プリンシパル*とも呼ばれます。一般的に別のコンピューターまたはユーザーを指します) が自称するエンティティであるかどうかを確認するプロセスです。 承認とは、認証されたプリンシパルにリソース (ファイル システムのファイルやデータベースのテーブルなど) へのアクセスを認めるプロセスです。  
  
 レプリケーション セキュリティでは、認証と承認を使用して、レプリケートされたデータベース オブジェクトへのアクセスや、レプリケーション処理に関係するコンピューターやエージェントへのアクセスを制御します。 これは、以下の 3 つのメカニズムによって実現されます。  
  
-   エージェント セキュリティ  
  
     レプリケーション エージェントのセキュリティ モデルでは、レプリケーション エージェントの実行や接続に使用されるアカウントをきめ細かく制御できます。 エージェント セキュリティ モデルの詳細については、「 [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md)」を参照してください。 エージェントのログインとパスワードの設定の詳細については、「[Manage Logins and Passwords in Replication](../../../relational-databases/replication/security/manage-logins-and-passwords-in-replication.md)」(レプリケーションのログインとパスワードの管理) を参照してください。  
  
-   管理ロール  
  
     レプリケーションのセットアップ、メンテナンス、および処理に対して適切なサーバー ロールやデータベース ロールが使用されていることを確認します。 詳細については、「 [Security Role Requirements for Replication](../../../relational-databases/replication/security/security-role-requirements-for-replication.md)」を参照してください。  
  
-   パブリケーション アクセス リスト (PAL)  
  
     パブリケーションへのアクセスは、PAL を通じて許可されます。 PAL は、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows のアクセス制御リストによく似た機能を備えています。 サブスクライバーがパブリッシャーやディストリビューターに接続し、パブリケーションへのアクセスを要求すると、エージェントによって渡された認証情報が PAL に対して確認されます。 PAL の詳細および推奨事項については、「[Secure the Publisher](../../../relational-databases/replication/security/secure-the-publisher.md)」(パブリッシャーのセキュリティ保護) を参照してください。  
  
## <a name="filtering-published-data"></a>パブリッシュされたデータのフィルター選択  
 レプリケーションでは、レプリケートされたデータやオブジェクトへのアクセスを認証と承認を使用して制御する以外に、列のフィルター選択と行のフィルター選択という 2 つのオプションを使用して、サブスクライバーで利用できるようにするデータを制御できます。 フィルター選択の詳細については、「[パブリッシュされたデータのフィルター選択](../../../relational-databases/replication/publish/filter-published-data.md)」を参照してください。  
  
 アーティクルを定義する際には、パブリケーションに必要な列のみをパブリッシュして、不要な列や機密データを含む列を除外することができます。 たとえば、Adventure Works データベースの **Customer** テーブルを現場の販売担当者にパブリッシュする際には、経営陣以外には関係のない **AnnualSales** 列を除外できます。  
  
 パブリッシュされたデータをフィルター選択することによって、データへのアクセスを制限し、サブスクライバーで使用できるデータを指定できます。 たとえば、 **Customer** テーブルをフィルター選択して、 **ShareInfo** 列の値が "yes" の顧客に関する情報のみをパートナー企業に提供することなどが可能です。 マージ レプリケーションにおいて HOST_NAME() を含むパラメーター化されたフィルターを使用する場合は、セキュリティ上の留意事項があります。 詳細については、「 [Parameterized Row Filters](../../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md)」の「HOST_NAME() によるフィルター選択」を参照してください。  
  
## <a name="see-also"></a>参照  
 [セキュリティと保護 &#40;レプリケーション&#41;](../../../relational-databases/replication/security/security-and-protection-replication.md)   
 [セキュリティの概要 &#40;レプリケーション&#41;](../../../relational-databases/replication/security/security-overview-replication.md)   
 [脅威と脆弱性の対策 &#40;レプリケーション&#41;](../../../relational-databases/replication/security/threat-and-vulnerability-mitigation-replication.md)  
  
  

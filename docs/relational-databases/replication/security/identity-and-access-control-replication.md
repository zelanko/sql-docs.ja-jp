---
title: "ID およびアクセス制御 (レプリケーション) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "アクセス制御 [SQL Server レプリケーション]"
  - "セキュリティ [SQL Server レプリケーション], ID およびアクセス制御"
  - "認証 [SQL Server レプリケーション]"
  - "ID [レプリケーション]"
ms.assetid: 4da0e793-1ee4-4f69-a80b-45c6732a238d
caps.latest.revision: 8
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 8
---
# ID およびアクセス制御 (レプリケーション)
  認証は、エンティティ (通常は、このコンテキストでコンピューター) とも呼ばれますその他のエンティティを検証するプロセス、 *プリンシパル*, 、(通常、別のコンピューターまたはユーザー) が、本物であります。 承認とは、認証されたプリンシパルにリソース (ファイル システムのファイルやデータベースのテーブルなど) へのアクセスを認めるプロセスです。  
  
 レプリケーション セキュリティでは、認証と承認を使用して、レプリケートされたデータベース オブジェクトへのアクセスや、レプリケーション処理に関係するコンピューターやエージェントへのアクセスを制御します。 これは、以下の 3 つのメカニズムによって実現されます。  
  
-   エージェント セキュリティ  
  
     レプリケーション エージェントのセキュリティ モデルでは、レプリケーション エージェントの実行や接続に使用されるアカウントをきめ細かく制御できます。 エージェントのセキュリティ モデルの詳細については、次を参照してください。 [レプリケーション エージェントのセキュリティ モデル](../../../relational-databases/replication/security/replication-agent-security-model.md)します。 エージェントの設定のログインとパスワードについては、次を参照してください。 [レプリケーションの管理のログインとパスワード](../../../relational-databases/replication/security/manage-logins-and-passwords-in-replication.md)します。  
  
-   管理ロール  
  
     レプリケーションのセットアップ、メンテナンス、および処理に対して適切なサーバー ロールやデータベース ロールが使用されていることを確認します。 詳細については、次を参照してください。 [レプリケーションのセキュリティ ロール要件](../../../relational-databases/replication/security/security-role-requirements-for-replication.md)します。  
  
-   パブリケーション アクセス リスト (PAL)  
  
     パブリケーションへのアクセスは、PAL を通じて許可されます。 PAL は、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows のアクセス制御リストによく似た機能を備えています。 サブスクライバーがパブリッシャーやディストリビューターに接続し、パブリケーションへのアクセスを要求すると、エージェントによって渡された認証情報が PAL に対して確認されます。 詳細および PAL のベスト プラクティスは、「 [パブリッシャーのセキュリティ保護](../../../relational-databases/replication/security/secure-the-publisher.md)します。  
  
## パブリッシュされたデータのフィルター選択  
 レプリケーションでは、レプリケートされたデータやオブジェクトへのアクセスを認証と承認を使用して制御する以外に、列のフィルター選択と行のフィルター選択という 2 つのオプションを使用して、サブスクライバーで利用できるようにするデータを制御できます。 フィルターの詳細については、次を参照してください。 [パブリッシュされたデータのフィルター](../../../relational-databases/replication/publish/filter-published-data.md)します。  
  
 アーティクルを定義する際には、パブリケーションに必要な列のみをパブリッシュして、不要な列や機密データを含む列を除外することができます。 例については、発行するときに、 **顧客** テーブル、フィールド内の販売担当者に Adventure Works データベースからは省略できます、 **AnnualSales** 列で、企業の経営幹部にのみ関連する可能性があります。  
  
 パブリッシュされたデータをフィルター選択することによって、データへのアクセスを制限し、サブスクライバーで使用できるデータを指定できます。 たとえば、抽出することができます、 **顧客** の取引先企業は顧客に関する情報のみを受信できるようにテーブルを **ShareInfo** 列に"yes"の値 マージ レプリケーションにおいて HOST_NAME() を含むパラメーター化されたフィルターを使用する場合は、セキュリティ上の留意事項があります。 詳細については、「HOST_NAME() によるフィルター選択」のセクションを参照してください [パラメーター化された行フィルター](../../../relational-databases/replication/merge/parameterized-row-filters.md)します。  
  
## 参照  
 [セキュリティと保護と #40 です。レプリケーションと #41 です。](../../../relational-databases/replication/security/security-and-protection-replication.md)   
 [セキュリティの概要と #40 です。レプリケーションと #41 です。](../../../relational-databases/replication/security/security-overview-replication.md)   
 [脅威と脆弱性の対策と #40 です。レプリケーションと #41 です。](../../../relational-databases/replication/security/threat-and-vulnerability-mitigation-replication.md)  
  
  
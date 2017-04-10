---
title: "暗号化された列のデータをレプリケートする (SQL Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "03/06/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "暗号化 [SQL Server レプリケーション]、データ レプリケーション"
  - "暗号化 [SQL Server レプリケーション]"
  - "パブリッシング [SQL Server レプリケーション]、暗号化された列"
ms.assetid: d1f8f586-e5a3-4a71-9391-11198d42bfa3
caps.latest.revision: 8
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 8
---
# 暗号化された列のデータをレプリケートする (SQL Server Management Studio)
  レプリケーションでは、暗号化された列データをパブリッシュできます。 このデータの暗号化を解除してサブスクライバーで使用するには、パブリッシャーでのデータの暗号化に使用されたキーがサブスクライバーにも存在する必要があります。 レプリケーションでは、暗号化キーを送信する安全なメカニズムは提供されません。 このため、暗号化キーはサブスクライバーで手動で再作成する必要があります。 このトピックでは、パブリッシャーで列を暗号化し、暗号化キーをサブスクライバーで使用できるようにする方法について説明します。  
  
 基本的な手順は次のとおりです。  
  
1.  パブリッシャーで対称キーを作成します。  
  
2.  その対称キーを使用して列データを暗号化します。  
  
3.  暗号化された列を含むテーブルをパブリッシュします。  
  
4.  パブリケーションにサブスクライブします。  
  
5.  サブスクリプションを初期化します。  
  
6.  手順 1 と同じ値を ALGORITHM、KEY_SOURCE、IDENTITY_VALUE に使用して、サブスクライバーで対称キーを再作成します。  
  
7.  暗号化された列データにアクセスします。  
  
> [!NOTE]  
>  列データを暗号化するには、対称キーを使用する必要があります。 対称キー自体は、パブリッシャーとサブスクライバーで、それぞれ異なる手段で保護できます。  
  
### 暗号化された列データを作成およびレプリケートするには  
  
1.  パブリッシャーで実行 [CREATE SYMMETRIC KEY](../../../t-sql/statements/create-symmetric-key-transact-sql.md)します。  
  
    > [!IMPORTANT]  
    >  KEY_SOURCE の値は、対象キーの再作成およびデータの暗号化解除に使用できる重要なデータです。 KEY_SOURCE は、常に安全に格納および送信する必要があります。  
  
2.  実行 [OPEN SYMMETRIC KEY](../../../t-sql/statements/open-symmetric-key-transact-sql.md) を新しいキーを開きます。  
  
3.  使用して、 [EncryptByKey](../../../t-sql/functions/encryptbykey-transact-sql.md) パブリッシャーで列のデータを暗号化する関数。  
  
4.  実行 [CLOSE SYMMETRIC KEY](../../../t-sql/statements/close-symmetric-key-transact-sql.md) してキーを閉じます。  
  
5.  暗号化された列を含むテーブルをパブリッシュします。 詳しくは、「 [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md)」をご覧ください。  
  
6.  パブリケーションにサブスクライブします。 詳細については、次を参照してください。 [プル サブスクリプションを作成する](../../../relational-databases/replication/create-a-pull-subscription.md) または [プッシュ サブスクリプションを作成する](../../../relational-databases/replication/create-a-push-subscription.md)です。  
  
7.  サブスクリプションを初期化します。 詳細については、「 [Create and Apply the Initial Snapshot](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)」を参照してください。  
  
8.  サブスクライバーで、次のように実行します。 [CREATE SYMMETRIC KEY](../../../t-sql/statements/create-symmetric-key-transact-sql.md) ALGORITHM、KEY_SOURCE、および IDENTITY_VALUE 手順 1 と同様に同じ値を使用します。 ENCRYPTION BY には別の値を指定することもできます。  
  
    > [!IMPORTANT]  
    >  KEY_SOURCE の値は、対象キーの再作成およびデータの暗号化解除に使用できる重要なデータです。 KEY_SOURCE は、常に安全に格納および送信する必要があります。  
  
9. 実行 [OPEN SYMMETRIC KEY](../../../t-sql/statements/open-symmetric-key-transact-sql.md) を新しいキーを開きます。  
  
10. 使用して、 [DecryptByKey](../../../t-sql/functions/decryptbykey-transact-sql.md) サブスクライバーにレプリケートされたデータを復号化します。  
  
11. 実行 [CLOSE SYMMETRIC KEY](../../../t-sql/statements/close-symmetric-key-transact-sql.md) してキーを閉じます。  
  
## 例  
 この例では、対称キー、対称キーを保護するために使用される証明書、およびマスター キーを作成しています。 これらのキーは、パブリケーション データベースで作成されます。 これらは、`SalesOrderHeader` テーブル内の暗号化された列 (EncryptedCreditCardApprovalCode) の作成に使用されます。 この列は、暗号化していない CreditCardApprovalCode 列の代わりに、AdvWorksSalesOrdersMerge パブリケーションでパブリッシュされます。 可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 スクリプト ファイルに資格情報を格納する必要がある場合は、不正アクセスを防ぐために、ファイルを保護します。  
  
 [!code-sql[HowTo#sp_PublishEncryptedColumn](../../../relational-databases/replication/codesnippet/tsql/replicate-data-in-encryp_1.sql)]  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../relational-databases/replication/codesnippet/tsql/replicate-data-in-encryp_2.sql)]  
  
## 例  
 この例では、最初の例の ALGORITHM、KEY_SOURCE、および IDENTITY_VALUE の場合と同じ値を使用して、サブスクリプション データベース内に同じ対象キーを再作成しています。 この例は、暗号化された列をレプリケートする AdvWorksSalesOrdersMerge パブリケーションへのサブスクリプションが初期化済みであることを前提としています。 可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 スクリプト ファイルに資格情報を保存する必要がある場合は、格納時および送信時の不正アクセスからファイルを保護する必要があります。  
  
 [!code-sql[HowTo#sp_SubscriberEncryptedColumn](../../../relational-databases/replication/codesnippet/tsql/replicate-data-in-encryp_3.sql)]  
  
## 参照  
 [セキュリティの概要と #40 です。レプリケーションと #41 です。](../../../relational-databases/replication/security/security-overview-replication.md)   
 [2 台のサーバーでの同じ対称キーの作成](../../../relational-databases/security/encryption/create-identical-symmetric-keys-on-two-servers.md)  
  
  
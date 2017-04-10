---
title: "レッスン 2: Shared Access Signature を使用して SQL Server 資格情報を作成する | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "02/25/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-backup-restore"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 29e57ebd-828f-4dff-b473-c10ab0b1c597
caps.latest.revision: 17
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 17
---
# レッスン 2: Shared Access Signature を使用して SQL Server 資格情報を作成する
このレッスンでは、[「レッスン 1: Azure コンテナーに格納済みアクセス ポリシーと Shared Access Signature を作成する」](../relational-databases/lesson-1-create-stored-access-policy-and-shared-access-signature.md) で作成した Azure コンテナーに対して読み書きを行うために SQL Server で使用するセキュリティ情報を格納するための資格情報を作成します。  
  
SQL Server 資格情報は、SQL Server の外部にあるリソースへの接続に必要な認証情報を保存するために使用されるオブジェクトです。 資格情報には、ストレージ コンテナーの URI パスと、このコンテナーの Shared Access Signature が格納されます。  
  
> [!NOTE]  
> この Azure コンテナーに SQL Server 2012 SP1 CU2 以降のデータベースまたは SQL Server 2014 データベースをバックアップする場合、[こちら](https://technet.microsoft.com/en-US/library/dn435916(v=sql.120).aspx) に記載されている非推奨構文を使用すれば、ストレージ アカウント キーに基づいて SQL Server 資格情報を作成することができます。  
  
## SQL Server 資格情報の作成  
SQL Server 資格情報を作成するには、次の手順を実行します。  
  
1.  SQL Server Management Studio に接続します。  
  
2.  新しいクエリ ウィンドウを開き、オンプレミスの環境内にあるデータベース エンジンの SQL Server 2016 インスタンスに接続します。  
  
3.  新しいクエリ ウィンドウで、レッスン 1 で取得した Shared Access Signature を指定した CREATE CREDENTIAL ステートメントを貼り付けて、そのスクリプトを実行します。  
  
    スクリプトは、次のコードのようになります。  
  
    ```Transact-SQL  
  
    USE master  
    CREATE CREDENTIAL 'https://<mystorageaccountname>.blob.core.windows.net/<mystorageaccountcontainername>' – this name must match the container path, start with https and must not contain a forward slash.  
       WITH IDENTITY='SHARED ACCESS SIGNATURE' -- this is a mandatory string and do not change it.   
       , SECRET = 'sharedaccesssignature' –- this is the shared access signature key that you obtained in Lesson 1.   
    GO  
  
    ```  
  
4.  使用可能なすべての資格情報を表示するには、インスタンスに接続されたクエリ ウィンドウで次のステートメントを実行できます。  
  
    ```Transact-SQL  
    SELECT * from sys.credentials  
    ```  
  
5.  新しいクエリ ウィンドウを開き、Azure 仮想マシン内にあるデータベース エンジンの SQL Server 2016 インスタンスに接続します。  
  
6.  新しいクエリ ウィンドウで、レッスン 1 で取得した Shared Access Signature を指定した CREATE CREDENTIAL ステートメントを貼り付けて、そのスクリプトを実行します。  
  
7.  Azure コンテナーにアクセスするようにしたい SQL Server 2016 インスタンスが他にもある場合は、手順 5. と手順 6. を繰り返します。  
  
**次のレッスン:**  
  
[レッスン 3: URL へのデータベースのバックアップ](../relational-databases/lesson-3-database-backup-to-url.md)  
  
## 参照  
[資格情報 &#40;データベース エンジン&#41;](../relational-databases/security/authentication-access/credentials-database-engine.md)  
[CREATE CREDENTIAL &#40;Transact-SQL&#41;](../t-sql/statements/create-credential-transact-sql.md)  
[sys.credentials &#40;Transact-SQL&#41;](../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)  
  

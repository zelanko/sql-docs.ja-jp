---
title: 'レッスン 3: SQL Server の資格情報を作成する |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 29e57ebd-828f-4dff-b473-c10ab0b1c597
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 61a25d1f4e86204d05b3be6bf2a5dbc8cd0474b9
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "70153830"
---
# <a name="lesson-3-create-a-sql-server-credential"></a>レッスン 3:SQL Server 資格情報の作成
  このレッスンでは、Azure ストレージアカウントへのアクセスに使用するセキュリティ情報を格納するための資格情報を作成します。  
  
 SQL Server 資格情報は、SQL Server の外部にあるリソースへの接続に必要な認証情報を保存するために使用されるオブジェクトです。 資格情報には、ストレージ コンテナーの URI パスと Shared Access Signature キー値が格納されます。 データ ファイルまたはログ ファイルによって使用されるストレージ コンテナーごとに、名前がコンテナーのパスに一致する SQL Server 資格情報を作成する必要があります。  
  
 資格情報の全般的な情報については、「[資格情報 &#40;データベースエンジン&#41;](security/authentication-access/credentials-database-engine.md)」を参照してください。  
  
> [!IMPORTANT]  
>  以下で説明する SQL Server 資格情報を作成するための要件は、 [Azure 機能の SQL Server データファイル](databases/sql-server-data-files-in-microsoft-azure.md)に固有のものです。 Azure storage でのバックアッププロセス用の資格情報の作成の詳細については、「[レッスン 2: SQL Server 資格情報の作成](../tutorials/lesson-2-create-a-sql-server-credential.md)」を参照してください。  
  
 SQL Server 資格情報を作成するには、次の手順を実行します。  
  
1.  SQL Server Management Studio に接続します。  
  
2.  オブジェクト エクスプローラーで、インストールしたデータベース エンジンのインスタンスに接続します。  
  
3.  [標準] ツール バーの [新しいクエリ]をクリックします。  
  
4.  次の例をコピーしてクエリ ウィンドウに貼り付け、必要に応じて変更します。 次のステートメントは、ストレージコンテナーの共有アクセス証明書を格納するための SQL Server 資格情報を作成します。  
  
    ```sql  
  
    USE master  
    CREATE CREDENTIAL credentialname - this name should match the container path and it must start with https.   
       WITH IDENTITY='SHARED ACCESS SIGNATURE', -- this is a mandatory string and do not change it.   
       SECRET = 'sharedaccesssignature' -- this is the shared access signature key that you obtained in Lesson 2.   
    GO  
  
    ```  
  
     詳細については、SQL Server オンラインブックの「 [CREATE CREDENTIAL &#40;transact-sql&#41;](/sql/t-sql/statements/create-credential-transact-sql) 」を参照してください。  
  
5.  使用可能なすべての資格情報を表示するには、クエリ ウィンドウで次のステートメントを実行します。  
  
    ```sql  
    SELECT * from sys.credentials  
    ```  
  
     詳細については、「」を参照してください。資格情報の詳細については、SQL Server オンラインブックで[&#40;transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-credentials-transact-sql)を参照してください。  
  
 **次のレッスン:**  
  
 [レッスン 4:Azure Storage にデータベースを作成する](lesson-3-database-backup-to-url.md)  
  
  

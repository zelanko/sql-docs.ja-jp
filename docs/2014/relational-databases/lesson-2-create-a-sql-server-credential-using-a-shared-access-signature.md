---
title: 'レッスン 3: Create a SQL Server Credential |Microsoft ドキュメント'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 29e57ebd-828f-4dff-b473-c10ab0b1c597
caps.latest.revision: 7
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 201863a1df64cdc85ef41a55170948dbf4eba419
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36176170"
---
# <a name="lesson-3-create-a-sql-server-credential"></a>レッスン 3: SQL Server 資格情報の作成
  このレッスンでは、Windows Azure ストレージ アカウントにアクセスするために使用するセキュリティ情報を格納する資格情報を作成します。  
  
 SQL Server 資格情報は、SQL Server の外部にあるリソースへの接続に必要な認証情報を保存するために使用されるオブジェクトです。 資格情報には、ストレージ コンテナーの URI パスと Shared Access Signature キー値が格納されます。 データ ファイルまたはログ ファイルによって使用されるストレージ コンテナーごとに、名前がコンテナーのパスに一致する SQL Server 資格情報を作成する必要があります。  
  
 資格情報の詳細については、次を参照してください。[資格情報&#40;データベース エンジン&#41;](security/authentication-access/credentials-database-engine.md)です。  
  
> [!IMPORTANT]  
>  次に示す SQL Server 資格情報を作成するための要件に固有です、 [Windows Azure で SQL Server データ ファイル](databases/sql-server-data-files-in-microsoft-azure.md)機能します。 Azure ストレージにバックアップ プロセスの資格情報を作成する方法については、次を参照してください。[レッスン 2: Create a SQL Server Credential](../tutorials/lesson-2-create-a-sql-server-credential.md)です。  
  
 SQL Server 資格情報を作成するには、次の手順を実行します。  
  
1.  SQL Server Management Studio に接続します。  
  
2.  オブジェクト エクスプローラーで、インストールしたデータベース エンジンのインスタンスに接続します。  
  
3.  標準的なツール バーで、新しいクエリ をクリックします。  
  
4.  次の例をコピーしてクエリ ウィンドウに貼り付け、必要に応じて変更します。 次のステートメントでは、ストレージ コンテナーの共有アクセス証明書を格納する SQL Server の資格情報を作成します。  
  
    ```tsql  
  
    USE master  
    CREATE CREDENTIAL credentialname – this name should match the container path and it must start with https.   
       WITH IDENTITY='SHARED ACCESS SIGNATURE', -- this is a mandatory string and do not change it.   
       SECRET = 'sharedaccesssignature' –- this is the shared access signature key that you obtained in Lesson 2.   
    GO  
  
    ```  
  
     詳細については、次を参照してください。 [CREATE CREDENTIAL &#40;TRANSACT-SQL&#41; ](/sql/t-sql/statements/create-credential-transact-sql) SQL Server オンライン ブック。  
  
5.  使用可能なすべての資格情報を表示するには、クエリ ウィンドウで次のステートメントを実行します。  
  
    ```tsql  
    SELECT * from sys.credentials  
    ```  
  
     Sys.credentials の詳細については、次を参照してください。 [sys.credentials &#40;TRANSACT-SQL&#41; ](/sql/relational-databases/system-catalog-views/sys-credentials-transact-sql) SQL Server オンライン ブック。  
  
 **次のレッスン:**  
  
 [レッスン 4: Windows Azure ストレージにデータベースを作成する](lesson-3-database-backup-to-url.md)  
  
  

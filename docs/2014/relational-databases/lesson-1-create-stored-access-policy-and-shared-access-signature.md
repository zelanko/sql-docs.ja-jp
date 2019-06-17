---
title: 'レッスン 2: コンテナーのポリシーを作成し、Shared Access Signature (SAS) キーの生成 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 41674d9d-8132-4bff-be4d-85a861419f3d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 23e80a2bf02ee6b97449ea3acff38a3937d37000
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "67046737"
---
# <a name="lesson-2-create-a-policy-on-container-and-generate-a-shared-access-signature-sas-key"></a>レッスン 2: コンテナーのポリシーを作成し、Shared Access Signature (SAS) キーを生成する
  このレッスンでは、BLOB コンテナーのポリシーを作成する方法と、SAS キーを生成する方法について学習します。  
  
 保存されたアクセス ポリシーによって、サーバー側の Shared Access Signature のコントロール レベルが 1 つ増えます。 Shared Access Signature とは、コンテナー、BLOB、キュー、およびテーブルに対する制限付きアクセス権を付与する URI です。 この新しい機能強化を使用する場合は、読み取り、書き込み、一覧表示の権限のあるコンテナーに対するポリシーを作成する必要があります。  
  
 次の方法の 1 つを使用してポリシーと Shared Access Signature を作成できます。  
  
-   Windows Azure REST API 操作:[コンテナーを作成する](https://msdn.microsoft.com/library/azure/dd179468.aspx)、[コンテナー ACL の設定](https://msdn.microsoft.com/library/azure/dd179391.aspx)、および[コンテナー ACL の取得](https://msdn.microsoft.com/library/azure/dd179469.aspx)します。  
  
-   [CloudBlobContainer.GetSharedAccessSignature メソッド](https://docs.microsoft.com/dotnet/api/microsoft.azure.storage.blob.cloudblobcontainer.getsharedaccesssignature)windows Azure SDK。  
  
    ```  
  
       string signature = blob.GetSharedAccessSignature(new SharedAccessPolicy()   
        {   
            // Specify the expiration time for the signature.   
            SharedAccessExpiryTime = DateTime.Now.Years(1),   
            // Specify the permissions granted by the signature.    
            Permissions = SharedAccessPermissions.Write | SharedAccessPermissions.Read   
        });  
  
    ```  
  
-   などのサード パーティの Windows Azure エクスプ ローラー ツール[Azure ストレージ エクスプ ローラー](http://azurestorageexplorer.codeplex.com/)します。  
  
 **次のレッスン:**  
  
 [レッスン 3:SQL Server 資格情報を作成します。](../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)  
  
  

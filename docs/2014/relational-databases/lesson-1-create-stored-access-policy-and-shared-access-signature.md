---
title: レッスン 2。 コンテナーのポリシーを作成し、Shared Access Signature (SAS) キーの生成 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 41674d9d-8132-4bff-be4d-85a861419f3d
caps.latest.revision: 7
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 708c347e587d19ebfb7c2f24e94fd59db0289c52
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37324302"
---
# <a name="lesson-2-create-a-policy-on-container-and-generate-a-shared-access-signature-sas-key"></a>レッスン 2。 コンテナーのポリシーを作成し、Shared Access Signature (SAS) キーを生成する
  このレッスンでは、BLOB コンテナーのポリシーを作成する方法と、SAS キーを生成する方法について学習します。  
  
 保存されたアクセス ポリシーによって、サーバー側の Shared Access Signature のコントロール レベルが 1 つ増えます。 Shared Access Signature とは、コンテナー、BLOB、キュー、およびテーブルに対する制限付きアクセス権を付与する URI です。 この新しい機能強化を使用する場合は、読み取り、書き込み、一覧表示の権限のあるコンテナーに対するポリシーを作成する必要があります。  
  
 次の方法の 1 つを使用してポリシーと Shared Access Signature を作成できます。  
  
-   Windows Azure REST API 操作:[コンテナーの作成](https://msdn.microsoft.com/library/azure/dd179468.aspx)、 [Set Container ACL](https://msdn.microsoft.com/library/azure/dd179391.aspx)、および[コンテナー ACL の取得](https://msdn.microsoft.com/library/azure/dd179469.aspx)します。  
  
-   [CloudBlobContainer.GetSharedAccessSignature メソッド](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.storageclient.cloudblobcontainer.getsharedaccesssignature.aspx)windows Azure SDK。  
  
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
  
 [レッスン 3: SQL Server 資格情報の作成](../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)  
  
  

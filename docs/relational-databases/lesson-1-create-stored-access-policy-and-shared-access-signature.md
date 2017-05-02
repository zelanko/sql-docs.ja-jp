---
title: "レッスン 1: 保存されたアクセス ポリシーと Shared Access Signature を作成する | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 06/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
ms.assetid: 41674d9d-8132-4bff-be4d-85a861419f3d
caps.latest.revision: 22
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f2c8af4701b9a01ee21613fe7e093a89f1d8f990
ms.lasthandoff: 04/11/2017

---
# <a name="lesson-1-create-stored-access-policy-and-shared-access-signature"></a>レッスン 1: 保存されたアクセス ポリシーと Shared Access Signature を作成する
このレッスンでは [Azure PowerShell](https://azure.microsoft.com/en-us/documentation/articles/powershell-install-configure/) スクリプトを使用して、Azure BLOB コンテナーに格納済みアクセス ポリシーを使用した Shared Access Signature を作成します。  
  
> [!NOTE]  
> このスクリプトは、Azure PowerShell 5.0.10586 を使用して作成されています。  
  
Shared Access Signature とは、コンテナー、BLOB、キュー、またはテーブルに対する制限付きアクセス権を付与する URI です。 格納済みアクセス ポリシーによって、取り消し、期限切れ、アクセス権の拡張などのサーバー側の Shared Access Signatures のコントロールのレベルが追加されます。 この新しい機能強化を使用する場合は、少なくとも読み取り、書き込み、一覧表示の権限のあるコンテナーに対してポリシーを作成する必要があります。  
  
格納済みアクセス ポリシーと Shared Access Signature を作成するには、Azure PowerShell、Azure Storage SDK、Azure REST API、またはサード パーティのユーティリティを使用します。 このチュートリアルでは、Azure PowerShell スクリプトを使用して、このタスクを実行する方法について説明します。 スクリプトは、リソース マネージャー展開モデルを使用して、次の新しいリソースを作成します。  
  
-   リソース グループ  
  
-   [ストレージ アカウント]  
  
-   Azure BLOB コンテナー  
  
-   SAS ポリシー  
  
このスクリプトでは、まず前述のリソースの名前と次の必要な入力値の名前を指定するための多くの変数を宣言します。  
  
-   その他のリソース オブジェクトの名前付けで使用されるプレフィックス名  
  
-   サブスクリプション名  
  
-   データ センターの場所  
  
> [!NOTE]  
> このスクリプトは、既存の ARM または従来の展開モデル リソースのどちらも使用できるように記述します。  
  
このスクリプトでは、最後に「 [レッスン 2: Shared Access Signature を使用して SQL Server 資格情報を作成する](../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)」で使用する適切な CREATE CREDENTIAL ステートメントを生成します。 このステートメントは、自動的にクリップボードにコピーされ、コンソールに出力されるので、確認できます。  
  
コンテナーのポリシーを作成し、Shared Access Signature (SAS) キーを生成するには、次の手順に従います。  
  
1.  Window PowerShell または Windows PowerShell ISE (前述のバージョン要件を参照してください) を開きます。  
  
2.  次のスクリプトを編集してから、実行します。  
  
    ```  
    \<#   
    This script uses the Azure Resource model and creates a new ARM storage account.  
    Modify this script to use an existing ARM or classic storage account   
    using the instructions in comments within this script  
    #>  
    # Define global variables for the script  
    $prefixName = '<a prefix name>'  # used as the prefix for the name for various objects  
    $subscriptionName='<your subscription name>'   # the name  of subscription name you will use  
    $locationName = '<a data center location>'  # the data center region you will use  
    $storageAccountName= $prefixName + 'storage' # the storage account name you will create or use  
    $containerName= $prefixName + 'container'  # the storage container name to which you will attach the SAS policy with its SAS token  
    $policyName = $prefixName + 'policy' # the name of the SAS policy  
  
    \<#   
    Using Azure Resource Manager deployment model  
    Comment out this entire section and use the classic storage account name to use an existing classic storage account  
    #>  
  
    # Set a variable for the name of the resource group you will create or use  
    $resourceGroupName=$prefixName + 'rg'   
  
    # adds an authenticated Azure account for use in the session   
    Login-AzureRmAccount    
  
    # set the tenant, subscription and environment for use in the rest of   
    Set-AzureRmContext -SubscriptionName $subscriptionName   
  
    # create a new resource group - comment out this line to use an existing resource group  
    New-AzureRmResourceGroup -Name $resourceGroupName -Location $locationName   
  
    # Create a new ARM storage account - comment out this line to use an existing ARM storage account  
    New-AzureRmStorageAccount -Name $storageAccountName -ResourceGroupName $resourceGroupName -Type Standard_RAGRS -Location $locationName   
  
    # Get the access keys for the ARM storage account  
    $accountKeys = Get-AzureRmStorageAccountKey -ResourceGroupName $resourceGroupName -Name $storageAccountName  
  
    # Create a new storage account context using an ARM storage account  
    $storageContext = New-AzureStorageContext -StorageAccountName $storageAccountName -StorageAccountKey $accountKeys[0].Value 
  
    \<#  
    Using the Classic deployment model  
    Use the following four lines to use an existing classic storage account  
    #>  
    #Classic storage account name  
    #Add-AzureAccount  
    #Select-AzureSubscription -SubscriptionName $subscriptionName #provide an existing classic storage account  
    #$accountKeys = Get-AzureStorageKey -StorageAccountName $storageAccountName  
    #$storageContext = New-AzureStorageContext -StorageAccountName $storageAccountName -StorageAccountKey $accountKeys.Primary  
  
    # The remainder of this script works with either the ARM or classic sections of code above  
  
    # Creates a new container in blob storage  
    $container = New-AzureStorageContainer -Context $storageContext -Name $containerName  
    $cbc = $container.CloudBlobContainer  
  
    # Sets up a Stored Access Policy and a Shared Access Signature for the new container  
    $permissions = $cbc.GetPermissions();  
    $policyName = $policyName  
    $policy = new-object 'Microsoft.WindowsAzure.Storage.Blob.SharedAccessBlobPolicy'  
    $policy.SharedAccessStartTime = $(Get-Date).ToUniversalTime().AddMinutes(-5)  
    $policy.SharedAccessExpiryTime = $(Get-Date).ToUniversalTime().AddYears(10)  
    $policy.Permissions = "Read,Write,List,Delete"  
    $permissions.SharedAccessPolicies.Add($policyName, $policy)  
    $cbc.SetPermissions($permissions);  
  
    # Gets the Shared Access Signature for the policy  
    $policy = new-object 'Microsoft.WindowsAzure.Storage.Blob.SharedAccessBlobPolicy'  
    $sas = $cbc.GetSharedAccessSignature($policy, $policyName)  
    Write-Host 'Shared Access Signature= '$($sas.Substring(1))''  
  
    # Outputs the Transact SQL to the clipboard and to the screen to create the credential using the Shared Access Signature  
    Write-Host 'Credential T-SQL'  
    $tSql = "CREATE CREDENTIAL [{0}] WITH IDENTITY='Shared Access Signature', SECRET='{1}'" -f $cbc.Uri,$sas.Substring(1)   
    $tSql | clip  
    Write-Host $tSql  
  
    ```  
  
3.  スクリプトが完了すると、CREATE CREDENTIAL ステートメントがクリップボード上にあるため、次のレッスンで使用できます。  
  
**次のレッスン**  
  
[レッスン 2: Shared Access Signature を使用して SQL Server 資格情報を作成する](../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)  
  
## <a name="see-also"></a>参照  
[Shared Access Signature, 第 1 部: SAS モデルについて](https://azure.microsoft.com/en-us/documentation/articles/storage-dotnet-shared-access-signature-part-1/)  
[コンテナーの作成](https://msdn.microsoft.com/library/azure/dd179468.aspx)  
[コンテナー ACL の設定](https://msdn.microsoft.com/library/azure/dd179391.aspx)  
[コンテナー ACL の取得](https://msdn.microsoft.com/library/azure/dd179469.aspx)  
  
  
  



---
title: "接続マネージャーの azure Data Lake Store |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SQL13.DTS.DESIGNER.AFPADLSCM.F1
- sql14.dts.designer.afpadlscm.f1
ms.assetid: f4c44553-0f08-4731-ac47-7534990b8c8d
caps.latest.revision: 7
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: a2e3655bedbb24f2174a62c8792cd168e7642592
ms.openlocfilehash: 39630087acdb2ade2e77d4364e4467f8d740d8d4
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="azure-data-lake-store-connection-manager"></a>Azure Data Lake Store 接続マネージャー
  **Azure Data Lake Store 接続マネージャー** では、SSIS パッケージを 2 種類の認証 (Azure AD のユーザー ID および Azure AD のサービス ID) を使用して Azure Data Lake Store サービスに接続することができます。  
  
 **接続マネージャーの Azure Data Lake Store**のコンポーネントである、 [SQL Server Integration Services (SSIS) Feature Pack for Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md)です。

>   [!NOTE]
> Azure Data Lake Store 接続マネージャーとこれを使用するコンポーネント (つまり、Azure Data Lake Store Source と Azure Data Lake Store Destination) がサービスに接続できるようにするために、必ず最新バージョンの Azure Feature Pack を [こちら](https://www.microsoft.com/download/details.aspx?id=49492)からダウンロードしてください。 
 
## <a name="configure-the-azure-data-lake-store-connection-manager"></a>Azure Data Lake Store 接続マネージャーを構成する

 
1.  **[SSIS 接続マネージャーの追加]** ダイアログ ボックスで **[AzureDataLake]**を選択し、 **[追加]**をクリックします。  
  
2.  Azure Data Lake Store 接続マネージャー エディター ダイアログ ボックスの **[ADLS ホスト]** フィールドに、Azure Data Lake Store ホストの URL を入力します。 例:`https://test.azuredatalakestore.net`または`test.azuredatalakestore.net`です。
  
3.  Azure Data Lake Store データにアクセスするための該当する認証の種類を選択します。

    1.  **[Azure AD のユーザー ID]** 認証オプションを選択した場合は、次の操作を行います。
        1. **[ユーザー名]** と **[パスワード]** のフィールドに値を指定します。 
    
        2. **[接続テスト]** ボタンをクリックして接続をテストします。 自分自身とテナント管理者が SSIS から Azure Data Lake Store データへのアクセスに同意していない場合は、別ウィンドウで表示されるダイアログで **[同意する]** ボタンをクリックし、SSIS から Azure Data Lake Store データへのアクセスに同意する必要があります。 この同意エクスペリエンスの詳細については、「 [Azure Active Directory とアプリケーションの統合](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-integrating-applications#updating-an-application)」を参照してください。
    
        >   [!NOTE] 
        > Azure AD のユーザー ID 認証オプションでは、多要素認証と Microsoft アカウントはサポートされていません。
    
    2. **[Azure AD のサービス ID]** 認証オプションを選択した場合は、次の操作を行います。
        1. Azure Data Lake リソースにアクセスできる AAD アプリケーションおよびサービス プリンシパルを作成します。
    
        2. Azure Data Lake リソースにアクセスするために適切な権限をこの AAD アプリケーションに割り当てます。 この認証オプションの詳細については、「 [Use portal to create Active Directory application and service principal that can access resources](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-create-service-principal-portal)」 (ポータルを使用して、リソースにアクセスできる Active Directory アプリケーションとサービス プリンシパルを作成する) を参照してください。
    
        3. **[クライアント ID]**、 **[シークレット キー]** および **[テナント名]** の各フィールドに値を指定します。
    
        4. **[接続テスト]** ボタンをクリックして接続をテストします。  
  
6.  **[OK]** をクリックして、ダイアログ ボックスを閉じます。  
  
    作成した接続マネージャーのプロパティは、 **[プロパティ]** ウィンドウに表示されます。  
  
  

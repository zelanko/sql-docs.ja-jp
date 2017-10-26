---
title: "接続マネージャーの azure Data Lake Store |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-server-2016
ms.reviewer: douglasl
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
author: Lingxi-Li
ms.author: lingxl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 29b296b2ae7e04871e81a9c236cb990bdd19562b
ms.openlocfilehash: 0a84b10114d785c9216a0902b2eefbcb0bd3f4c8
ms.contentlocale: ja-jp
ms.lasthandoff: 10/11/2017

---
# <a name="azure-data-lake-store-connection-manager"></a>Azure Data Lake Store 接続マネージャー
SQL Server Integration Services (SSIS) パッケージは、Azure Data Lake Store の接続マネージャーを使用して、2 次認証の種類のいずれかの Azure Data Lake Store サービスに接続できます。
-   Azure AD のユーザー Id
-   Azure AD サービス Id 

Azure Data Lake Store の接続マネージャーのコンポーネントである、 [SQL Server Integration Services (SSIS) Feature Pack for Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md)です。

>   [!NOTE]
> Azure Data Lake Store 接続マネージャーとこれを使用するコンポーネント (つまり、Azure Data Lake Store Source と Azure Data Lake Store Destination) がサービスに接続できるようにするために、必ず最新バージョンの Azure Feature Pack を [こちら](https://www.microsoft.com/download/details.aspx?id=49492)からダウンロードしてください。 
 
## <a name="configure-the-azure-data-lake-store-connection-manager"></a>Azure Data Lake Store 接続マネージャーを構成する

1.  **SSIS 接続マネージャーの追加**ダイアログ ボックスで、 **AzureDataLake**、し、**追加**です。 **Azure データ ストア接続マネージャー エディター Lake**  ダイアログ ボックスが表示されます。
  
2.  **Azure データ ストア接続マネージャー エディター Lake**  ダイアログ ボックスで、 **ADLS ホスト**フィールドに、Azure Data Lake Store ホスト URL を指定します。 例:`https://test.azuredatalakestore.net`または`test.azuredatalakestore.net`です。
  
3.  **認証**フィールドに、Azure Data Lake Store のデータにアクセスする適切な認証の種類を選択します。

    1.  選択した場合、 **Azure AD のユーザー Id**認証オプションで、次の手順に従います。
        1. 値を指定して、**ユーザー名**と**パスワード**フィールドです。 
    
        2. 接続をテストするには、次のように選択します。**接続のテスト**です。 ユーザーまたはテナント管理者が Azure Data Lake Store のデータ アクセスを選択する SSIS を許可することに同意していない以前場合**Accept**されたらです。 この同意エクスペリエンスの詳細については、「 [Azure Active Directory とアプリケーションの統合](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-integrating-applications#updating-an-application)」を参照してください。
    
        >   [!NOTE] 
        > 選択した場合、 **Azure AD のユーザー Id**認証オプション、多要素認証と Microsoft アカウントの認証はサポートされていません。
    
    2. 選択した場合、 **Azure AD サービス Id**認証オプションで、次の手順に従います。
        1. Azure Active Directory (AAD) のアプリケーションとサービスをプリンシパルは、Azure Data Lake データへのアクセスを作成します。
    
        2. この AAD アプリケーションを Azure Data Lake のリソースにアクセスできるようにする適切なアクセス許可を割り当てます。 この認証オプションの詳細については、「 [Use portal to create Active Directory application and service principal that can access resources](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-create-service-principal-portal)」 (ポータルを使用して、リソースにアクセスできる Active Directory アプリケーションとサービス プリンシパルを作成する) を参照してください。
    
        3. 値を指定して、**クライアント Id**、**シークレット キー**、および**テナント名**フィールドです。
    
        4. 接続をテストするには、次のように選択します。**接続のテスト**です。  
  
6.  選択**OK**を閉じる、 **Azure データ Lake ストア接続マネージャー エディター**  ダイアログ ボックス。  

## <a name="view-the-properties-of-the-connection-manager"></a>接続マネージャーのプロパティを表示します。
作成した接続マネージャーのプロパティは、 **[プロパティ]** ウィンドウに表示されます。  
  
  


---
title: Azure Data Lake Analytics 接続マネージャー | Microsoft Docs
ms.custom: ''
ms.date: 05/18/2018
ms.prod: sql
ms.prod_service: integration-services
ms.component: connection-manager
ms.reviewer: douglasl
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- SQL13.DTS.DESIGNER.AFPADLSCM.F1
- sql14.dts.designer.afpadlscm.f1
ms.assetid: f4c44553-0f08-4731-ac47-7534990b8c8d
caps.latest.revision: 7
author: yanancai
ms.author: yanacai
manager: craigg
ms.openlocfilehash: 17b63aad55cf50262d7e1e56267859b1a34cc9d3
ms.sourcegitcommit: 44e9bf62f2c75449c17753ed66bf85c43928dbd5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/05/2018
ms.locfileid: "37854414"
---
# <a name="azure-data-lake-analytics-connection-manager"></a>Azure Data Lake Analytics 接続マネージャー

SQL Server Integration Services (SSIS) パッケージでは、Azure Data Lake Analytics 接続マネージャーを使用して、次の 2 つの認証の種類のいずれかで Azure Data Lake Analytics アカウントに接続できます。
-   Azure AD のユーザー ID
-   Azure AD のサービス ID 

Azure Data Lake Analytics 接続マネージャー は、[SQL Server Integration Services (SSIS) Feature Pack for Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md) のコンポーネントです。
 
## <a name="configure-the-azure-data-lake-analytics-connection-manager"></a>Azure Data Lake Analytics 接続マネージャーを構成する

1.  **[SSIS 接続マネージャーの追加]** ダイアログ ボックスで **[AzureDataLakeAnalytics]** を選択してから **[追加]** を選択します。 **[Azure Data Lake Analytics Connection Manager Editor]\(Azure Data Lake Analytics 接続マネージャー エディター\)** ダイアログ ボックスが開きます。
  
2.  **[Azure Data Lake Analytics Connection Manager Editor]\(Azure Data Lake Analytics 接続マネージャー エディター\)** ダイアログ ボックスの **[ADLA Account Name]\(ADLA アカウント名\)** フィールドに、Azure Data Lake Analytics アカウントの名前を入力します。 たとえば、「myadlaaccountname」などと入力します。
  
3.  **[認証]** フィールドで、Azure Data Lake Analytics のデータにアクセスするために適切な認証の種類を選択します。

    1.  **[Azure AD のユーザー ID]** 認証オプションを選択する場合は、次の操作を行います。
        1. **[ユーザー名]** と **[パスワード]** のフィールドに値を指定します。 
    
        2. 接続をテストするには、**[接続テスト]** を選択します。 自分自身またはテナント管理者が SSIS から Azure Data Lake Analytics アカウントへのアクセスに同意していない場合は、プロンプトが表示されたときに **[同意する]** を選択します。 この同意エクスペリエンスの詳細については、「[Azure Active Directory とアプリケーションの統合](https://docs.microsoft.com/azure/active-directory/active-directory-integrating-applications#updating-an-application)」を参照してください。
    
        >   [!NOTE] 
        > **[Azure AD のユーザー ID]** 認証オプションを選択する場合、多要素認証と Microsoft アカウント認証はサポートされません。
    
    2. **[Azure AD のサービス ID]** 認証オプションを選択する場合は、次の操作を行います。
        1. Azure Data Lake Analytics アカウントにアクセスするための Azure Active Directory (AAD) アプリケーションおよびサービス プリンシパルを作成します。 この認証オプションの詳細については、「[Use portal to create Active Directory application and service principal that can access resources](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal)」 (ポータルを使用して、リソースにアクセスできる Active Directory アプリケーションとサービス プリンシパルを作成する) を参照してください。
    
        2. 適切な権限を割り当てて、この AAD アプリケーションが Azure Data Lake Analytics アカウントにアクセスできるようにします。 [ユーザー追加ウィザードを使用](https://docs.microsoft.com/azure/data-lake-analytics/data-lake-analytics-manage-use-portal#add-a-new-user)して Azure Data Lake Analytics アカウントへのアクセス許可を付与する方法を確認してください。 
    
        3. **[アプリケーション ID]**、**[認証キー]**、**[テナント ID]** フィールドの値を指定します。
    
        4. 接続をテストするには、**[接続テスト]** を選択します。  

4.  **[OK]** を選択して、**[Azure Data Lake Analytics Connection Manager Editor]\(Azure Data Lake Analytics 接続マネージャー エディター\)** ダイアログ ボックスを閉じます。  

## <a name="view-the-properties-of-the-connection-manager"></a>接続マネージャーのプロパティを表示する
作成した接続マネージャーのプロパティは、 **[プロパティ]** ウィンドウに表示されます。  
  
  

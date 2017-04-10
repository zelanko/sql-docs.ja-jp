---
title: "マスター データ サービスを使用した Data Quality Services 統合の有効化 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ab32938d-a80e-4106-80d4-94b2de3d67dc
caps.latest.revision: 5
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 5
---
# マスター データ サービスを使用した Data Quality Services 統合の有効化
  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] では、Data Quality Services (DQS) によって照合機能が提供されます。 この機能を使用するには、機能を有効にする必要があります。  
  
## 前提条件  
  
-   [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Web アプリケーションとデータベースが存在する必要があります。  
  
-   Data Quality Services 機能と Data Quality クライアントは、MDS データベースをホストする同じ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス上にインストールする必要があります。 詳細については、「[Data Quality Services のインストール](../../data-quality-services/install-windows/install-data-quality-services.md)」を参照してください。  
  
### Data Quality Services 統合を有効にするには  
  
1.  [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] を開きます。  
  
2.  左ペインで **[Web の構成]**をクリックします。  
  
3.  **[Web の構成]** ページで、Web サイトと Web アプリケーションを選択します。  
  
4.  **[DQS 統合の有効化]** セクションで、**[Data Quality Services との統合を有効化]** をクリックします。  
  
5.  確認のダイアログ ボックスで **[OK]**をクリックします。  
  
## 参照  
 [Excel 用 MDS アドインでのデータ品質照合](../../master-data-services/microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md)   
 [Microsoft Excel 用マスター データ サービス アドイン](../../master-data-services/microsoft-excel-add-in/master-data-services-add-in-for-microsoft-excel.md)   
 [マスター データ サービスのインストール](../../master-data-services/install-windows/install-master-data-services.md)  
  
  
---
title: "マスター データ サービスと Data Quality Services 統合を有効にする |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- setup-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ab32938d-a80e-4106-80d4-94b2de3d67dc
caps.latest.revision: 5
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 2086ab8ca26f813fe2e6c0a6ab3ec924f6024ab3
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="enable-data-quality-services-integration-with-master-data-services"></a>マスター データ サービスを使用した Data Quality Services 統合の有効化
  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]、Data Quality Services (DQS) によって照合機能提供します。 この機能を使用するには、機能を有効にする必要があります。  
  
## <a name="prerequisites"></a>前提条件  
  
-   [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Web アプリケーションとデータベースが存在する必要があります。  
  
-   Data Quality Services 機能と Data Quality クライアントは、MDS データベースをホストする同じ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス上にインストールする必要があります。 詳細については、「 [Data Quality Services のインストール](../../data-quality-services/install-windows/install-data-quality-services.md)」を参照してください。  
  
### <a name="to-enable-data-quality-services-integration"></a>Data Quality Services 統合を有効にするには  
  
1.  [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]を開きます。  
  
2.  左ペインで **[Web の構成]**をクリックします。  
  
3.  **[Web の構成]** ページで、Web サイトと Web アプリケーションを選択します。  
  
4.  **[DQS 統合の有効化]** セクションで、 **[Data Quality Services との統合を有効化]**をクリックします。  
  
5.  確認のダイアログ ボックスで **[OK]**をクリックします。  
  
## <a name="see-also"></a>参照  
 [Excel 用の MDS アドインでは、照合データ品質](../../master-data-services/microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md)   
 [マスター データ サービス アドインを Microsoft Excel](../../master-data-services/microsoft-excel-add-in/master-data-services-add-in-for-microsoft-excel.md)   
 [マスター データ サービスのインストール](../../master-data-services/install-windows/install-master-data-services.md)  
  
  

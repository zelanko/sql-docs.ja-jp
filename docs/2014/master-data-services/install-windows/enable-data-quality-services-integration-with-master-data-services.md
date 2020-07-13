---
title: マスター データ サービスを使用した Data Quality Services 統合の有効化 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: ab32938d-a80e-4106-80d4-94b2de3d67dc
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 9b268b6d9a5bd784cc5fcb0a20029df2e544e92f
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84971318"
---
# <a name="enable-data-quality-services-integration-with-master-data-services"></a>マスター データ サービスを使用した Data Quality Services 統合の有効化
  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]では、Data Quality Services (DQS) によって照合機能が提供されます。 この機能を使用するには、機能を有効にする必要があります。  
  
## <a name="prerequisites"></a>前提条件  
  
-   [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Web アプリケーションとデータベースが存在する必要があります。  
  
-   Data Quality Services 機能と Data Quality クライアントは、MDS データベースをホストする同じ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス上にインストールする必要があります。 詳細については、「 [Data Quality Services のインストール](../../data-quality-services/install-windows/install-data-quality-services.md)」を参照してください。  
  
### <a name="to-enable-data-quality-services-integration"></a>Data Quality Services 統合を有効にするには  
  
1.  [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] を開きます。  
  
2.  左ペインで **[Web の構成]** をクリックします。  
  
3.  **[Web の構成]** ページで、Web サイトと Web アプリケーションを選択します。  
  
4.  **[DQS 統合の有効化]** セクションで、 **[Data Quality Services との統合を有効化]** をクリックします。  
  
5.  確認のダイアログ ボックスで **[OK]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [Excel 用 MDS アドインでのデータ品質照合](../microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md)   
 [Microsoft Excel 用マスター データ サービス アドイン](../microsoft-excel-add-in/master-data-services-add-in-for-microsoft-excel.md)   
 [マスター データ サービスのインストール](install-master-data-services.md)  
  
  

---
title: "ビジネス ルールの適用 (Excel 用 MDS アドイン) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cd106345-f561-4966-88d3-a69139b2bd78
caps.latest.revision: 7
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 7
---
# ビジネス ルールの適用 (Excel 用 MDS アドイン)
  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] では、データを検証してデータが有効であることを確認する必要がある場合に、ビジネス ルールを適用できます。 検証に基づいて修正し、データを再度パブリッシュできます。  
  
> [!NOTE]  
>  データの検証は、データをパブリッシュするときに自動的に行われます。 詳細については、「[検証 (マスター データ サービス)](../../master-data-services/validation-master-data-services.md)」を参照してください。  
  
## 前提条件  
 この手順を実行するには  
  
-   **[エクスプローラー]** 機能領域へのアクセス権が必要です。  
  
-   MDS によって管理されるデータが含まれているアクティブなワークシートが必要です。  
  
### ビジネス ルールを適用するには  
  
1.  **[パブリッシュと検証]** グループの **[ルールの適用]** をクリックします。  
  
    > [!NOTE]  
    >  一度に検証されるメンバー (行) の数は、[!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]の設定によって異なります。 詳細については、「[ビジネス ルール設定](../../master-data-services/system-settings-master-data-services.md#BusinessRules)」を参照してください。  
  
2.  データがビジネス ルールに対して検証され、2 つの状態列が表示されます。 これらの列が自動的に表示されない場合は、**[パブリッシュと検証]** グループの **[状態の表示]** をクリックして列を表示します。  
  
## 参照  
 [概要: Excel からのデータのインポート (Excel 用 MDS アドイン)](../../master-data-services/microsoft-excel-add-in/overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
  
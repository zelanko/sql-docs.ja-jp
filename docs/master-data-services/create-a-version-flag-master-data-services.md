---
title: "バージョン フラグを作成する (マスター データ サービス) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "バージョン フラグの作成 [マスター データ サービス]"
  - "バージョン フラグ [マスター データ サービス], 作成"
  - "バージョン [マスター データ サービス], フラグの作成"
ms.assetid: 3067e1e3-05b7-4f11-9206-c612ef4e7e42
caps.latest.revision: 7
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 7
---
# バージョン フラグを作成する (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] で、バージョンに割り当てるバージョン フラグを作成します。 フラグによって、ユーザーまたはサブスクライブ システムが使用する必要があるバージョンを示すことができます。  
  
## 前提条件  
 この手順を実行するには  
  
-   **[バージョン管理]** 機能領域にアクセスする権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「[Administrators &#40;Master Data Services&#41; (管理者 &#40;マスター データ サービス&#41;)](../master-data-services/administrators-master-data-services.md)」を参照してください。  
  
-   [バージョン管理] 機能領域にアクセスする権限が必要です。 詳細については、「[機能領域権限 (マスター データ サービス)](../master-data-services/functional-area-permissions-master-data-services.md)」を参照してください。  
  
### バージョン フラグを作成するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[バージョン管理]**をクリックします。  
  
2.  **[バージョンの管理]** ページのメニュー バーから **[管理]** をポイントして **[フラグ]** をクリックします。  
  
3.  **[バージョン フラグの管理]** ページの **[モデル]** フィールドから、フラグを作成するモデルを選択します。  
  
4.  **[追加]**をクリックします。  
  
5.  **[名前]** ボックスに名前を入力します。  
  
6.  **[説明]** ボックスに説明を入力します。  
  
7.  **[コミット済みのバージョンのみ]** フィールドで **[True]** を選択すると、フラグは **[コミット済み]** の状態のバージョンにのみ割り当てることができます。 **[False]** を選択すると、フラグは任意の状態のバージョンに割り当てることができます。  
  
8.  **[保存]**をクリックします。  
  
## 次の手順  
  
-   [バージョンにフラグを割り当てる (マスター データ サービス)](../master-data-services/assign-a-flag-to-a-version-master-data-services.md)  
  
## 参照  
 [バージョン (マスター データ サービス)](../master-data-services/versions-master-data-services.md)   
 [バージョン フラグ名を変更する (マスター データ サービス)](../master-data-services/change-a-version-flag-name-master-data-services.md)  
  
  
---
title: "ビジネス ルールに対してバージョンを検証する (マスター データ サービス) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- validating versions [Master Data Services]
- validating versions [Master Data Services], about validating versions
- versions [Master Data Services], validating
- business rules [Master Data Services], applying to all members
ms.assetid: 5aee7901-6d05-41d4-8bbb-c6f26791d1df
caps.latest.revision: 8
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: 2a31c8b91872276636addc25c673f07ba5b11bc7
ms.contentlocale: ja-jp
ms.lasthandoff: 09/07/2017

---
# <a name="validate-a-version-against-business-rules-master-data-services"></a>ビジネス ルールに対してバージョンを検証する (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、ビジネス ルールをモデル バージョンのすべてのメンバーに適用するためにバージョンが検証されます。  
  
 この手順では、 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web アプリケーションを使用してデータを検証する方法について説明します。 MDS データベースの権限がある場合は、代わりにストアド プロシージャを使用することができます。 詳細については、「 [検証ストアド プロシージャ (マスター データ サービス)](../master-data-services/validation-stored-procedure-master-data-services.md)」を参照してください。  
  
> [!NOTE]  
>  バージョンをコミットするには、すべてのメンバーが検証に合格する必要があります。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   **[バージョン管理]** 機能領域にアクセスする権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「[Administrators &#40;Master Data Services&#41; (管理者 &#40;マスター データ サービス&#41;)](../master-data-services/administrators-master-data-services.md)」を参照してください。  
  
-   バージョンの状態は、**[未処理]** または **[ロック済み]** である必要があります。  
  
-   **[バージョンの検証]** ページに **[検証成功]**以外の状態のメンバーが存在する必要があります。  
  
### <a name="to-validate-a-version"></a>バージョンを検証するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[バージョン管理]**をクリックします。  
  
2.  **[バージョンの管理]** ページのメニュー バーから **[バージョンの検証]**をクリックします。  
  
3.  **[バージョンの検証]** ページで、検証するモデルおよびバージョンを選択します。  
  
4.  **[検証]**をクリックします。  
  
5.  確認のダイアログ ボックスで **[OK]**をクリックします。  
  
    > [!NOTE]  
    >  バージョンの検証が完了すると、進行状況インジケーターが表示されなくなります。  
  
## <a name="next-steps"></a>次の手順  
  
-   [バージョンをロックする (マスター データ サービス)](../master-data-services/lock-a-version-master-data-services.md)  
  
## <a name="see-also"></a>参照  
 [検証状態 (マスター データ サービス)](../master-data-services/validation-statuses-master-data-services.md)   
 [検証ストアド プロシージャ (マスター データ サービス)](../master-data-services/validation-stored-procedure-master-data-services.md)   
 [バージョン (マスター データ サービス)](../master-data-services/versions-master-data-services.md)   
 [ビジネス ルール (マスター データ サービス)](../master-data-services/business-rules-master-data-services.md)   
 [ビジネス ルールに対して特定のメンバーを検証する (マスター データ サービス)](../master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
  

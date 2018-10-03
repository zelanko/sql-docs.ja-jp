---
title: Code 属性の値の自動生成 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
ms.assetid: 19b354ee-2906-4cc7-ba2f-32b4543bddcf
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 42887c9126014a1a1bd56217a915539306959275
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48207817"
---
# <a name="automatically-generate-code-attribute-values-master-data-services"></a>Code 属性の値の自動生成 (Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、新しいメンバーが作成されるたびにエンティティの Code 属性の値に整数を自動的に割り当てる場合は、Code 属性の値を自動的に生成します。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   **[システム管理]** 機能領域にアクセスする権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「[Administrators &#40;Master Data Services&#41; (管理者 &#40;マスター データ サービス&#41;)](administrators-master-data-services.md)」を参照してください。  
  
-   エンティティが存在する必要があります。 詳細については、「[エンティティを作成する (マスター データ サービス)](../../2014/master-data-services/create-an-entity-master-data-services.md)」を参照してください。  
  
### <a name="to-automatically-generate-code-values"></a>コード値を自動的に生成するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。  
  
2.  **モデル エクスプ ローラー**  ページで、ポイントして、メニュー バーから**管理** をクリック**エンティティ**します。  
  
3.  **[エンティティのメンテナンス]** ページの **[モデル]** ボックスの一覧からモデルを選択します。  
  
4.  コードを生成するエンティティの行を選択します。  
  
5.  **[選択したエンティティの編集]** をクリックします。  
  
6.  **[コード値を自動的に作成する]** チェック ボックスをオンにします。  
  
7.  **[開始]** ボックスに、増分を開始する値を入力します。 メンバーが既に存在する場合は、コードは既存の最も大きい値に基づいて設定されます。 たとえば、最も大きい既存のコード値が 299 の場合、次のメンバーのコード値は 300 に設定されます。  
  
8.  クリックして**エンティティの保存**します。  
  
## <a name="see-also"></a>参照  
 [コードの自動作成&#40;マスター データ サービス&#41;](../../2014/master-data-services/automatic-code-creation-master-data-services.md)   
 [Code 以外の属性の値を自動的に生成&#40;マスター データ サービス&#41;](../../2014/master-data-services/automatically-generate-attribute-values-other-than-code-master-data-services.md)  
  
  

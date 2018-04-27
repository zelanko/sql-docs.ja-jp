---
title: エンティティのトランザクション ログの種類の変更 (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: mds
ms.service: ''
ms.component: non-specific
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 75250b32-3384-43c2-9b5c-1607cc3aa7b3
caps.latest.revision: 10
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f80ca05b11b1ac9b77954b7a23267ce2fcfe6766
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="change-the-entity-transaction-log-type-master-data-services"></a>エンティティのトランザクション ログの種類の変更 (マスター データ サービス)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  エンティティのトランザクション ログの種類を、"属性"、"メンバー"、または "なし" に変更できます。  
  
|トランザクション ログの種類|Description|  
|--------------------------|-----------------|  
|属性|エンティティの変更ログは、属性レベルで保存されます。<br /><br /> トランザクション ログは、 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]の場合と同様に保存されます。|  
|メンバー|エンティティの変更ログは、行レベルで保存されます。<br /><br /> すべての属性の変更に対し、新しい行の更新がトリガーされます。<br /><br /> トランザクション ログの種類として "行" を使用している場合、エンティティは、緩やかに変化するディメンション タイプ 4 として保存されます。 タイプ 2 のサブスクリプション ビューとタイプ 4 の (履歴) サブスクリプション ビューがサポートされます。 詳細については、「[サブスクリプション ビュー形式 (マスター データ サービス)](../master-data-services/subscription-view-formats-master-data-services.md)」を参照してください。<br /><br /> より優れたパフォーマンスが得られます。|  
|なし|変更ログは保存されません。<br /><br /> 最適なパフォーマンスが得られます。|  
  
## <a name="prerequisites"></a>Prerequisites  
 この手順を実行するには  
  
-   [システム管理] 機能領域にアクセスする権限が必要です。詳細については、「[機能領域権限 (マスター データ サービス)](../master-data-services/functional-area-permissions-master-data-services.md)」を参照してください。  
  
-   モデル管理者である必要があります。 詳細については、「 [管理者 (マスター データ サービス)](../master-data-services/administrators-master-data-services.md)にアクセスすることなくグループに対してユーザーの追加または削除を行うことができます。  
  
-   エンティティが存在する必要があります。 詳細については、「[エンティティを作成する (マスター データ サービス)](../master-data-services/create-an-entity-master-data-services.md)」を参照してください。  
  
 **トランザクション ログの種類を変更するには**  
  
1.  マスター データ マネージャーで、 **[システム管理]** をクリックします。  
  
2.  **[モデルの管理]** ページで、編集するエンティティのモデルの行を選択し、 **[エンティティ]** をクリックします。  
  
3.  **[Manage Entity]** (エンティティの管理) ページで、更新するエンティティの行を選択し、 **[編集]** をクリックします。  
  
4.  ドロップダウン リストでトランザクション ログの種類を選択します。  
  
5.  **[保存]** をクリックします。  
  
  

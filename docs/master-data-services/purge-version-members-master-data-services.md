---
title: バージョン メンバーのパージ (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: adecce2d-46bb-49ff-8be9-0b31b8dd3cb6
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 571ac34ad836bf25ad98f973f9fc33c9de499ba9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68024655"
---
# <a name="purge-version-members-master-data-services"></a>バージョン メンバーのパージ (マスター データ サービス)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、メンバーを削除してもメンバーは非アクティブ化 (論理削除) されるだけです。 データはデータベースに残ります。 このトピックでは、モデル バージョンで論理削除されたすべてのメンバーをパージ (永続的に削除) する方法について説明します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 この手順を実行するには  
  
-   [バージョン管理] 機能領域にアクセスする権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「 [管理者 &#40;マスター データ サービス&#41;](../master-data-services/administrators-master-data-services.md)にアクセスすることなくグループに対してユーザーの追加または削除を行うことができます。  
  
## <a name="to-purge-soft-deleted-members"></a>論理削除されたメンバーをパージするには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[バージョン管理]** をクリックします。  
  
2.  **[バージョンの管理]** ページで、パージするバージョンのあるモデルを選択します。 モデル バージョンの一覧が表示されます。  
  
3.  パージするバージョンの行を選択します。  
  
4.  **[Purge Members]** (メンバーのパージ) をクリックします。  
  
5.  確認プロンプトで [OK] をクリックします。  
  
## <a name="additional-methods-to-purge-members"></a>メンバーをパージするための追加メソッド  
 バージョン メンバーをパージすると、選択したバージョンに関連するすべてのエンティティの論理削除されたメンバーが永続的に削除されます。 より細分化された代替手段としては、エンティティ ベースのステージングを使用してエンティティの特定のメンバーのみを永続的に削除します。 また、エクスプローラーの機能権限を持つエンティティ管理者は、エンティティ エクスプローラー ページ内のエンティティ バージョンをパージできます。  
  
 詳細については、「[リーフ メンバー ステージング テーブル (マスター データ サービス)](../master-data-services/leaf-member-staging-table-master-data-services.md)」を参照してください。  
  
  

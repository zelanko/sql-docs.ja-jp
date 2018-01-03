---
title: "明示的階層を作成する (マスター データ サービス) | Microsoft Docs"
ms.custom: 
ms.date: 04/01/2016
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: non-specific
ms.reviewer: 
ms.suite: sql
ms.technology: master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating explicit hierarchies [Master Data Services]
- explicit hierarchies, creating
ms.assetid: ba768393-6990-4eda-8cb0-d58cb3cfc2e2
caps.latest.revision: "10"
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9847fea6acc6fe9d32b94d2db3cb9a461d4d8923
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="create-an-explicit-hierarchy-master-data-services"></a>明示的階層を作成する (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で任意のレベルでメンバーが存在できる不規則階層が必要な場合、明示的階層を作成します。 明示的階層には、1 つのエンティティのメンバーが含まれています。  
  
 明示的階層を作成したら、 **[エクスプローラー]** 機能領域で明示的階層にメンバーを追加できます。  
  
## <a name="prerequisites"></a>Prerequisites  
 この手順を実行するには  
  
-   **[システム管理]** 機能領域にアクセスする権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「 [管理者 (マスター データ サービス)](../master-data-services/administrators-master-data-services.md)にアクセスすることなくグループに対してユーザーの追加または削除を行うことができます。  
  
-   エンティティは、明示的階層およびコレクションに対して有効化されている必要があります。  
  
### <a name="to-create-an-explicit-hierarchy"></a>明示的階層を作成するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]**をクリックします。  
  
2.  **[モデルの管理]** ページでグリッドからモデルを選択し、 **[エンティティ]**をクリックします。  
  
3.  **[Manage Entity]** (エンティティの管理) ページで、明示的階層を作成するエンティティの行をグリッドから選択します。  
  
4.  **[明示的階層]**をクリックします。  
  
5.  **[Manage Explicit Hierarchy]** (明示的階層の管理) ページで、 **[追加]**をクリックします。  
  
6.  **[名前]** ボックスに階層の名前を入力します。  
  
7.  必要に応じて、 **[必須階層]** チェック ボックスをオフにして、任意の階層として明示的階層を作成します。 階層の種類の詳細については、「 [明示的階層 (マスター データ サービス)](../master-data-services/explicit-hierarchies-master-data-services.md)」を参照してください。  
  
8.  **[保存]**をクリックします。  
  
## <a name="grid-columns"></a>グリッド列  
 作成する各明示的階層で、グリッドに 7 列の行が追加されます。 次に、各列について説明します。  
  
|[オブジェクト名]|Description|  
|----------|-----------------|  
|状態|エンティティの状態。 **[保存]** をクリックすると、エンティティが更新中であることを示す次のイメージが表示されます。<br /><br /> ![更新中状態のアイコン](../master-data-services/media/mds-statusicon-updating.png "更新中状態のアイコン")<br /><br /> エンティティの作成または編集中にエラーが発生すると、次のイメージが表示されます。<br /><br /> ![エラー状態のアイコン](../master-data-services/media/mds-statusicon-error.png "エラー状態のアイコン")<br /><br /> 適切な状態の場合は、次のイメージが表示されます。<br /><br /> ![適切な状態のアイコン](../master-data-services/media/mds-statusicon-ok.png "適切な状態のアイコン")|  
|[オブジェクト名]|明示的階層の名前。|  
|必須|明示的階層が必須かどうかを指定します。|  
|[作成者]|明示的階層を作成したユーザーの名前。|  
|作成日|明示的階層が作成された日時。|  
|更新者|明示的階層を更新したユーザーの名前。|  
|更新日|明示的階層が最後に更新された日時。|  
  
## <a name="next-steps"></a>Next Steps  
  
-   [統合メンバーを作成する (マスター データ サービス)](../master-data-services/create-a-consolidated-member-master-data-services.md)  
  
  
  
## <a name="see-also"></a>参照  
 [明示的階層 (マスター データ サービス)](../master-data-services/explicit-hierarchies-master-data-services.md)   
 [明示的なキャップを持つ派生階層 &#40;マスター データ サービス&#41;](../master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md)   
 [明示的階層名を変更する (マスター データ サービス)](../master-data-services/change-an-explicit-hierarchy-name-master-data-services.md)  
  
  


---
title: "SSMS (SSAS テーブル) を使用してロールの管理 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 652faac0-1cfc-438b-8119-2f4b090a2381
caps.latest.revision: 10
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c7458aa948c023e073f3080116fed980e8571c78
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="manage-roles-by-using-ssms-ssas-tabular"></a>SSMS を使用したロールの管理 (SSAS テーブル)
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用して、配置したテーブル モデルのロールの作成、編集、および管理を行うことができます。  
  
 このトピックのタスク:  
  
-   [新しいロールを作成するには](#bkmk_new_role)  
  
-   [ロールをコピーするには](#bkmk_copy_role)  
  
-   [ロールを編集するには](#bkmk_edit_role)  
  
-   [ロールを削除するには](#bkmk_deletet_role)  
  
> [!CAUTION]  
>  [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] のロール マネージャーを使用して定義済みロールを含むテーブル モデル プロジェクトを再配置すると、配置済みテーブル モデルに定義されたロールが上書きされます。  
  
> [!CAUTION]  
>  モデル プロジェクトが [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で開いているときに、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] を使用してテーブル モデル ワークスペース データベースを管理すると、Model.bim ファイルが破損することがあります。 テーブル モデル ワークスペース データベースのロールを作成および管理するときは、 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]のロール マネージャーを使用してください。  
  
###  <a name="bkmk_new_role"></a> 新しいロールを作成するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、新しいロールを作成するテーブル モデル データベースを展開し、 **[ロール]**を右クリックしてから **[新しいロール]**をクリックします。  
  
2.  **[ロールの作成]** ダイアログ ボックスの [ページの選択] ウィンドウで **[全般]**をクリックします。  
  
3.  全般設定のウィンドウの **[名前]** フィールドにロールの名前を入力します。  
  
     既定では、既定ロールの名前に番号が付き、新しいロールを作成するたびにその番号が増加します。 Finance Managers や Human Resources Specialists など、メンバーの種類を明確に特定する名前を付けることをお勧めします。  
  
4.  **[このロールにデータベースの権限を設定します]**で、次の権限オプションのいずれかを選択します。  
  
    |権限|Description|  
    |----------------|-----------------|  
    |**[フル コントロール (管理者)]**|メンバーは、モデル スキーマを変更したり、すべてのデータを表示したりできます。|  
    |**[データベースの処理]**|メンバーは、処理およびすべて処理の各操作を実行できます。 モデル スキーマを変更することはできませんし、データを表示することもできません。|  
    |**読み取り**|メンバーは、データを表示できますが (行フィルターに従って)、モデル スキーマを変更することはできません。|  
  
5.  **[ロールの作成]** ダイアログ ボックスの [ページの選択] ウィンドウで **[メンバーシップ]**をクリックします。  
  
6.  メンバーシップ設定ウィンドウで **[追加]**をクリックし、 **[ユーザーまたはグループの選択]** ダイアログ ボックスで、メンバーとして追加する Windows ユーザーまたはグループを選択します。  
  
7.  作成しているロールに読み取り権限がある場合、DAX 数式を使用してテーブルに行フィルターを追加できます。 行フィルターを追加する、**ロールのプロパティ - \<rolename >**ダイアログ ボックスで、**ページの選択**、をクリックして**行フィルター**です。  
  
8.  行フィルター ウィンドウで、テーブルを選択し、をクリックして、 **DAX フィルター**フィールド、し、 **DAX フィルター - \<tablename >**フィールドに、DAX の数式を入力します。  
  
    > [!NOTE]  
    >  DAX フィルター - \<tablename > フィールドが、AutoComplete クエリ エディターを含むまたは関数挿入機能していません。 DAX 数式を作成するときにオートコンプリート機能を使用するには、 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]の DAX 数式エディターを使用する必要があります。  
  
9. **[OK]** をクリックして、ロールを保存します。  
  
###  <a name="bkmk_copy_role"></a> ロールをコピーするには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、コピーするロールを含むテーブル モデル データベースを展開し、 **[ロール]**を展開してから、ロールを右クリックして **[複製]**をクリックします。  
  
###  <a name="bkmk_edit_role"></a> ロールを編集するには  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、編集するロールを含むテーブル モデル データベースを展開し、 **[ロール]**を展開してから、ロールを右クリックして **[プロパティ]**をクリックします。  
  
     **ロール プロパティ** \<rolename > ダイアログ ボックスで、アクセス許可を変更、追加するか、メンバーを削除および追加/編集行フィルターします。  
  
###  <a name="bkmk_deletet_role"></a> ロールを削除するには  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、削除するロールを含むテーブル モデル データベースを展開し、 **[ロール]**を展開してから、ロールを右クリックして **[削除]**をクリックします。  
  
## <a name="see-also"></a>参照  
 [ロール (SSAS テーブル)](../../analysis-services/tabular-models/roles-ssas-tabular.md)  
  
  


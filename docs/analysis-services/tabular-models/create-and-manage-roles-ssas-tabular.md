---
title: 作成し、Analysis Services 表形式モデルでロールの管理 |Microsoft Docs
ms.date: 09/17/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 093197db8257cf9be261658f1828783fa01d7cc2
ms.sourcegitcommit: 8a64c59c5d84150659a015e54f8937673cab87a0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2018
ms.locfileid: "53072219"
---
# <a name="create-and-manage-roles"></a>作成し、ロールの管理 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  テーブル モデルでは、ロールはあるモデルのメンバー アクセス許可を定義します。 モデル プロジェクトのロールは、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]の [ロール マネージャー] ダイアログ ボックスを使用して定義します。 

> [!IMPORTANT]
> Azure Analysis Services にプロジェクトをデプロイする場合は、使用**統合ワークスペース**ワークスペース データベースとします。 詳細についてを参照してください。[ワークスペース データベース](workspace-database-ssas-tabular.md)します。
  
 この記事のタスクを作成し、ロール マネージャー ダイアログ ボックスを使用してモデルの作成時にロールを管理する方法を説明する[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]します。 配置済みモデル データベース内のロールを管理する方法の詳細については、次を参照してください。[テーブル モデル ロール](../../analysis-services/tabular-models/tabular-model-roles-ssas-tabular.md)します。  
  
## <a name="tasks"></a>処理手順  
 ロールの作成、編集、コピー、削除の各操作を実行するには、 **[ロール マネージャー]** ダイアログ ボックスを使用します。 **[ロール マネージャー]** ダイアログ ボックスを表示するには、 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]の **[モデル]** メニューをクリックし、 **[ロール マネージャー]** をクリックします。  
  
###  <a name="bkmk_new_role"></a> 新しいロールを作成するには  
  
1.  [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]で、 **[モデル]** メニューをクリックし、 **[ロール マネージャー]** をクリックします。  
  
2.  **[ロール マネージャー]** ダイアログ ボックスで **[新規]** をクリックします。  
  
     新しいロールが [ロール] リストに追加され、強調表示されます。  
  
3.  **[ロール]** リストの **[名前]** フィールドに、ロールの名前を入力します。  
  
     既定では、既定ロールの名前に番号が付き、新しいロールを作成するたびにその番号が増加します。 Finance Managers や Human Resources Specialists など、メンバーの種類を明確に特定する名前を付けることをお勧めします。  
  
4.  **[権限]** フィールドで下矢印をクリックしてから、次の権限の種類から 1 つを選択します。  
  
    |権限|説明|  
    |----------------|-----------------|  
    |**None**|メンバーは、モデル スキーマを変更したり、データをクエリしたりすることはできません。|  
    |**読み取り**|メンバーは、(行フィルターに基づいて) データをクエリできますが、モデル スキーマを変更することはできません。|  
    |**読み取りと処理**|メンバーは、(行レベル フィルターに基づいて) データをクエリでき、処理およびすべて処理の各操作も実行できますが、モデル スキーマを変更することはできません。|  
    |**[処理]**|メンバーは、処理およびすべて処理の各操作を実行できます。 モデル スキーマを変更することはできませんし、データをクエリすることもできません。|  
    |**管理者**|メンバーは、モデル スキーマを変更したり、すべてのデータをクエリしたりできます。|  
  
5.  ロールの説明を入力するには、 **[説明]** フィールドをクリックして説明を入力します。  
  
6.  作成しているロールに読み取りまたは読み取りと処理の権限がある場合、DAX 式を使用して行フィルターを追加できます。 行フィルターを追加するには、 **[行フィルター]** タブをクリックし、テーブルを選択してから、 **[DAX フィルター]** フィールドをクリックし、DAX 式を入力します。  
  
7.  このロールにメンバーを追加するには、 **[メンバー]** タブをクリックし、 **[追加]** をクリックします。  
  
    > [!NOTE]  
    >  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用して、配置済みモデルにロール メンバーを追加することもできます。 詳細については、次を参照してください。 [SSMS を使用してロールの管理](../../analysis-services/tabular-models/manage-roles-by-using-ssms-ssas-tabular.md)します。  
  
8.  **[ユーザーまたはグループの選択]** ダイアログ ボックスで、メンバーとして Windows ユーザーまたは Windows グループ オブジェクトを入力します。  
  
9. **[OK]** をクリックします。  
  
## <a name="see-also"></a>関連項目  
 [ロール](../../analysis-services/tabular-models/roles-ssas-tabular.md)   
 [パースペクティブ](../../analysis-services/tabular-models/perspectives-ssas-tabular.md)   
 [[Excel で分析]](../../analysis-services/tabular-models/analyze-in-excel-ssas-tabular.md)   
 [USERNAME 関数 (DAX)](http://msdn.microsoft.com/22dddc4b-1648-4c89-8c93-f1151162b93f)   
 [CUSTOMDATA 関数 (DAX)](http://msdn.microsoft.com/58235ad8-226c-43cc-8a69-5a52ac19dd4e)  
  
  

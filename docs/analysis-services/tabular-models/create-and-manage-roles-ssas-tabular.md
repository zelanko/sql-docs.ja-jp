---
title: 作成し、ロールの管理 |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/22/2018
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.asvs.bidtoolset.rolemanager.f1
- sql13.asvs.bidtoolset.roledb.f1
ms.assetid: e23d27a8-e968-4082-9dbe-963fc724b5d9
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 788e0cab02a0b3931c0c8a702989366983e33b65
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="create-and-manage-roles"></a>作成し、ロールの管理 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  テーブル モデルでは、ロールはあるモデルのメンバー アクセス許可を定義します。 モデル プロジェクトのロールは、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]の [ロール マネージャー] ダイアログ ボックスを使用して定義します。 モデルが配置されると、データベース管理者は [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用してロールを管理することができます。  
  
 この記事でタスクを作成し、[ロール マネージャー] ダイアログ ボックスを使用して、モデルの作成時にロールを管理する方法について説明[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]です。 配置済みモデル データベースでロールを管理する方法の詳細については、次を参照してください。[表形式モデル ロール](../../analysis-services/tabular-models/tabular-model-roles-ssas-tabular.md)です。  
  
## <a name="tasks"></a>処理手順  
 ロールの作成、編集、コピー、削除の各操作を実行するには、 **[ロール マネージャー]** ダイアログ ボックスを使用します。 **[ロール マネージャー]** ダイアログ ボックスを表示するには、 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]の **[モデル]** メニューをクリックし、 **[ロール マネージャー]** をクリックします。  
  
###  <a name="bkmk_new_role"></a> 新しいロールを作成するには  
  
1.  [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]で、 **[モデル]** メニューをクリックし、 **[ロール マネージャー]** をクリックします。  
  
2.  **[ロール マネージャー]** ダイアログ ボックスで **[新規]** をクリックします。  
  
     新しいロールが [ロール] リストに追加され、強調表示されます。  
  
3.  **[ロール]** リストの **[名前]** フィールドに、ロールの名前を入力します。  
  
     既定では、既定ロールの名前に番号が付き、新しいロールを作成するたびにその番号が増加します。 Finance Managers や Human Resources Specialists など、メンバーの種類を明確に特定する名前を付けることをお勧めします。  
  
4.  **[権限]** フィールドで下矢印をクリックしてから、次の権限の種類から 1 つを選択します。  
  
    |権限|Description|  
    |----------------|-----------------|  
    |**なし**|メンバーは、モデル スキーマを変更したり、データをクエリしたりすることはできません。|  
    |**読み取り**|メンバーは、(行フィルターに基づいて) データをクエリできますが、モデル スキーマを変更することはできません。|  
    |**読み取りと処理**|メンバーは、(行レベル フィルターに基づいて) データをクエリでき、処理およびすべて処理の各操作も実行できますが、モデル スキーマを変更することはできません。|  
    |**[処理]**|メンバーは、処理およびすべて処理の各操作を実行できます。 モデル スキーマを変更することはできませんし、データをクエリすることもできません。|  
    |**管理者**|メンバーは、モデル スキーマを変更したり、すべてのデータをクエリしたりできます。|  
  
5.  ロールの説明を入力するには、 **[説明]** フィールドをクリックして説明を入力します。  
  
6.  作成しているロールに読み取りまたは読み取りと処理の権限がある場合、DAX 式を使用して行フィルターを追加できます。 行フィルターを追加するには、 **[行フィルター]** タブをクリックし、テーブルを選択してから、 **[DAX フィルター]** フィールドをクリックし、DAX 式を入力します。  
  
7.  このロールにメンバーを追加するには、 **[メンバー]** タブをクリックし、 **[追加]** をクリックします。  
  
    > [!NOTE]  
    >  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用して、配置済みモデルにロール メンバーを追加することもできます。 詳細については、次を参照してください。 [SSMS を使用してロールの管理](../../analysis-services/tabular-models/manage-roles-by-using-ssms-ssas-tabular.md)です。  
  
8.  **[ユーザーまたはグループの選択]** ダイアログ ボックスで、メンバーとして Windows ユーザーまたは Windows グループ オブジェクトを入力します。  
  
9. **[OK]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [ロール](../../analysis-services/tabular-models/roles-ssas-tabular.md)   
 [パースペクティブ](../../analysis-services/tabular-models/perspectives-ssas-tabular.md)   
 [Excel で分析します。](../../analysis-services/tabular-models/analyze-in-excel-ssas-tabular.md)   
 [USERNAME 関数 (DAX)](http://msdn.microsoft.com/en-us/22dddc4b-1648-4c89-8c93-f1151162b93f)   
 [CUSTOMDATA 関数 (DAX)](http://msdn.microsoft.com/en-us/58235ad8-226c-43cc-8a69-5a52ac19dd4e)  
  
  

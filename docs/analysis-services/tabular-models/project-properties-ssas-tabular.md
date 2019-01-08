---
title: Analysis Services 表形式モデル プロジェクトのプロパティ |Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b695f847ec7f99366e71e76aefe5aecb99cf5933
ms.sourcegitcommit: 8a64c59c5d84150659a015e54f8937673cab87a0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2018
ms.locfileid: "53072659"
---
# <a name="project-properties"></a>プロジェクト プロパティ 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  この記事では、モデル プロジェクトのプロパティについて説明します。 各テーブル モデル プロジェクトには、プロジェクトとモデルの配置方法を指定する配置オプションおよび配置サーバーのプロパティがあります。 たとえば、モデルの配置先のサーバーや配置されるモデル データベースの名前です。 これらの設定は、モデル プロパティとは異なります。モデル プロパティは、モデル ワークスペース データベースに対する設定です。 ここで説明するプロジェクト プロパティは、他の種類のプロパティを表示するために使用されるプロパティ ウィンドウとは異なり、モーダル プロパティ ダイアログ ボックスに表示されます。 モーダル プロジェクト プロパティを表示するには、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]の **ソリューション エクスプローラー**で、プロジェクトを右クリックして、 **[プロパティ]** をクリックします。  
  
 このトピックのセクション:  
  
-   [プロジェクトのプロパティ](#bkmk_proj_properties)  
  
-   [配置オプションおよび配置サーバー プロパティの設定を構成する](#bkmk_conf_proj_settings)  
  
##  <a name="bkmk_proj_properties"></a> プロジェクトのプロパティ  
 **配置オプション**  
  
|プロパティ|既定の設定|説明|  
|--------------|---------------------|-----------------|  
|**[処理オプション]**|**Default**|既定では、オブジェクトの変更を配置するときに Analysis Services で必要な処理方法が決定されます。 通常は、これで配置時間が最速になりますが、 配置のたびに完全処理を実行するか処理を実行しないかを選択することもできます。|  
|**トランザクション配置**|**False**|モデルの配置がトランザクションかどうかを指定します。 既定では、すべてのオブジェクトまたは変更されたオブジェクトの配置は、それらを配置した後の処理とトランザクション関係がありません。 処理に失敗しても、配置は成功して持続できます。 これを変更して、配置と処理を 1 つのトランザクションに組み込むこともできます。|  
|**クエリ モード**|**In-Memory**|クエリ結果を返すソースを指定します。 詳細については、次を参照してください。 [DirectQuery モード](../../analysis-services/tabular-models/directquery-mode-ssas-tabular.md)します。|  
  
 **配置サーバー**  
  
|プロパティ|既定の設定|説明|  
|--------------|---------------------|-----------------|  
|**[サーバー]**|**localhost**|Analysis Services のインスタンスを指定します。 既定では、モデルは、ローカル コンピューター上の Analysis Services の既定のインスタンスに配置されます。 この設定を変更して、ローカル コンピューター上の名前付きインスタンスや、Analysis Services オブジェクトを作成する権限のあるリモート コンピューター上の任意のインスタンスを指定できます。 通常は、管理者権限です。<br /><br /> このプロパティの既定の設定は、[ツール] メニューから開く [オプション] ダイアログ ボックスで分析サーバーの設定の [配置] ページの既定の配置サーバー プロパティを使用して変更できます。 詳細については、次を参照してください。[既定のデータ モデリングとデプロイのプロパティを構成する](../../analysis-services/tabular-models/configure-default-data-modeling-and-deployment-properties-ssas-tabular.md)します。|  
|**のエディション**|**開発者**|モデルを配置する Analysis Services サーバーのエディションを指定します。 サーバー エディションにより、プロジェクトに組み込むことができるさまざまな機能が定義されます。|  
|**[データベース]**|**[モデル]**|配置時にモデル オブジェクトがインスタンス化される Analysis Services データベースの名前を指定します。 この名前は、データ接続や .rsds データ接続ファイルに指定されます。 モデルを使用して実行される分析の種類を反映した名前 (AdventureWorksSalesModel など) を指定することをお勧めします。<br /><br /> 配置済みのモデルの名前が重複しないようにするために、モデルの目的を反映するように **[データベース]** プロパティ名の設定を変更します。 ユーザーがデータ ソースとしてモデルに接続するときに、この名前が表示されます。|  
|**[キューブ名]**|**[モデル]**|レポートのクライアント データ接続に表示されるデータベース キューブの名前を指定します。|  
|**バージョン**|**13.0**|プロジェクトの配置先となる Analysis Services インスタンスのバージョンです。|  
  
 **DirectQuery オプション**  
  
|プロパティ|既定の設定|説明|  
|--------------|---------------------|-----------------|  
|**権限借用設定**|**Default**|DirectQuery モードで実行されているモデルのデータ ソースへの接続に使用する資格情報を指定します。 これらの資格情報は、既定の In-Memory モードで使用される権限借用の資格情報とは異なります。 詳細については、次を参照してください。[偽装](../../analysis-services/tabular-models/impersonation-ssas-tabular.md)します。|  
  
##  <a name="bkmk_conf_proj_settings"></a> 配置オプションおよび配置サーバー プロパティの設定を構成する  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]の **ソリューション エクスプローラー**で、プロジェクトを右クリックし、 **[プロパティ]** をクリックします。  
  
2.  **[プロパティ]** ウィンドウでプロパティをクリックし、値を入力するか、下矢印をクリックして、設定オプションを選択します。  
  
## <a name="see-also"></a>参照  
 [既定のデータ モデリングとデプロイのプロパティを構成します。](../../analysis-services/tabular-models/configure-default-data-modeling-and-deployment-properties-ssas-tabular.md)   
 [モデルのプロパティ](../../analysis-services/tabular-models/model-properties-ssas-tabular.md)   
 [テーブル モデル ソリューションの配置](../../analysis-services/tabular-models/tabular-model-solution-deployment-ssas-tabular.md)  
  
  

---
title: SQL Server Data Tools から Analysis Services 表形式モデルのデプロイ |Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 09d859cf8b5c372b9588266b9210837012396ea6
ms.sourcegitcommit: 8a64c59c5d84150659a015e54f8937673cab87a0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2018
ms.locfileid: "53072139"
---
# <a name="deploy-from-sql-server-data-tools"></a>SQL Server データ ツールからの配置
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  このトピックのタスクを使用して、SSDT で Deploy コマンドを使用して、表形式モデル ソリューションをデプロイします。  
  
##  <a name="bkmk_deploy"></a> 配置オプションおよび配置サーバー プロパティの構成  
 テーブル モデル ソリューションを配置する前に、まず、配置オプションと配置サーバーのプロパティを指定する必要があります。 展開のプロパティおよび設定に関する詳細については、次を参照してください。[表形式モデル ソリューションの配置](../../analysis-services/tabular-models/tabular-model-solution-deployment-ssas-tabular.md)します。  
  
#### <a name="to-configure-options-and-properties"></a>オプションとプロパティを構成するには  
  
1.  SSDT での**ソリューション エクスプ ローラー**プロジェクト名を右クリックし、クリックして**プロパティ**します。  
  
2.  **\<プロジェクト名 > プロパティ**ダイアログで、**展開オプション**既定の設定と異なる場合は、プロパティの設定を指定します。  
  
    > [!NOTE]  
    >  キャッシュ モードのモデルの場合、 **[クエリ モード]** は常に **[In-Memory]** です。  
  
    > [!NOTE]  
    >  DirectQuery モードのモデルの場合、 **[権限借用設定]** は指定できません。  
  
3.  **[配置サーバー]** で、 **[サーバー]** (名前)、 **[エディション]**、 **[データベース]** (名前)、 **[キューブ名]** の各プロパティの設定を指定し (既定の設定と異なる場合)、 **[OK]** をクリックします。  
  
> [!NOTE]  
>  作成した新しいプロジェクトが指定したサーバーに自動的に配置されるように、既定の配置サーバー プロパティの設定を指定することもできます。 詳細については、次を参照してください。[既定のデータ モデリングとデプロイのプロパティを構成する](../../analysis-services/tabular-models/configure-default-data-modeling-and-deployment-properties-ssas-tabular.md)します。  
  
##  <a name="bkmk_deploy_proc"></a> 表形式モデルをデプロイします。  
  
#### <a name="to-deploy-a-tabular-model"></a>表形式モデルをデプロイするには
  
-   SSDT での**ビルド** メニューのをクリックして**デプロイ\<プロジェクト名 >** します。  
  
     **[配置]** ダイアログ ボックスが表示され、メタデータの配置の状態とモデルに含まれる各テーブルの処理が示されます ([処理オプション] プロパティが [処理しない] に設定されている場合を除きます)。 展開プロセスが完了したら、SSMS を使用して、Analysis Services インスタンスに接続し、新しい model データベース オブジェクトが作成されていることを確認するまたはレポート作成、デプロイされたモデルに接続するアプリケーションのクライアントを使用します。  
  
##  <a name="bkmk_deploy_status"></a> 配置状態  
 **[配置]** ダイアログ ボックスでは、配置操作の進行状況を監視できます。 配置操作を停止することもできます。  
  
 **ステータス**  
 配置操作が正常に行われたかどうかを示します。  
  
 **詳細**  
 配置されたメタデータ項目と各メタデータ項目の状態を一覧表示し、何か問題があればメッセージを表示します。  
  
 **[展開の停止]**  
 クリックすると、配置操作が停止されます。 このオプションは、配置操作に時間がかかりすぎる場合や、エラーが多すぎる場合に有効です。  
  
## <a name="see-also"></a>関連項目  
 [表形式モデル ソリューションの配置](../../analysis-services/tabular-models/tabular-model-solution-deployment-ssas-tabular.md)   
 [既定のデータ モデルと配置プロパティの構成](../../analysis-services/tabular-models/configure-default-data-modeling-and-deployment-properties-ssas-tabular.md)  
  
  

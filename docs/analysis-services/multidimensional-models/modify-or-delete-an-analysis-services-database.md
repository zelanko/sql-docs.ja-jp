---
title: 変更または Analysis Services データベースの削除 |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3bd513e509b4c0ca51f7815cad3a284abc103373
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="modify-or-delete-an-analysis-services-database"></a>Analysis Services データベースの変更または削除
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースの名前と説明は、配置前には [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] で、配置後には [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で変更できます。 また、環境に応じて [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースの追加の設定を調整することもできます。  
  
> [!NOTE]  
>  オンライン モードで [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] を使用して、データベースのプロパティを変更することはできません。  
  
## <a name="modifying-databases-using-sql-server-management-studio"></a>SQL Server Management Studio を使用したデータベースの変更  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースの配置後は、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、データベース内のデータ ソースに接続するときに [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で使用される権限借用モードを変更できます。 権限借用モードを使用すると、処理、参照、またはドリルスルーの目的でデータ ソースに接続するときに [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で使用されるセキュリティ コンテキストを指定できます。  
  
## <a name="modifying-databases-using-sql-server-data-tools"></a>SQL Server データ ツールを使用したデータベースの変更  
 プロジェクト モードで [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] を使用すると、データベースの定義に使用する [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトのキャプションや説明の翻訳を変更できます。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースでの翻訳の使用方法については、「 [Analysis Services のグローバリゼーションのシナリオ](../../analysis-services/globalization-scenarios-for-analysis-services.md)」をご覧ください。  
  
 データベースに含まれているディメンションの勘定科目属性で使用される勘定科目の種類に関連付けられている別名や集計関数を設定することもできます。 別名を使用すると、勘定科目一覧表の勘定科目の種類に対して組織が使用するビジネス固有の用語を選択できます。 勘定科目属性のメンバーは、勘定科目の種類を使用して、各メンバーのメジャーを集計する方法を示します。集計は、データベース内の各勘定科目の種類に指定されている集計関数を使用して行います。 勘定科目属性の詳細については、「 [属性と属性階層](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)」をご覧ください。  
  
## <a name="deleting-databases"></a>消去、データベース  
 既存の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースを削除すると、データベースとすべてのキューブ、ディメンション、およびデータベース内のマイニング モデルが削除されます。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、既存の [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]データベースのみを削除できます。  
  
#### <a name="to-delete-an-analysis-services-database"></a>Analysis Services データベースを削除するには  
  
1.  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスに接続します。  
  
2.  **オブジェクト エクスプローラー**で、接続した [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスのノードを展開し、削除するオブジェクトを表示します。  
  
3.  削除するオブジェクトを右クリックし、 **[削除]** をクリックします。  
  
4.  **[オブジェクトの削除]** ダイアログ ボックスで **[OK]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [ドキュメントし、Analysis Services データベースをスクリプトの実行](../../analysis-services/multidimensional-models/document-and-script-an-analysis-services-database.md)  
  
  

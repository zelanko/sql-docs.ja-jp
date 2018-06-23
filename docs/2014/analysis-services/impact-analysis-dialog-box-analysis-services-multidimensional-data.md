---
title: 影響分析 ダイアログ ボックス (Analysis Services - 多次元データ) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.process.impactanalysisdialog.f1
ms.assetid: 208268eb-4e14-44db-9c64-6f74b776adb6
caps.latest.revision: 19
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: da3a687a637dee6b3b9df59eecebf957f06e64be
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36070576"
---
# <a name="impact-analysis-dialog-box-analysis-services---multidimensional-data"></a>[影響分析] ダイアログ ボックス (Analysis Services - 多次元データ)
  **および** の [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] [影響分析] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ダイアログ ボックスを使用すると、 **[処理]** ダイアログ ボックスに一覧表示されているオブジェクトが処理された場合に影響を受ける依存オブジェクトを特定し、必要に応じて処理できます。 **[影響分析]** ダイアログ ボックスを表示するには、 **[処理]** ダイアログ ボックスの **[影響分析]** をクリックします。  
  
> [!NOTE]  
>  オブジェクトが複数回にわたって影響を受ける場合は、そのオブジェクトが複数回表示されます。  
  
## <a name="options"></a>および  
 **[オブジェクト一覧]**  
 依存オブジェクトの一覧をグリッドに表示します。 このグリッドには次の列が含まれています。  
  
 **[オブジェクト名]**  
 処理する必要がある可能性がある依存オブジェクトの名前を表示します。 名前の左にあるアイコンはオブジェクトの種類を示しています。  
  
 **Type**  
 処理する必要がある可能性がある依存オブジェクトの種類を表示します。  
  
 **影響の種類**  
 **[処理]** ダイアログ ボックスに表示されているオブジェクトを処理することによって依存オブジェクトに与える影響を表示します。 次の表に、処理の影響と、その結果として警告またはエラーのどちらが生成されるかどうかを示します。  
  
|影響|メッセージ|  
|------------|-------------|  
|オブジェクトがクリアされます (処理されません)。|警告|  
|オブジェクトが無効になります。|[エラー]|  
|集計が削除されます。|警告|  
|柔軟な集計が削除されます。|警告|  
|インデックスが削除されます。|警告|  
|子オブジェクトでないオブジェクトが処理されます。|警告|  
  
 **プロセス オブジェクト**  
 処理操作の対象となる依存オブジェクトを選択します。 選択されていない依存オブジェクトは、処理操作が完了した後に処理する必要があります。 処理しないと、それらのオブジェクトは使用できません。  
  
## <a name="see-also"></a>参照  
 [Analysis Services のデザイナーおよびダイアログ ボックス&#40;多次元データ&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [処理 ダイアログ ボックス&#40;Analysis Services - 多次元データ&#41;](process-dialog-box-analysis-services-multidimensional-data.md)  
  
  
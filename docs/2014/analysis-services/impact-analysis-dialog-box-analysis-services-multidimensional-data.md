---
title: '[影響分析] ダイアログボックス (Analysis Services-多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.process.impactanalysisdialog.f1
ms.assetid: 208268eb-4e14-44db-9c64-6f74b776adb6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0c08690cd2f5b77471392cab3aad1587b4cb0f9a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66080751"
---
# <a name="impact-analysis-dialog-box-analysis-services---multidimensional-data"></a>[影響分析] ダイアログ ボックス (Analysis Services - 多次元データ)
  **および** の [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] [影響分析] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ダイアログ ボックスを使用すると、 **[処理]** ダイアログ ボックスに一覧表示されているオブジェクトが処理された場合に影響を受ける依存オブジェクトを特定し、必要に応じて処理できます。 **[影響分析]** ダイアログ ボックスを表示するには、 **[処理]** ダイアログ ボックスの **[影響分析]** をクリックします。  
  
> [!NOTE]  
>  オブジェクトが複数回にわたって影響を受ける場合は、そのオブジェクトが複数回表示されます。  
  
## <a name="options"></a>オプション  
 **オブジェクトの一覧**  
 依存オブジェクトの一覧をグリッドに表示します。 このグリッドには次の列が含まれています。  
  
 **オブジェクト名**  
 処理する必要がある可能性がある依存オブジェクトの名前を表示します。 名前の左にあるアイコンはオブジェクトの種類を示しています。  
  
 **Type**  
 処理する必要がある可能性がある依存オブジェクトの種類を表示します。  
  
 **[影響の種類]**  
 **[処理]** ダイアログ ボックスに表示されているオブジェクトを処理することによって依存オブジェクトに与える影響を表示します。 次の表に、処理の影響と、その結果として警告またはエラーのどちらが生成されるかどうかを示します。  
  
|影響|Message|  
|------------|-------------|  
|オブジェクトがクリアされます (処理されません)。|警告|  
|オブジェクトが無効になります。|Error|  
|集計が削除されます。|警告|  
|柔軟な集計が削除されます。|警告|  
|インデックスが削除されます。|警告|  
|子オブジェクトでないオブジェクトが処理されます。|警告|  
  
 **[オブジェクトの処理]**  
 処理操作の対象となる依存オブジェクトを選択します。 選択されていない依存オブジェクトは、処理操作が完了した後に処理する必要があります。 処理しないと、それらのオブジェクトは使用できません。  
  
## <a name="see-also"></a>参照  
 [多次元データ &#40;Analysis Services のデザイナーとダイアログボックス&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [[処理] ダイアログボックス &#40;Analysis Services-多次元データ&#41;](process-dialog-box-analysis-services-multidimensional-data.md)  
  
  

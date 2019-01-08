---
title: 属性の KeyColumn プロパティの変更 |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4415c5dba3382e636488ac94408f163c8e54dc6f
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2018
ms.locfileid: "52539022"
---
# <a name="attribute-properties---modify-the-keycolumn-property"></a>属性のプロパティ - KeyColumn プロパティを変更する
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  属性の **KeyColumns** プロパティは変更できます。 たとえば、単一キーではなく複合キーをその属性のキーとして指定する場合があります。  
  
### <a name="to-modify-the-keycolumns-property-of-an-attribute"></a>属性の KeyColumns プロパティを変更するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、 **KeyColumns** プロパティを変更するプロジェクトを開きます。  
  
2.  次のいずれかの手順を実行して、ディメンション デザイナーを開きます。  
  
    -   **ソリューション エクスプローラー**では、 **[ディメンション]** フォルダー内のディメンションを右クリックし、 **[開く]** または **[デザイナーの表示]** をクリックします。  
  
         - または -  
  
    -   キューブ デザイナーの上、**キューブ構造** タブで、キューブ ディメンションを展開し、**ディメンション**ウィンドウをクリックします**編集\<ディメンション >**。  
  
3.  **[ディメンション構造]** タブの **[属性]** ペインで、変更する **KeyColumns** プロパティを含む属性をクリックします。  
  
4.  **[プロパティ]** ウィンドウで、 **KeyColumns** プロパティの値をクリックします。  
  
5.  プロパティ ボックスの値のセルに表示される参照ボタン ( **[...]** ) をクリックします。  
  
     **[キー列]** ダイアログ ボックスが表示されます。  
  
6.  既存のキー列を削除するには、**[キー列]** の一覧で列を選択し、**[\<]** をクリックします。  
  
7.  キー列を追加するには、**[使用できる列]** の一覧で列を選択し、**[>]** をクリックします。  
  
    > [!NOTE]  
    >  複数のキー列を定義する場合、**[キー列]** の一覧での列の順序が表示順序に影響します。 たとえば、Month 属性には、月および年という 2 つのキー列があります。 一覧で年の列が月の列よりも前に表示される場合は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] により、まず年順に並べ替えられ、続いて月順に並べ替えられます。 月の列が年の列よりも前に表示される場合は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] により、まず月順に並べ替えられ、続いて年順に並べ替えられます。  
  
8.  キー列の順序を変更するには、列を選択し、 **[上へ]** または **[下へ]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [ディメンションの属性のプロパティの参照](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)  
  
  

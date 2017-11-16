---
title: "ディメンションにディメンション インテリジェンスの追加 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Business Intelligence enhancements [Analysis Services], dimension intelligence
- dimensions [Analysis Services], Business Intelligence enhancements
- dimension intelligence [Analysis Services]
- Type property
ms.assetid: b64fa386-eac2-4286-a320-0631a1887aac
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d1d167da0ab38819f016dd4a0c18c2e65ef42da1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="bi-wizard---add-dimension-intelligence-to-a-dimension"></a>BI ウィザード - ディメンションにディメンション インテリジェンスを追加します。
  ディメンションに標準のビジネスの種類を指定するには、ディメンション インテリジェンス拡張機能をキューブまたはディメンションに追加します。 この拡張機能により、ディメンション属性に対応する型も指定されます。 クライアント アプリケーションでは、指定された種類をデータの分析時に使用できます。  
  
 ディメンション インテリジェンスを追加するには、ビジネス インテリジェンス ウィザードを使用して、 **[拡張機能の選択]** ページの **[ディメンション インテリジェンスの定義]** オプションを選択します。 次に、ウィザードに従って、ディメンション インテリジェンスの適用先となるディメンションを選択し、選択したディメンションの属性を識別します。  
  
## <a name="selecting-a-dimension"></a>ディメンションの選択  
 ウィザードの最初の **[ディメンション インテリジェンス オプションの設定]** ページで、ディメンション インテリジェンスの適用先になるディメンションを指定します。 選択したディメンションに追加されたディメンション インテリジェンス拡張機能により、ディメンションが変更されます。 これらの変更は、選択したディメンションを含むすべてのキューブによって継承されます。  
  
> [!NOTE]  
>  ディメンションに **[勘定科目]** を選択した場合は、ディメンションに勘定科目インテリジェンスを指定します。 詳細については、「 [ディメンションへの勘定科目インテリジェンスの追加](../../analysis-services/multidimensional-models/bi-wizard-add-account-intelligence-to-a-dimension.md)」を参照してください。  
  
## <a name="specifying-dimension-attributes"></a>ディメンション属性の指定  
 **[ディメンション インテリジェンスの定義]** ページの **[ディメンションの種類]** の一覧で選択した値によって、ディメンションの **Type** プロパティが設定されます。 **Type** プロパティの設定により、サーバーとクライアント アプリケーションにディメンションのコンテンツに関する情報が提供されます。 一部の設定はクライアント アプリケーションにガイダンス情報のみを提供するもので、これらの設定は省略できます。 [勘定科目] や [時間] などのその他の設定は特定の動作を決定するので、特定のビジネス インテリジェンス拡張機能を実装するために必要な場合があります。 たとえば、SQL Server Management Studio では、通貨ディメンションを識別し、適切な通貨換算規則を設定するためにディメンションの種類が使用されます。 **[ディメンションの種類]** の既定値は **[標準]**で、ディメンションのコンテンツに関する仮定は行われません。  
  
 ディメンションの種類を選択したら、 **[ディメンションの属性]**の **[追加]** 列で、ディメンションに対応する属性がある標準の属性型の隣のチェック ボックスをオンにします。 最後に、 **[ディメンションの属性]** 列で、ドロップダウン リストを展開し、選択した属性の型に対応するディメンション内の属性を選択します。 一覧から属性を選択すると、その属性の **Type** プロパティが設定されます。  
  
 たとえば、勘定科目ディメンションにディメンション インテリジェンスを追加するには、 **[ディメンションの種類]**で **[勘定科目]**を選択します。 次に、このディメンションに **[勘定科目の種類]** 属性と **[勘定科目の説明]** 属性がある場合は、 **[追加]** 列で、 **[勘定科目名]** と **[勘定科目の種類]** の、各勘定科目の種類に対応するチェック ボックスをオンにします。 さらに **[ディメンションの属性]** 列で、これらの勘定科目の種類をディメンションの **[勘定科目の説明]** 属性と **[勘定科目の種類]** 属性にそれぞれ関連付けます。  
  
## <a name="see-also"></a>参照  
 [ビジネス インテリジェンス ウィザードを使用したタイム インテリジェンス計算の定義](../../analysis-services/multidimensional-models/define-time-intelligence-calculations-using-the-business-intelligence-wizard.md)  
  
  


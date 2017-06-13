---
title: "レポート (SSRS) にアセンブリ参照の追加 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code [Reporting Services]
- custom assemblies [Reporting Services], referencing
- custom code [Reporting Services]
- adding assembly references
- assemblies [Reporting Services], references
ms.assetid: 0a03939e-48ce-4c30-b227-98533f2e0ccb
caps.latest.revision: 43
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 1bf8106435899a97572c5972721bdf3190d031a6
ms.contentlocale: ja-jp
ms.lasthandoff: 06/13/2017

---
# <a name="add-an-assembly-reference-to-a-report-ssrs"></a>レポートにアセンブリへの参照を追加する (SSRS)
  参照を含んだカスタム コードを埋め込む場合[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]に追加されていないクラス<xref:System.Math>または<xref:System.Convert>、レポート プロセッサは、名前を解決できるように、アセンブリ、レポートへの参照を提供する必要があります。 詳細については、「[レポートにコードを追加する (SSRS)](../../reporting-services/report-design/add-code-to-a-report-ssrs.md)」を参照してください。  
  
### <a name="to-add-an-assembly-reference-to-a-report"></a>レポートにアセンブリへの参照を追加するには  
  
1.  **[デザイン]** ビューで、デザイン画面のレポートの罫線の外を右クリックし、 **[レポートのプロパティ]**をクリックします。  
  
2.  **[参照]**をクリックします。  
  
3.  **[アセンブリの追加または削除]**で **[追加]** をクリックしてから、参照ボタンをクリックし、アセンブリを参照します。  
  
4.  **[クラスの追加または削除]**で **[追加]** をクリックしてから、クラスの名前を入力し、レポート内で使用するインスタンス名を指定します。  
  
    > [!NOTE]  
    >  インスタンスベースのメンバーにのみ、クラスおよびインスタンスの名前を指定してください。 **[クラス]** の一覧に静的メンバーを指定しないでください。 詳細については、「[レポート デザイナーでカスタム コードやアセンブリを式から参照する (SSRS)](../../reporting-services/report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md)」を参照してください。  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>参照  
 [レポートでのカスタム アセンブリの使用](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)   
 [[参照] ([レポートのプロパティ] ダイアログ ボックス)](http://msdn.microsoft.com/library/4639d368-9918-4bb1-9953-7a724ca78dea)  
  
  

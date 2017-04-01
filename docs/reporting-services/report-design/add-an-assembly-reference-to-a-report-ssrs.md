---
title: "レポートにアセンブリへの参照を追加する (SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "コード [Reporting Services]"
  - "カスタム アセンブリ [Reporting Services], 参照"
  - "カスタム コード [Reporting Services]"
  - "アセンブリへの参照の追加"
  - "アセンブリ [Reporting Services], 参照"
ms.assetid: 0a03939e-48ce-4c30-b227-98533f2e0ccb
caps.latest.revision: 43
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 43
---
# レポートにアセンブリへの参照を追加する (SSRS)
  <xref:System.Math> または <xref:System.Convert> にない [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] クラスへの参照を含むカスタム コードを埋め込む場合は、レポート プロセッサで名前を解決できるように、レポートへのアセンブリ参照を指定する必要があります。 詳細については、「[レポートにコードを追加する (SSRS)](../../reporting-services/report-design/add-code-to-a-report-ssrs.md)」を参照してください。  
  
### レポートにアセンブリへの参照を追加するには  
  
1.  **[デザイン]** ビューで、デザイン画面のレポートの罫線の外を右クリックし、**[レポートのプロパティ]** をクリックします。  
  
2.  **[参照]** をクリックします。  
  
3.  **[アセンブリの追加または削除]** で **[追加]** をクリックしてから、参照ボタンをクリックし、アセンブリを参照します。  
  
4.  **[クラスの追加または削除]** で **[追加]** をクリックしてから、クラスの名前を入力し、レポート内で使用するインスタンス名を指定します。  
  
    > [!NOTE]  
    >  インスタンスベースのメンバーにのみ、クラスおよびインスタンスの名前を指定してください。 **[クラス]** の一覧に静的メンバーを指定しないでください。 詳細については、「[レポート デザイナーでカスタム コードやアセンブリを式から参照する (SSRS)](../../reporting-services/report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md)」を参照してください。  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## 参照  
 [レポートでのカスタム アセンブリの使用](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)   
 [[参照] ([レポートのプロパティ] ダイアログ ボックス)](../Topic/Report%20Properties%20Dialog%20Box,%20References.md)  
  
  
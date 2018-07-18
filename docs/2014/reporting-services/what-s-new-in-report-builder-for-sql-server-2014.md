---
title: どのような&#39;s New in SQL Server 2014 用レポート ビルダー |Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 8223c19b-4b0d-4b1d-a042-9a726c18e708
caps.latest.revision: 13
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8825385596c14121d0e6e13a7ecdbccbafb26a52
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37224902"
---
# <a name="what39s-new-in-report-builder-for-sql-server-2014"></a>どのような&#39;s for SQL Server 2014 レポート ビルダーの新機能
  [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] では、いくつかの [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 機能が導入されています。  
  
 このリリースの他の機能については[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]製品およびテクノロジでは、「 [SQL Server 2014 における新](../sql-server/what-s-new-in-sql-server-2016.md)します。  
  
> [!TIP]  
>  最新の情報とこのリリースの新機能に関するリソースを参照してください。[追加情報については、SQL Server Reporting Services (SSRS) で新しい](http://go.microsoft.com/fwlink/?LinkId=207147)します。  
  
##  <a name="ExcelRenderer"></a> Microsoft Excel 2007-2010 レンダラーと Microsoft Excel 2003 用 excel レンダラー  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] で新しく採用された [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Excel 表示拡張機能では、インストールされている Word/Excel/PowerPoint 用 Microsoft Office 互換機能パックによって、レポートが [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 2007-2010 および [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 2003 と互換性のある Excel 文書として表示されます。 形式は Office Open XML で、ファイルのファイル拡張子は .xlsx です。  
  
 この Excel 表示拡張機能では、Excel 2003 と互換性のある以前のバージョンの制約が取り除かれています。 表示拡張機能で強化された点を次に示します。  
  
-   ワークシートあたりの最大行数: 1,048,576 行  
  
-   ワークシートあたりの最大列数: 16,384  
  
-   ワークシート内で使用できる色の数: 約 1,600 万色 (24 ビット カラー)  
  
-   ZIP 圧縮によるファイル サイズの削減  
  
 詳細については、「[Microsoft Excel へのエクスポート &#40;レポート ビルダーおよび SSRS&#41;](report-builder/exporting-to-microsoft-excel-report-builder-and-ssrs.md)」を参照してください。  
  
##  <a name="WordRenderer"></a> Microsoft Word 2007-2010 レンダラーと Microsoft Word 2003 用の Word レンダラー  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] で新しく採用された [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Word 表示拡張機能では、インストールされている Word/Excel/PowerPoint 用 [!INCLUDE[ofprword](../includes/ofprword-md.md)] Office 互換機能パックによって、レポートが [!INCLUDE[ofprword](../includes/ofprword-md.md)] 2007-2010 および [!INCLUDE[msCoName](../includes/msconame-md.md)] 2003 と互換性のある Word 文書として表示されます。 形式は Office Open XML で、ファイルのファイル拡張子は docx です。  
  
 エクスポートされたレポートで Word 2007-2010 の新機能が利用できるようになる点に加え、エクスポートされたレポートの *.docx ファイルのサイズが小さくなる傾向があります。 Word レンダラーを使用してエクスポートされたレポートは通常、Word 2003 レンダラーを使用してエクスポートされた同じレポートよりもサイズがかなり小さくなります。  
  
 詳細については、「[Microsoft Word へのエクスポート &#40;レポート ビルダーおよび SSRS&#41;](report-builder/exporting-to-microsoft-word-report-builder-and-ssrs.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQL Server 2014 のレポート ビルダー](report-builder/report-builder-in-sql-server-2016.md)  
  
  

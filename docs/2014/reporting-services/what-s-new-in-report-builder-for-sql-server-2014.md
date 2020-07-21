---
title: SQL Server 2014 | のレポートビルダーの&#39;の新機能Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 8223c19b-4b0d-4b1d-a042-9a726c18e708
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 35ac6191407e02a2dc15ab210c5e9276e761df75
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66098682"
---
# <a name="what39s-new-in-report-builder-for-sql-server-2014"></a>SQL Server 2014 のレポートビルダーの新&#39;
  [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] では、いくつかの [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 機能が導入されています。  
  
 このリリースの他の[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]製品およびテクノロジの機能の詳細については、「 [SQL Server 2014 の新](../sql-server/what-s-new-in-sql-server-2016.md)機能」を参照してください。  
  
> [!TIP]  
>  このリリースの新機能に関する最新の情報とリソースについては、 [SQL Server Reporting Services (SSRS) の新機能に関する追加情報](https://go.microsoft.com/fwlink/?LinkId=207147)を参照してください。  
  
##  <a name="excel-renderer-for-microsoft-excel-2007-2010-and-microsoft-excel-2003"></a><a name="ExcelRenderer"></a>Microsoft Excel 2007-2010 および Microsoft Excel 2003 用 excel レンダラー  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] で新しく採用された [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Excel 表示拡張機能では、インストールされている Word/Excel/PowerPoint 用 Microsoft Office 互換機能パックによって、レポートが [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 2007-2010 および [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 2003 と互換性のある Excel 文書として表示されます。 形式は Office Open XML で、ファイルのファイル拡張子は .xlsx です。  
  
 この Excel 表示拡張機能では、Excel 2003 と互換性のある以前のバージョンの制約が取り除かれています。 表示拡張機能で強化された点を次に示します。  
  
-   ワークシートあたりの最大行数: 1,048,576 行  
  
-   ワークシートあたりの最大列数: 16,384  
  
-   ワークシート内で使用できる色の数: 約 1,600 万色 (24 ビット カラー)  
  
-   ZIP 圧縮によるファイル サイズの削減  
  
 詳細については、「 [Microsoft Excel へのエクスポート &#40;レポート ビルダーおよび SSRS&#41;](report-builder/exporting-to-microsoft-excel-report-builder-and-ssrs.md)で操作できます。  
  
##  <a name="word-renderer-for-microsoft-word-2007-2010-and-microsoft-word-2003"></a><a name="WordRenderer"></a>Microsoft Word 2007-2010 および Microsoft Word 2003 用 word レンダラー  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] で新しく採用された [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Word 表示拡張機能では、インストールされている Word/Excel/PowerPoint 用 [!INCLUDE[ofprword](../includes/ofprword-md.md)] Office 互換機能パックによって、レポートが [!INCLUDE[ofprword](../includes/ofprword-md.md)] 2007-2010 および [!INCLUDE[msCoName](../includes/msconame-md.md)] 2003 と互換性のある Word 文書として表示されます。 形式は Office Open XML で、ファイルのファイル拡張子は docx です。  
  
 エクスポートされたレポートで Word 2007-2010 の新機能が利用できるようになる点に加え、エクスポートされたレポートの *.docx ファイルのサイズが小さくなる傾向があります。 Word レンダラーを使用してエクスポートされたレポートは通常、Word 2003 レンダラーを使用してエクスポートされた同じレポートよりもサイズがかなり小さくなります。  
  
 詳細については、「 [Microsoft Word へのエクスポート &#40;レポート ビルダーおよび SSRS&#41;](report-builder/exporting-to-microsoft-word-report-builder-and-ssrs.md)で操作できます。  
  
## <a name="see-also"></a>参照  
 [SQL Server 2014 のレポート ビルダー](report-builder/report-builder-in-sql-server-2016.md)  
  
  

---
title: 画像ファイルへのエクスポート (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 020d8ea2-de07-4212-a2bb-2ed0df2c8db8
caps.latest.revision: 10
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 1d4ea909ce3682498755ab45fd3336e2586e539b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37299792"
---
# <a name="exporting-to-an-image-file-report-builder-and-ssrs"></a>画像ファイルへのエクスポート (レポート ビルダーおよび SSRS)
  画像表示拡張機能では、レポートがビットマップまたはメタファイルとして表示されます。 画像表示拡張機能では、既定でレポートの TIFF ファイルが生成されます。このファイルは、複数のページに表示することもできます。 クライアントは、受信した画像をイメージ ビューアーで表示したり、印刷したりできます。 ここでは、画像レンダラー固有の情報を提供し、また表示規則の例外について説明します。  
  
 画像表示拡張機能では、 [!INCLUDE[ndptecgdiplus](../../includes/ndptecgdiplus-md.md)]でサポートされている形式 (BMP、EMF、EMFPlus、GIF、JPEG、PNG、TIFF) でファイルを生成できます。 TIFF 形式の場合、プライマリ ストリームのファイル名は *ReportName*.tif です。 その他の形式の場合は、1 ファイルが 1 ページに表示されます。ファイル名は *ReportName_Page.ext*  (*ext* は選択した形式のファイル拡張子) です。 画像としてサポートされている別の形式でファイルを作成するには、上記の文字列のいずれかを **OutputFormatDeviceInfo** 設定で指定します。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="SupportedImageFormats"></a> サポートされている画像形式  
 次の表は、各画像レンダラー形式のファイルの拡張子と MimeType を示しています。  
  
|**型**|**拡張子**|**MIMEType**|  
|--------------|-------------------|------------------|  
|BMP|BMP|image/bmp|  
|GIF|GIF|image/gif|  
|JPEG|JPEG|image/jpeg|  
|PNG|PNG|image/png|  
|TIFF|tif|image/tiff|  
|EMF|EMF|image/emf|  
|EMFPlus|emf|image/emf|  
  
  
##  <a name="RenderingMultiplePages"></a> 複数ページの表示  
 1 つのファイルで複数のページのドキュメントをサポートしているファイル形式は TIFF だけです。 JPG や PNG などの他の形式では、一度に出力できるのは 1 ページで、ページごとに表示拡張機能を個別に呼び出す必要があります。  
  
  
##  <a name="Interactivity"></a> 対話性  
 このレンダラーで生成されたすべての画像形式では、対話機能がサポートされていません。 次の対話型要素は表示されません。  
  
-   ハイパーリンク  
  
-   表示/非表示  
  
-   ドキュメント マップ  
  
-   ドリルスルー リンクまたはクリックスルー リンク  
  
-   エンド ユーザー並べ替え  
  
-   固定ヘッダー  
  
-   ブックマーク  
  
  
##  <a name="DeviceInfo"></a> デバイス情報設定  
 デバイス情報設定を変更することによって、このレンダラーの既定の設定の一部を変更することができます。 詳細については、「 [画像デバイス情報設定](../image-device-information-settings.md)」を参照してください。  
  
  
## <a name="see-also"></a>参照  
 [Reporting Services の改ページ &#40;レポート ビルダーおよび SSRS&#41;](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md)   
 [レンダリングの動作 &#40;レポート ビルダーおよび SSRS&#41;](../report-design/rendering-behaviors-report-builder-and-ssrs.md)   
 [さまざまなレポート表示拡張機能の対話機能 &#40;レポート ビルダーおよび SSRS&#41;](interactive-functionality-different-report-rendering-extensions.md)   
 [レポート アイテムのレンダリング &#40;レポート ビルダーおよび SSRS&#41;](../report-design/rendering-report-items-report-builder-and-ssrs.md)   
 [テーブル、マトリックス、および一覧 &#40;レポート ビルダーおよび SSRS&#41;](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)  
  
  

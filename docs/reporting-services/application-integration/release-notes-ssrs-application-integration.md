---
title: SSRS のレポート ビューアー コントロールのリリース ノート
ms.date: 09/20/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: application-integration
ms.topic: reference
ms.assetid: 112e0240-351d-46a9-98c7-2be09f26ac60
ms.reviewer: maghan
author: RhysSchmidtke
ms.author: rhys
ms.openlocfilehash: 1528358c8aff5d6e99869f0f4f8c1676ee2d5e75
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67730907"
---
# <a name="release-notes-for-the-report-viewer-controls-for-webforms-and-winforms-of-ssrs"></a>WebForms および WinForms の SSRS にレポート ビューアー コントロールのリリース ノート

これらの WebForms および WinForms、関連するレポート ビューアー コントロールのリリース ノートは、 [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] (SSRS)。

SSRS のリリース ノートについては、次を参照してください。[の SQL Server Reporting Services (SSRS) 2017 以降のリリース ノート](../release-notes-reporting-services.md)します。

## <a name="15013580"></a>150.1358.0
| 変更の説明 | 詳細 |
| :----------------- | :------ |
| バグの修正 | プロジェクトの参照から Microsoft.ReportViewer.Design アセンブリを削除する変更を元に戻されます。 |
|           | その他の変更の一環として、2 つのアセンブリは 15.3 を 15.0 のバージョンから変更されました。 これが戻されました。 |
| &nbsp; | &nbsp; |

## <a name="15013570"></a>150.1357.0
| 変更の説明 | 詳細 |
| :----------------- | :------ |
| バグの修正  | 高 DPI モニターの適切な印刷のプレビュー |
|            | 表示領域外印刷ダイアログ ボックスが表示されます。 |
|            | 多数のパラメーターにより、スクロール バーのパラメーターおよびドロップダウン リストが正しく動作していません |
|            | Null と日付時刻のパラメーターで問題を修正しました |
|            | 更新された JQuery バージョン 3.3.1 |
|            | HTML のレンダリングで tablix セルの重複を修正しました |
|            | プロジェクトの参照をプロジェクトに追加される VS アセンブリを誤ったを排除するデザイン時の削除 |
|            | アクティブな項目に対してのみナレーションをツール バーのアクセシビリティの修正します。 |
| &nbsp; | &nbsp; |

## <a name="15900148"></a>15.900.148

| 変更の説明 | 詳細 |
| :----------------- | :------ |
| パラメーターのないレポートが **Server.LoadReportDefinition** によって読み込まれないバグが修正されています。 | &nbsp; |
| WebForms レポート ビューアー コントロール。 | RTL ページ (*direction: rtl;* css を使用してテキスト フローをを変更するページ) への埋め込みがサポートされました。<br/><br/>*IReportViewerMessages5* ローカリゼーション インターフェイスを使用した、印刷ダイアログ テキストのカスタマイズがサポートされました。<br/><br/>ユーザー補助のサポートが改善されました。<br/><br/>&bull; &nbsp; &nbsp; [WebForms のレポート ビューアー コントロール用の NuGet パッケージ](https://www.nuget.org/packages/Microsoft.ReportingServices.ReportViewerControl.Webforms/150.900.148) |
| WinForms レポート ビューアー コントロール。 | アプリが高 DPI モードで実行されている場合の印刷機能が修正されました。<br/><br/>&bull; &nbsp; &nbsp; [WinForms のレポート ビューアー コントロール用の NuGet パッケージ](https://www.nuget.org/packages/Microsoft.ReportingServices.ReportViewerControl.Winforms/150.900.148) |
| &nbsp; | &nbsp; |

## <a name="next-steps"></a>次の手順

レポート ビューアー コントロールの[概要](integrating-reporting-services-using-reportviewer-controls-get-started.md)。

その他の質問 [Reporting Services のフォーラムをお試しください](https://go.microsoft.com/fwlink/?LinkId=620231)。

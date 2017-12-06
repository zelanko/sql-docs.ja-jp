---
title: "レポート ビルダーをアンインストールする | Microsoft Docs"
ms.custom: 
ms.date: 05/30/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: install-windows
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- reporting-services-native
- reporting-services-sharepoint
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 009538c6-4941-4393-b14b-9144cffdbdaf
caps.latest.revision: "10"
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: b8b43fb2c76f33204c739779af03ede54869839f
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="uninstall-report-builder"></a>レポート ビルダーをアンインストールする

スタンドアロン バージョンのレポート ビルダーは、コントロール パネルまたはコマンド ラインからアンインストールできます。

レポート ビルダーをコマンド ラインからアンインストールする場合に使用する構文は、/i オプションの代わりに /x オプションを使用する以外はレポート ビルダーをインストールする場合と同じです。 /quiet オプションやその他の標準のオプションも使用できます。 レポート ビルダーの Windows インストーラー パッケージ (ReportBuilder3_x86.msi) を削除してしまった場合は、コマンド ラインを使用してレポート ビルダーをアンインストールするのは容易ではありません。 GUID を使用してレポート ビルダーを削除する方法の詳細については、「 [Command-Line Options](https://msdn.microsoft.com/library/windows/desktop/aa367988.aspx)」 (コマンドライン オプション) の msiexec プログラムのドキュメントを参照してください。  

レポート ビルダーで使用しているフォルダーにカスタム ファイルが含まれている場合は、レポート ビルダーを削除しても、それらのフォルダーとファイルは削除されません。 レポート ビルダーのファイルのみが削除されます。  

### <a name="to-uninstall-report-builder-from-the-control-panel"></a>レポート ビルダーをコントロール パネルからアンインストールするには

1.  **[スタート]** ボタンをクリックし、 **[コントロール パネル]**をクリックします。  
  
2.  コントロール パネルで、 **[プログラムと機能]**をクリックします。  
  
3.  **[名前]** の一覧で、[!INCLUDE[msCoName](../../includes/msconame-md.md)] SQL Server 2016 レポート ビルダーを見つけてクリックします。  
  
4.  **[アンインストール]**をクリックします。  
  
5.  レポート ビルダーをアンインストールするかどうかを確認するメッセージが表示された場合は、 **[はい]**をクリックします。  
  
### <a name="to-uninstall-report-builder-from-the-command-line"></a>レポート ビルダーをコマンド ラインからアンインストールするには  
  
1.  **[スタート]** メニューの **[ファイル名を指定して実行]**をクリックします。  
  
2.  **[名前]** ボックスに「 **cmd**」と入力します。  
  
3.  コマンド プロンプト ウィンドウで、ReportBuilder3_x86.msi が格納されているフォルダーに移動します。  
  
4.  コマンド ラインに次のように入力します。  
  
 `msiexec /x ReportBuilder3_x86.msi /quiet /l*v install.log`  
  
 ログ記録を使用できる場合は、次のようなコマンド ラインを使用します。  
  
 `msiexec /x ReportBuilder3_x86.msi /quiet /l*v c:\junk\install.log`  
  
5.  **Enter**キーを押します。  

## <a name="next-steps"></a>次の手順

[レポート ビルダーをインストールする](../../reporting-services/install-windows/install-report-builder.md)  

その他の質問 [Reporting Services のフォーラムに質問してみてください](http://go.microsoft.com/fwlink/?LinkId=620231)

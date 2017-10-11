---
title: "SharePoint サイト上の SQL Server Reporting Services レポート ビューアー web パーツを展開 |Microsoft ドキュメント"
ms.custom: 
ms.date: 10/05/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: ea362cd05de5d1ba17ca717d94354d5786119bab
ms.openlocfilehash: a75ad193204e17e1d053aa4e00adba5f551d684b
ms.contentlocale: ja-jp
ms.lasthandoff: 10/06/2017

---

# <a name="deploy-the-sql-server-reporting-services-report-viewer-web-part-on-a-sharepoint-site"></a>SharePoint サイト上の SQL Server Reporting Services レポート ビューアー web パーツを展開します。

[!INCLUDE [ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)]

レポート ビューアー web パーツとは、レポートを表示する SQL Server Reporting Services (ネイティブ モード)、SharePoint サイト内で使用できるカスタム web パーツです。 表示、移動、印刷、web パーツを使用し、レポート サーバー上のレポートをエクスポートできます。 レポート ビューアー web パーツは、SQL Server Reporting Services レポート サーバーまたは Power BI のレポート サーバーによって処理されるレポート定義 (.rdl) ファイルに関連付けられます。 このレポート ビューアー web パーツは、Power BI のレポート サーバーでホストされている Power BI レポートで使用できません。

レポート ビューアー web パーツを SharePoint Server 2013 または SharePoint Server 2016 の環境に追加するソリューション パッケージを手動で展開するのにには、次の手順を使用します。 Web パーツを構成するために必要な手順は、ソリューションを配置します。

**レポート ビューアー web パーツは、ソリューション パッケージがスタンドアロンと SQL Server Reporting Services の SharePoint 統合モードに関連付けられていません。**

## <a name="requirements"></a>必要条件

**SharePoint サーバーのバージョンをサポートします。**  
* SharePoint Server 2016
* SharePoint Server 2013

**Reporting Services のバージョンをサポートします。**  
* SQL Server 2008 Reporting Services (ネイティブ モード) およびそれ以降。
* Power BI レポート サーバー

## <a name="download-the-report-viewer-web-part-solution-package"></a>レポート ビューアー web パーツのソリューション パッケージをダウンロードします。

レポート ビューアー web パーツは、Microsoft ダウンロード センターで使用可能なです。

[レポート ビューアー web パーツのソリューション パッケージをダウンロードします。](https://www.microsoft.com/download/details.aspx?id=55949)

## <a name="deploy-the-farm-solution"></a>ファーム ソリューションを配置します。

このセクションでは、SharePoint ファームにソリューション パッケージを展開する方法を示します。 このタスクは一度実行するだけで済みます。

1. SharePoint サーバーに SharePoint 管理シェルを使用して、開き、**管理者として実行**オプション。

2. 実行[追加 SPSolution](https://technet.microsoft.com/library/ff607552(v=office.16).aspx)ファーム ソリューションを追加します。

    ```
    Add-SPSolution –LiteralPath "{path to file}\ReportViewerWebPart.wsp"
    ```

    コマンドレットにより、ソリューション名、ソリューション ID、および Deployed=False が返されます。 次の手順では、ソリューションを配置します。

3. 実行、[インストール SPSolution](https://technet.microsoft.com/library/ff607534(v=office.16).aspx)コマンドレット ファーム ソリューションの配置を使用します。

    **SharePoint 2013**

    ```
    Install-SPSolution –Identity ReportViewerWebPart.wsp -CompatibilityLevel "14,15" -GACDeployment -WebApplication {URL to web application}
    ```

    **SharePoint 2016**

    ```
    Install-SPSolution –Identity ReportViewerWebPart.wsp -GACDeployment -WebApplication {URL to web application}
    ```

## <a name="activate-feature"></a>機能をアクティブ化します。

1. SharePoint サイトで次のように選択します。、**歯車**クリックし、左上にあるアイコン **サイトの設定*です。

    ![サイトの設定は、歯車アイコンをクリックします。](media/sharepoint-site-settings.png)

    既定では、SharePoint Web アプリケーションへのアクセスにはポート 80 が使用されます。 つまり、多くの場合、入力することで SharePoint サイトにアクセスすることができますを*http://<computer name>* を開くには、ルート サイト コレクション。

3. **サイト コレクションの管理****サイト コレクション機能**します。

4. ページが表示されるまで下へスクロールして、**レポート ビューアー web パーツ**機能します。

5. **[アクティブ化]**を選びます。

    ![レポート ビューアー web パーツの機能をアクティブ化します。](media/web-part-activiate-feature.png)

6. 各サイトを開き、サイトの操作をクリックして、追加のサイト コレクションに対して繰り返します。

必要に応じて、使用することできますも PowerShell を使用してすべてのサイトにこの機能を有効にする、 [Enable-spfeature](https://technet.microsoft.com/library/ff607803.aspx)コマンドレット。

```
Get-SPWebApplication "<web application url>" | Get-SPSite -Limit ALL | 
        ForEach-Object {
            Write-Host "Enabling feature for $($_.URL)"
            Enable-SPFeature -identity "ReportViewerWebPart" -URL $_.URL -ErrorAction Continue
        }
```

## <a name="remove-the-solution"></a>ソリューションを削除します。

SharePoint サーバーの全体管理でソリューションの取り消しを取り消す必要はありません、 **ReportViewerWebPart.wsp**ファイルのインストールまたはパッチ配置の問題のトラブルシューティングを体系的に行う場合を除き、します。

1. SharePoint サーバーの全体管理で**システム設定****ファーム ソリューションの管理**です。

2. 選択**ReportViewerWebPart.wsp**です。

3. ソリューションの取り消しを選択します。

### <a name="remove-the-web-part-from-site-settings"></a>Web パーツをサイトの設定から削除します。

ソリューションの取り消しも、レポート ビューアー web パーツは、SharePoint サイト内の web パーツの一覧から削除されません。 レポート ビューアー web パーツを削除するには、次のです。

1. SharePoint サイトで次のように選択します。、**歯車**クリックし、左上にあるアイコン **サイトの設定*です。

    ![サイトの設定は、歯車アイコンをクリックします。](media/sharepoint-site-settings.png)

    既定では、SharePoint Web アプリケーションへのアクセスにはポート 80 が使用されます。 つまり、多くの場合、入力することで SharePoint サイトにアクセスすることができますを*http://<computer name>* を開くには、ルート サイト コレクション。

2. **Web デザイナー ギャラリー** **web パーツ**です。

3. 選択、 **編集 アイコン** の横に**ReportViewerNativeMode.dwp**です。 結果の最初のページには表示されません。

4. 選択**項目を削除**です。

    ![編集し、レポート ビューアーのネイティブ モードの web パーツを削除](media/report-viewer-native-mode-edit-delete.png)

PowerShell を使用して、web パーツの削除を試行するが、直接コマンドがありません。 スクリプトの例では、次を参照してください。 [web パーツ ギャラリーから web パーツを削除する方法](https://gallery.technet.microsoft.com/office/How-to-delete-Web-Parts-1132701f)です。

## <a name="supported-languages"></a>サポートされている言語

Web パーツでは、次の言語がサポートされています。

* 英語 (en)
* ドイツ語 (de)
* スペイン語 (sp)
* フランス語 (fr)
* イタリア語 (it)
* 日本語 (ja)
* 韓国語 (ko)
* ポルトガル語 (pt)
* ロシア語 (ru)
* 簡体字中国語 - zh HANS と ZH-CHS)
* 中国語 (繁体 - それおよび ZH-CHT の)

## <a name="next-steps"></a>次の手順

レポート ビューアー web パーツが展開されているとアクティブ化では、SharePoint ページに web パーツを追加できます。 詳細については、次を参照してください。 [SharePoint ページに追加のレポート ビューアー web パーツ](add-report-viewer-web-part-to-page.md)です。

その他の質問 [Reporting Services のフォーラムに質問してみてください](http://go.microsoft.com/fwlink/?LinkId=620231)

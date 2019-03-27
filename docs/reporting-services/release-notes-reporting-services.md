---
title: リリース ノート (SSRS) の 2017 以降 |Microsoft Docs
ms.date: 09/01/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.reviewer: maghan
author: casualoak
ms.author: RhysSchmidtke
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions'
ms.openlocfilehash: c85d3811fc467d94dc1841b871964e3bb594e2df
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 03/20/2019
ms.locfileid: "58283295"
---
# <a name="release-notes-for-sql-server-reporting-services-ssrs-2017-and-later"></a>SQL Server Reporting Services (SSRS) 2017 以降のリリース ノート

[!INCLUDE [ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE [ssrs-appliesto-2017-and-later](../includes/ssrs-appliesto-2017-and-later.md)]

この記事では、変更をについて説明します[!INCLUDE[ssnoversion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] (SSRS) 2017 以降のバージョン。

レポート ビューアー コントロールのリリース ノートについては、次を参照してください。 [WebForms および WinForms の SSRS のレポート ビューアーのリリース ノートを制御](application-integration/release-notes-ssrs-application-integration.md)します。

<!--
We are "standardizing" all our 'Release Notes' style articles:

  - File names:   'release-notes-[TechArea-Name].md'


  - Content format:   2-column tables.  No longer using bullet lists.

    - Ideally, the 'Details' column should contain a link to another SSRS documentation article wherein the particular issue fix is discussed in any way.  Or if there is more to say beyond one sentence, the other sentences of elaboration would go into the 'Details' column.


  - H2 header names are kept short, for better display.


  - Try to keep all Release Notes in one .md file.  Avoid having multiple R.N. files whose names differ only by version or date.

    - Seriously consider erasing info about ancient releases that are so old that nobody cares about them anymore.  If you really want to retain ancient info, consider doing so in an HTML comment at the end of the .md file, just in case a Microsoft employee needs to re-examine ancient info.  In any case, this file cannot get ever longer, and some deletion or hiding of oldest info must eventually occur.


  - Do use '::: moniker range=' zones when version 2017 is no longer the only version represented inside this .md file.

    - Use the '=' operator on the moniker, not the '>=' operator.
    - In contrast, in our 'Whats New' articles we do use the '>=', rather than '='.

GeneMi, DevOps = 1467988 (MsEng > TechnicalContent) , 2019/03/19
-->

## <a name="1406001109-20190212"></a>14.0.600.1109、2019/02/12

| 問題を修正しました | 詳細 |
| :---------- | :------ |
| キャッシュ レポート スナップショット スケジュールが、サブスクリプションの変更後に "レポート固有のスケジュール" に変更される。 | &nbsp; |
| Express エディションで rc:Toolbar=false が機能しない。 | &nbsp; |
| ページ分割されたレポートを PDF にエクスポートすると、タイ語の特定の文字が正しく表示されない。 | &nbsp; |
| 完成したデータ ドリブン サブスクリプションの通知中にデッドロックが発生する。 | &nbsp; |
| rc:Toolbar=False パラメーターを使用すると、特定の状況で埋め込み画像が表示されなくなる。 | &nbsp; |
| カスケード型パラメーターを使用するレポートに対して、データ ドリブン サブスクリプションを作成できない。 | &nbsp; |
| 無効な間隔で構成されているサブスクリプションを編集できない。 | &nbsp; |
| セキュリティ更新プログラム。 | &nbsp; |
| リンク レポートの UI が表示されない。 | &nbsp; |
| 入れ子になった tablix コントロールがあるページ分割されたレポートで、間違ったフォントが使用される。 | &nbsp; |
| 空白文字は、tablix データ領域が含まれている特定の改ページ調整されたレポートに正しく追加されていません。 | &nbsp; |
| モバイル レポートのシンプル データ グリッドを拡張すると、ヘッダー行が消える。 | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="140600906-20180912"></a>14.0.600.906、2018/09/12

次の問題が修正されています。

| 問題を修正しました | 詳細 |
| :---------- | :------ |
| カスタム認証が正しい Cookie 情報を返さない。 | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="140600892-20180831"></a>14.0.600.892、2018/08/31

| 問題を修正しました | 詳細 |
| :---------- | :------ |
| rc:Toolbar=False で、テキストが長い場合、四角形の内部にあるテキスト ボックスのために四角形が垂直方向に拡大しない。 | &nbsp; |
| pageHeight が 0.5 インチ未満の場合、テキストのサイズが拡大縮小しない。 | &nbsp; |
| CRM と共に使用するときに、SSRS カタログ データベースでデッドロックが発生します。 | &nbsp; |
| レポートを下にスクロールするとき、垂直方向に整列された列見出しが正しく表示されない。 | &nbsp; |
| SCOM レポートの役割に追加されたユーザーが、SSRS Web ポータルへのアクセスをブロックされる。 | &nbsp; |
| タイ語文字は、正しく PDF にエクスポートされません。 | &nbsp; |
| ブラウザーの役割の動作の変更。 | &nbsp; |
| Express エディションで rc:Toolbar=false が機能しない。 | &nbsp; |
| パラメーターのプロンプト領域の垂直スクロール バーがありません。 | &nbsp; |
| 更新されたモバイル レポート ランタイム。 | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="140600744-20180425"></a>14.0.600.744、2018/04/25

| 問題を修正しました | 詳細 |
| :---------- | :------ |
| 配信オプションを作成しても [データ ドリブン サブスクリプション] ページに表示されない。 | &nbsp; |
| SSRS 2012 を SSRS 2017 にアップグレードすると、RSManagement で数秒ごとに例外がスローされる。 | &nbsp; |
| IE11 で複数値のパラメーターの既定値を変更できない。 | &nbsp; |
| 共有スケジュールが実行されるたびにスケジュールが空になる。 | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="140600689-20180228"></a>14.0.600.689、2018/02/28

| 問題を修正しました | 詳細 |
| :---------- | :------ |
| リンク レポートのレポート パラメーターの表示が、そのプロパティを編集すると元に戻る。 | &nbsp; |
| Express エディションで URL パラメーター rc:Toolbar=false が機能しない。 | &nbsp; |
| プロパティは、CanGrow を含むテキスト ボックスの式があると表示されない値で結果が false に設定します。 | &nbsp; |
| セットアップ時のプロダクト キーに "_詳細情報_" リンクが追加される。 | &nbsp; |
| カスタムのフォーム認証を使用した Web ポータルで、スライド式有効期限の Cookie が無視される。 | &nbsp; |
| 行のコンテンツが空の場合、Word にエクスポートすると行の高さが等しくならない。 | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="140600594-20180109"></a>14.0.600.594、2018/01/09

一部のセキュリティ更新プログラムが実装されました。

### <a name="140600490-20171101"></a>14.0.600.490、2017/11/01

SKU アップグレードに関する問題を解決しました。

## <a name="140600451-20170930"></a>14.0.600.451、2017/09/30

最初のリリース。

## <a name="next-steps"></a>次の手順

[Reporting Services (SSRS) の新機能](what-s-new-in-sql-server-reporting-services-ssrs.md)

その他の質問 [Reporting Services のフォーラムに質問してみてください](https://go.microsoft.com/fwlink/?LinkId=620231)。

---
title: SQL Server Reporting Services (SSRS) 2017 以降の変更ログ | Microsoft Docs
ms.date: 08/31/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
author: casualoak
ms.author: RhysSchmidtke
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 0eec59b0d2618686f866e6b7799922d9c255b238
ms.sourcegitcommit: 009bee6f66142c48477849ee03d5177bcc3b6380
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/13/2019
ms.locfileid: "56230909"
---
# <a name="change-log-for-sql-server-reporting-services-ssrs-2017-and-later"></a>SQL Server Reporting Services (SSRS) 2017 以降の変更ログ

[!INCLUDE [ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE [ssrs-appliesto-2017-and-later](../includes/ssrs-appliesto-2017-and-later.md)] 

この記事では、[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] の変更点について説明します。 

## <a name="sql-server-2017-reporting-services"></a>SQL Server 2017 Reporting Services 

### <a name="version-1406001109-released-february-12-2019"></a>バージョン 14.0.600.1109,、リリース日:2019 年 2 月 12 日

次の問題が修正されています。

 - キャッシュ レポート スナップショット スケジュールが、サブスクリプションの変更後に "レポート固有のスケジュール" に変更される。
 - Express エディションで rc:Toolbar=false が機能しない。
 - ページ分割されたレポートを PDF にエクスポートすると、タイ語の特定の文字が正しく表示されない。
 - 完成したデータ ドリブン サブスクリプションの通知中にデッドロックが発生する。
 - rc:Toolbar=False パラメーターを使用すると、埋め込まれている画像が特定の状況で表示されなくなる。
 - カスケード型パラメーターを使用するレポートに対して、データ ドリブンサブスクリプションを作成できない。
 - 無効な間隔で構成されているサブスクリプションを編集できない。
 - セキュリティ更新プログラム
 - リンク レポートの UI が表示されない。
 - 入れ子になった tablix コントロールがあるページ分割されたレポートで、間違ったフォントが使用される。
 - tablix データ領域が含まれるページ分割されたレポートで、ホワイトスペースが間違って追加される。
 - モバイル レポートのシンプル データ グリッドを拡張すると、ヘッダー行が消える。

### <a name="version-140600906-released-september-12-2018"></a>バージョン 14.0.600.906、リリース日:2018 年 9 月 12 日

次の問題が修正されています。

- カスタム認証が正しいクッキー情報を返さない

### <a name="version-140600892-released-august-31-2018"></a>バージョン 14.0.600.892、リリース日:2018 年 8 月 31 日

次の問題が修正されています。

- rc:Toolbar=False で、テキストが長い場合、四角形の内部にあるテキスト ボックスのために四角形が垂直方向に拡大しない 
- pageHeight が 0.5 インチ未満の場合、テキストのサイズが拡大縮小しない 
- CRM で使用したときの、SSRS カタログ データベースでのデッドロック 
- レポートを下にスクロールしたときの、誤って表示される垂直方向に整列された列見出し 
- SCOM レポートの役割に追加されたユーザーが、SSRS Web ポータルへのアクセスをブロックされる 
- タイ語の文字が PDF に正しくエクスポートされない 
- ブラウザーの役割の動作の変更 
- Express Edition で rc:Toolbar=false が機能しない 
- パラメーター プロンプト領域に垂直スクロール バーが表示されない 
- 更新されたモバイル レポート ランタイム 

### <a name="version-140600744-released-april-25-2018"></a>バージョン 14.0.600.744、リリース日:2018 年 4 月 25 日 

次の問題が修正されています。

- 配信オプションを作成しても [データ ドリブン サブスクリプション] ページに表示されない
- SSRS 2012 を SSRS 2017 にアップグレードすると、数秒ごとに例外がスローされる
- IE11 で複数値のパラメーターの既定値を変更できない
- 共有スケジュールが実行されるたびにスケジュールが空になる

### <a name="version-140600689-released-february-28-2018"></a>バージョン 14.0.600.689、リリース日:2018 年 2 月 28日

次の問題が修正されています。

- リンク レポートのレポート パラメーターの表示が、そのプロパティを編集すると元に戻る
- Express Edition で URL パラメーター rc:Toolbar=false が機能しない
- テキスト ボックスに CanGrow プロパティが false に設定された式があると、値が表示されない
- セットアップ時のプロダクト キーに "詳細情報" リンクが追加される
- カスタムのフォーム認証を使用した Web ポータルで、スライド式有効期限の Cookie が無視される
- 行のコンテンツが空の場合、Word にエクスポートすると行の高さに変化が生じる

### <a name="version-140600594-released-january-9-2018"></a>バージョン 14.0.600.594、リリース日:2018 年 1 月 9 日

セキュリティ更新プログラム

### <a name="version-140600490-released-november-1-2017"></a>バージョン 14.0.600.490、リリース日:2017 年 11 月 1 日

次の問題が修正されています。

- SKU アップグレードの問題を解決

### <a name="version-140600451-released-september-30-2017"></a>バージョン 14.0.600.451、リリース日:2017 年 9 月 30 日 

最初のリリース

## <a name="next-steps"></a>次の手順

[Reporting Services (SSRS) の新機能](what-s-new-in-sql-server-reporting-services-ssrs.md)   

その他の質問 [Reporting Services のフォーラムに質問してみてください](https://go.microsoft.com/fwlink/?LinkId=620231)
